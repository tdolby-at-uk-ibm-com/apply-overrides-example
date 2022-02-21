# apply-overrides-example
Using ibmint apply overrides to persist changes to UDPs in a node-associated server.

Test URL at http://localhost:7800/test should return JSON of the form 
```
{"ExampleUDP":"exampleWithoutOverrides"}
```
and should show `exampleWithoutOverrides` when TestApplication.bar is deployed and `BAROverride` when TestApplication_With_BAROverride.bar is deployed.

Assuming a server called `default`, WebUI overrides at http://localhost:4414/servers/default/applications/TestApplication/messageflows/TestSchema.TestFlow should allow the value to be changed, but changes are non-persistent.

To persist the value, modify the `override-properties.txt` file to change the value, and (assuming Windows and a broker name of testBroker) run
```
ibmint apply overrides <path to>\apply-overrides-example-workspace\TestApplication\override-properties.txt --work-directory c:\ProgramData\IBM\MQSI\components\testBroker\servers\default
```
to modify the broker.xml file on disk.
