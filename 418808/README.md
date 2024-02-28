# Stack Exchange Question 418808

## Question

Question can be found [here](https://salesforce.stackexchange.com/questions/418808/update-records-updated-in-flexcard-datatable)

I want to replace the Opportunity related list component on the Account record page with a Flexcard that has a datatable element listing all the related Opportunity records. 

I am aware that this use case is not best practise, but I use it to practise my Omnistudio skills. 

I also want to restrict this example to the Flexcard only and use the Flexcard's native functionality to update these record.

I am able to display all the related Opportunity records in the datatable using an Integration Procedure that receives the `AccountId` and retrieves all related Opportunities.

The issue I encounter is updating these records when they are changed on the datatable:

![](https://github.com/sfadriaan/Stack-Exchange-Questions/blob/main/418808/images/DatatableUpdate.gif)

The Salesforce Help files [here](https://help.salesforce.com/s/articleView?id=sf.os_flexcards_datatable_properties_29884.htm&type=5) lists a datatable event `update` that "Fires when table data changes."

I also found a very thorough Quip document going through all the datatable event use cases [here](https://exah.quip.com/ftaxAqKJknkj/FlexCards-data-table-events).

I created an event listener that triggers on the 'update' event and passes the information to an Integration Procedure that updates the relevant record:

![](https://github.com/sfadriaan/Stack-Exchange-Questions/blob/main/418808/images/UpdateEventSetup.png)

I assumed from the Quip document that the updated values will also be contained in the `{action.result.FIELD_NAME}` and as such I pass these merge fields to the IP.

From my GIF above, it seems like not to do the job, so my question is how to I pass the updated values to the IP to update the records OR is it even required to do such a thing with the 'update' event as from the Salesforce documentation as well as the Quip file it is not immediately obvious.

Should I rather use another event such as `rowclick` or `selectrow`?

I have created an MVP of the Flexcard which you can download [here](https://github.com/sfadriaan/Stack-Exchange-Questions/tree/main/418808).

Thanks for your time!
