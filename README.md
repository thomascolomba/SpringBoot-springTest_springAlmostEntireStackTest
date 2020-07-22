Run unit tests with almost the entire spring stack running.<br/>
<br/>
compile & execute :<br/>
mvn spring-boot:run<br/>

during the execution, at the url : http://localhost:8080/greeting<br/>
The application shows : Hello, World<br/>
<br/>
--GreetingController.java<br/>
@RequestMapping("/greeting")<br/>
public @ResponseBody String greeting() {<br/>
&nbsp;&nbsp;return <b>service.greet();</b><br/>
--GreetingService.java<br/>
public String greet() {<br/>
&nbsp;&nbsp;return "Hello, World";<br/>
--WebMockTest.java<br/>
@Test<br/>
public void greetingShouldReturnMessageFromService() throws Exception {<br/>
&nbsp;&nbsp;this.mockMvc.perform(get("/greeting"))<br/>
&nbsp;&nbsp;&nbsp;&nbsp;.andDo(print())<br/>
&nbsp;&nbsp;&nbsp;&nbsp;.andExpect(status().isOk())<br/>
&nbsp;&nbsp;&nbsp;&nbsp;.andExpect(content().string(containsString("Hello, World")));<br/>
<br/>