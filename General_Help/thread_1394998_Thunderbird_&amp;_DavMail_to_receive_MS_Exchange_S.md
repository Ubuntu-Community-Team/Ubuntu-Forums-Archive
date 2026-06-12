---
title: "Thunderbird &amp; DavMail to receive MS Exchange Server Mail. Need Help"
date: 2010-01-31
forum: General Help
---

### Post by jcampen on 2010-01-31
Seems quite a lot out there are finding it simple enough getting Thunderbird/Davmail to work, yet I've been at it for days now and still no luck. I've finally given up altogether with Evolution last week, as it seems from weeks of reading and trying, there just isn't a solution for it to work with Exchange Server mail. Yes I tried brutus and its web sites are down so to get additions such as Brutus Keyring is impossible. (its all a long story for another day)Evolution is now uninstalled and in the bin.

So now Im into the 5th day trying with Davmail and Thunderbird to get emails from my company mail exchange server.

I am sure Im going to have better luck with Thunderbird from what Ive read so far, but it still eludes me how to set it up with Devmail and the information Ive found so far is not very clear. I am sure I am just missing the most simplest step somewhere along the line.

Can someone please post a detailed instruction on how to configure both Thunderbird and Devmail to work together and also how to test if Davmails is working?

This is what I have so far.
Thunderbird 2.0.0.23 with lightning and Devmail all installed and no issues there (Devmail working on Java 6)
Ubuntu 9.10

I can easily access my company emails via OWA with [https://thecompanyname.com](https://thecompanyname.com) from my home internet, so no issue there.
From the efforts of trying to get Evol to work where it came up with the error. "Evolution connector is not compatible with Exchange 5.5", I assume our company server is running an MS exchange server version 2003 or older.

Setup of Davmail:
OWA(Exchange)URL: [https://email.thecompanyname.com](https://email.thecompanyname.com) (is the "https://" required here or not?)
IMAP port: 1143
Local SMTP: 1025
Caldav HTTP:1080
Loal LDAP: 1389

Thuderbird Setup:
Account Type: IMAP
Server Name: email.thecompanyname.com
User Name: email.thecompanyname.com\loginname (Have also tried using just the loginname on its own, but still no luck)
Use secure connection: None (I tried all of them. Assume None should work)
Port: 143

Outgoing SMTP:
Server: email.thecompanyname.com
User: loginname
Port: 25
Security: None

SMTP in Thunderbird seems to be partly working because I can sent out emails, although when it send and then tries to copy it to the sent folder it never succeeds. I have checked and the emails do go thorough and get received at the other end. I have this same result whether Davmail is running or not. So I am assuming because I cant receive emails and the sent mail doesn't copy to the sent folder, that TB isn't talking to Davmail or Davmails isn't configured correctly

The Questions.
Is there anyway to check if Thunderbird is actually talking to Davmail?

I ran Davmail from terminal as root, but cant see anywhere on there an indication if it is talking to ether the server or TB.

Is there anyway to check if Davmail is talking to the server?

Can anyone spot any error in my TB and DM configurations?
I have tried adding /exchange and /owa at the end of [https://email.thecompanyname.com](https://email.thecompanyname.com) but neither works so assume its not needed?

Do the port settings need to be same in DM as TH eg. TB 1143 DM 1143 or is the setting in TB at 143 correct?

When I checked on my Outlook in WindowsXP, the domain setting for Microsoft Exchange Server is different to the OWA server name. On Microsoft Exchange Server it is with the three initials of the company name eg. say our company name is "The Company Name" the server address is TCN-MAIL.thecompanyname.com

I assume this is for outgoing mails, but not sure really.

I appreciate any help from those who have managed to get it all working.
Thanks. jc

OS: Ubuntu 9.10 Karmic Koala
Installed on: Bootable USB Stick, 16Gb SanDisk U3 Cruzer Micro

---

### Post by jcampen on 2010-03-01
Ok! I have it all sorted and have Thunderbird working with Davmail and thanks to the guy at Davmail.
Hear are the settings that have it working.

Setup of Davmail:
OWA(Exchange)URL: [https://email.thecompanyname.com/exchange/](https://email.thecompanyname.com/exchange/) (note that the URL must be appended with /exchange/ for Exchange server 2003 or older and with /owa/ for Exchange 2007)
IMAP port: 1143
Local SMTP: 1025
Caldav HTTP:1080
Loal LDAP: 1389

Thunderbird Setup:
Account Type: IMAP
Server Name: localhost ("localhost" is used if Davmail is running locally which in my case it is)
User Name: loginname (same as your mail login user name)
Use secure connection: None
Port: 1143 (note added the 1 in front to match the same in Davmail settings)

Outgoing SMTP:
Server: localhost ("localhost" is used if Davmail is running locally which in my case it is)
User: loginname (same as your mail login user name)
Port: 1025 (note added the 10 in front to match the same in Davmail settings)
Security: None

Hope this helps any others who had same trouble as me. Cheers

---

### Post by 2by4 on 2010-05-03
Unless anybody wants problems, please don't use TB3 with DavMail.

I've tried multiple times, wiped out settings, started from scratch however every single time I've had nothing more but headaches:

e.g. 

TB3 decided to get confused and wiped out Inbox on exchange. Fixed that by restoring on exchange server.

Wiped out .thunderbird directory, started from scratch. Again, few days later tried to delete 100 messages from one of the folders, TB3 got confused again and could not finish process successfully. I ended up with 700mb/89000 messages in Trash folder, TB3 tried deleting messages and failed, then was repeating over and over again multiplying all those messages in trash. Deleting 1 message at a time works, however emptying folder and then purging Trash is a nightmare to happen.

Don't get me wrong, idea is good however DavMail is based on java (problem in itself) and it's not in production ready state, not to mention TB3 is buggy in itself.

Waiting to see Evolution 2.30

---

### Post by anamtamrin on 2010-05-30
Hi,

Having installed DavMail I've succeeded accessing my Exchange Inbox both using Thunderbird and Evolution. But I can not send email from both. 

I've tried several combinations for the outgoing SMTP using different ports (25,1025) and security setting for SMTP but still I can not send an email.

The progress status shown "connected" but after a few seconds I got this:

"An error occurred sending mail: The mail server sent an incorrect greeting:  cannot connect to server."

and than this..

"Sending of message failed.
The message could not be sent because the connection to SMTP server mycompanyname.org was lost in the middle of the transaction. Try again or contact your network administrator."

any help?

---

