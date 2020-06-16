What is SoapUI
------------------------
API Testing Tool
For manual and automation testing of SOAP and REST APIs
Its a Cross-platform tool built entirely over Java platform using Swing for GUI


Why to use SoapUI
------------------------------
1. To create quick and efficient API tests
2. To create API functional, performance and security tests
3. To create API Testing automation framework


Hierarchy follows in SoapUI
------------------------------

Project - Test Suite - Test Case - Test Step

Tips and Tricks

Use Search Forum for articles ex: Data driven testing


ASSERTIONS
--------------------------------

1. What are assertions
2. Why do we add assertions
3. Diff types of assertions in SoapUI


ASSERTIONS - validations on the response

expected vs actual

Contains 
XPath Match
XQuery Match
Compliance
JSON Path assertions

SLA - SERVICE LEVEL AGREEMENT


--------------------------------------------------------------------
What is API Monitoring:
Checking of your APIs at regular interval for 
Availability
Correctness
Performance

Step 1 : Open SoapUI - Right click on Project and Select - Monitor APIs

Step 2 : Connect to AlertSite (SignUp | SignIn)

Step 3 : Create Monitors

Step 4 : Add APIs to monitor and view in AlertSite


-----------------------------------------------------------------

JSON PATH FINDER - chrome-extension://bankcpekihijigplompggpdolehhnale/index.html


How to 
--------------------------
Generate Documentation - Right click on WSDL and select Generate documentation

Properties - Can be defined at Project ,TestSuite,TestCase and Test Step 

Properties can be accessed at following levels:
Project       -  ${#Project#PropertyName}
TestSuite   -  ${#TestSuite#PropertyName}
TestCase   -  ${#TestCase#PropertyName}
TestStep    -  ${TestStepName#PropertyName} // Take a special note,NO # AT TestStepName

System   -    ${#System#PropertyName}
Env        -     ${#Env#PropertyName}
Global    -     ${#Global#PropertyName} 

----------------------------------------

Notes:
groovy code to run test case
=====================
def tCase = testRunner.testCase.testSuite.testCases["TestCaseName"]
runner = tCase.run(new com.eviware.soapui.support.types.StringToObjectMap(), false);

groovy code to loop test cases in a test suite
==================================
def testCases = context.testCase.testSuite.getTestCaseList() 
testCases.each{
log.info(it.name)
}
	
Run a Project from groovy
---------------------------------
def projectName=testRunner.getTestCase().getTestSuite().getProject().getWorkspace().getProjectByName("REST Project 1")
projectName.run(null,true)
//projectName.run(new com.eviware.soapui.support.types.StringToObjectMap(), false)

def projectName=testRunner.getTestCase().getTestSuite().getProject().getWorkspace().getProjectByName("REST Project 1")
projectName.run(null,true)
//projectName.run(new com.eviware.soapui.support.types.StringToObjectMap(), false)

Jar Locations - External jars
C:\Program Files (x86)\SmartBear\SoapUI-5.5.0\bin\ext

Log Location - |Soap UI Logs
C:\Program Files (x86)\SmartBear\SoapUI-5.5.0\bin\ 


-----------------------------------------
groovy code to set and get setup and teardown scripts 
--------------------------------------------------------------------------
testRunner.testCase.testSuite.project.getTestSuiteByName('TestSuite1').getTestCaseByName('TestCase1').setSetupScript('log.info "setup"')
testRunner.testCase.testSuite.project.getTestSuiteByName('TestSuite1').getTestCaseByName('TestCase1').setTearDownScript('log.info "teardown"')

log.info ("  --  "+testRunner.testCase.getSetupScript());
log.info ("  --  "+testRunner.testCase.getTearDownScript());


-----------------------------------------------------------------------


For JSON response
-------------------------------

//get json response
import groovy.json.JsonSlurper
def responseMessage = messageExchange.response.responseContent
def json = new JsonSlurper().parseText(responseMessage)

//assert node values
log.info json.name
assert json.capital.toString() != null
assert json.name.toString() == "[Taiwan]"

testStepName = messageExchange.modelItem.testStep.name//to get the Test Step Name
log.info testStepName
xmlHold = messageExchange.responseContentAsXml.toString()  //to store the response as Xml string






	