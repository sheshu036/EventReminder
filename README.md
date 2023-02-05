# EventReminder 
## Event reminder using Power Automation

## Project Summary
I am sending event reminders via email using Power Automation. I have stored my event details in an Excel document and saved them on one drive. 
It will send event reminders one day before the event and on the event day as well.

## Changes done in Power Automation
To create a Power Automation flow, you should have an Outlook account. Once you login to Outlook, select Power Automate from the Outlook menu. 

### Step 1
Click on the "+ Create" option. It will show multiple options; select "Scheduled cloud flow."
![Step 1](https://github.com/sheshu036/EventReminder/blob/main/Steps/Step%201.jpg)

### Step 2
Mention your flow name and click on Create.

### Step 3
Add “Recurrence Trigger” and set Interval, Frequency values.

### Step 4
I have created excel and saved it in one drive.

### Step 5 
Select Excel document from one drive location and select the table. 

### Step 6
Add “Apply to each” control and select excel values as an input for this.

### Step 7
To select record based on event date then we have to add “Condition” control. Where we have to add two OR conditions.

##### One day before the event: 
`equals(if(empty(item()?['EventDate']),null,addDays('1899-12-30',int(item()?['EventDate']),'yyyy-MM-dd')), formatDateTime(utcNow(), 'yyyy-MM-dd'))` 

#### Reminder on event day:  
`equals(if(empty(item()?['EventDate']),null,addDays('1899-12-30',int(item()?['EventDate']),'yyyy-MM-dd')), formatDateTime(addDays(utcNow(),1,'yyyy-MM-dd'),'yyyy-MM-dd'))` 

### Step 8
If Step7 condition matches then send email otherwise no action required
