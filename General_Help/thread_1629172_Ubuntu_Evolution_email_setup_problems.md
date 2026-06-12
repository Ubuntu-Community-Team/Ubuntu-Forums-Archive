---
title: "Ubuntu Evolution email setup problems"
date: 2010-11-23
forum: General Help
---

### Post by Craigubunt on 2010-11-23
I just downloaded Ubuntu for my OS and am trying to setup my email.
First it asks me for my password. How do i find the password for my email on host pop3.live.com  ?  Would it be the same as the one for my email account at hotmail? i don't get it. I don't remember setting up one for email on Evolution.
Also when i try to send a message it says " Unable to connect to pop server pop3.live.com: No support for requested authentication mechanism.

Please any help would be appreciated.
Craig

---

### Post by viralmeme on 2010-11-23
> **Craigubunt said:**
> I just downloaded Ubuntu for my OS and am trying to setup my email. First it asks me for my password. How do i find the password for my email on host pop3.live.com  ?  Would it be the same as the one for my email account at hotmail?

**[SIZE=1]Configuring Evolution To Connect to Hotmail / Windows Live Mail[/SIZE]**

 [http://pricklytech.wordpress.com/2010/05/01/ubuntu-10-4-lucid-configuring-evolution-to-connect-to-hotmail-windows-live-mail/](http://pricklytech.wordpress.com/2010/05/01/ubuntu-10-4-lucid-configuring-evolution-to-connect-to-hotmail-windows-live-mail/)

---

### Post by pricetech on 2010-11-23
The password it is asking for is your hotmail password.

Try other authentication mechanisms for sending mail.  Evolution lets you check to see what is supported, but best I recall password is what you'll need to use.

---

### Post by Craigubunt on 2010-11-23
Now that the email works is there a way to import my email contacts from hotmail to Evolution?

---

### Post by NeverUsedItBefore on 2010-12-04
I guess I'm in the same boat as you.
I have some information but its only half the job:
In your hotmail All Contacts view, you can press Manage - Export.
This allows you to save as a .csv
The .csv can then be opened using the Open Office 'Excel spreadsheet' like thingie. You can tidy the contacts up.
In Evolution goto - Contacts using the button at the bottom. (This may not in fact be neccesary)
Then you can press File - Import, and select the .csv file you created.

HOWEVER!! - I found that it imported the contact NAMES but missed the EMAIL ADDRESSES which is a pretty key bit of information. It's most annoying. I suppose Evolution is expecting the .csv in a certain format but, the export from hotmail is not created in the format it expected.
I'm still investigating, I'll post if I find something out...

---

### Post by Dex73 on 2010-12-06
> **Craigubunt said:**
> Now that the email works is there a way to import my email contacts from hotmail to Evolution?

I have the quoted problem and I can't seem to send any mail. It always goes to 100% though. I read through the setup presented in the link earlier in this thread and got the setup complete e-mail from evolution in my inbox on evolution, but when I check my account with chrome, no such e-mail. Still unable to send people e-mail despite 100% complete briefly showing.

---

### Post by Dex73 on 2010-12-06
> **Dex73 said:**
> I have the quoted problem and I can't seem to send any mail.

Fixed sending mail by playing with options, but have yet to copy over contacts.

---

### Post by shoot2kill on 2010-12-06
RE: email addresses not being imported:

In your CSV file that you have exported from hotmail/live, what is the header name (top row) of the email address field?

---

### Post by Dex73 on 2010-12-06
> **shoot2kill said:**
> RE: email addresses not being imported:

In your CSV file that you have exported from hotmail/live, what is the header name (top row) of the email address field?

Haven't been able to export (don't know how) and can you tell me the path to that file would be by default. Thanks in advance.

P.S. check out this visual of your joke. Plus one I found online.

---

### Post by shoot2kill on 2010-12-06
Log into live.com

Messenger at the top of the page, then contacts

click manage near top, then export

follow the steps and you should be left with a csv file in your downloads folder.

i havnt got evolution to test it, so im basing this on the above posts.

first, try file->import in evolution. someone above said it didnt import the email addresses of the users but try that first and let me know.

---

Yes, i got the signature from that first image, lol..

---

### Post by shoot2kill on 2010-12-06
After looking into this a little, there are two obvious ways to do it.

1. Manually modifying the columns in the CSV file to match what evolution is expecting

2. (simpler way) Install thunderbird (dont worry, were going to remove it after) import your contacts to thunderbird (CSV)
--export contacts from thunderbird as LDIF, and import the LDIF into evolution.

then ```
rpm -e thunderbird
``` to remove thunderbird

hope this helps you out

---

### Post by Dex73 on 2010-12-06
Sorry, but I can't find any import option. I look in evolution and then tried right clicking on the .csv file that I successfully exported. However, I haven't been able to import to evolution. Am I messing something.

Also tried syc options in evolution but that takes me to a syc helper window for a palm pilot. We should almost be there. Just one more step to go.

---

### Post by Dex73 on 2010-12-06
O.K. got it imported into my contacts under the personal option in evolution, but when I try to send an e-mail clicking on to: takes my to a window that doesn't have any contacts listed no matter what configuration I put it on. Why is this happening? Doesn't make sense. Anyone else come across this or know a how to fix it?

---

### Post by sgosnell on 2010-12-06
In Evolution, in the top left corner, click on File.  That opens a menu which drops down.  About halfway down that menu is an option that says Import.  Click on that, and the import assistant opens.

---

### Post by Dex73 on 2010-12-06
> **sgosnell said:**
> In Evolution, in the top left corner, click on File.  That opens a menu which drops down.  About halfway down that menu is an option that says Import.  Click on that, and the import assistant opens.

Did that. It shows the list of names under contacts (no e-mail addresses), but you can't click the to: button when composing a message. This is the main feature I want. How do I get that to work?

---

### Post by sgosnell on 2010-12-07
Your import was borked, apparently.  If there were no email addresses, the .csv file was in the wrong format.  You need to get them in the correct order, and I'm not sure what that order is.  From Thunderbird, you should export as LDAP if you want to import into Evolution.  That works directly, but you have to manipulate the .csv to get the fields in the right order.

---

### Post by Dex73 on 2010-12-07
Image 01 and 02 are the way things are now. I've gotten the address on screen, but things aren't right. It looks like the first line in the excel in the evolution info in picture 02. Every thing was blank and then I typed in the e-mail under the e-mail address area. Things are diffinately related but where else might this info need to go?

---

### Post by sgosnell on 2010-12-07
Use LDAP, not .csv.  A .csv file is comma-delimited, meaning each field is separated by a comma, so a string of commas means a string of blank fields.  Thunderbird and Evolution can exchange data directly using LDAP, and there is an option for that in the import and export dialogs.

---

### Post by Dex73 on 2010-12-07
I'm trying to get these contacts from live.com account and it comes as .csv automatically. Can it be converted or made to come out the right way?

---

### Post by Dex73 on 2010-12-07
Managed to convert/retype everything. Problem solved. Thanx for all the help and suggestions.

---

