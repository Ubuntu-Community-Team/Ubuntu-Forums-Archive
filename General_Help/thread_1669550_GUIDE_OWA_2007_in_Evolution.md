---
title: "GUIDE: OWA 2007 in Evolution"
date: 2011-01-17
forum: General Help
---

### Post by Dokuganryu07 on 2011-01-17
Below I have attempted to create an easy to follow guide to setting up Evolution to send and receive emails from a "Outlook Web Access 5.5/2007" server, which is not supported by Evolution as an Exchange server.


The settings in evolution are as follows:

**DISCLAIMER** - Do not PING someone else's server without their permission.**


you must first find the IP address of your e-mail server, try either:

A) asking an admin for the IP
B) using an IP finding service, such as FindMyIP.com (I do not know if this site is still active.)
C) use EtherApe, login to your email server, and hit the refresh button,  etherape will give you a graphical representation, which server has  sent you information, double click that server to view it's IP.
**D) using the command "Ping <domain name> ie:  Ping example.edu


ok, so you have the IP address, great, what next?


Now, go into Evolution and click "add new account." 

 For server type  select "IMAP" (even though the server is exchange, exchange 2007 does  not work with evolution correctly.)  

Ok, now for the "server/server name" slot,  type the IP address that you found during step one.  it should look like this:  123.456.789.00, 11 numbers separated by periods in sets of 3 and one set of 2.

Next, For the username fuekd, type the name you use to log on, for  example:

[email]-johnny1234@example.com[/email]-

Johnny1234 would be your username.


select "no encryption/ no security."  Now you should be able to receive  emails from the server.  

--------------------------------------------------------------------------------
To send emails, set up the SMTP settings with  the same IP address.

Please note, if your email address is in this format:

***!******!******!******!***
[email]example@exch.example.edu[/email],  With a clear ".exch" in front of it, there is an alternative method that may need to be used, that method can be found below.
***!******!******!******!***


for server, type "Seed.exch.example.edu" replacing example with your  school.  Do the same for the SMTP server, and you should be golden.


---------------------------------------------------
Tested a total of 16 times as of 1/17/2011, worked every time with no or slight modification.  

Tested on Ubuntu 10.04, Ubuntu 10.10, Lubuntu.


Hope this helps.

---

