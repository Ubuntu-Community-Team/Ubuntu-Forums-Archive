---
title: "Help. . . Anybody"
date: 2006-03-05
forum: General Help
---

### Post by lakelovers on 2006-03-05
I've been trying for days to get my Breezy, desktop printer to work with my WinXP, laptop. I can get my desktop to share files with the WinXP, but can't find the key to get the printer working. I have a Canoni560 with a TurboPrint driver. I have the latest version of webmin which I've used to configure samba. And, I've tried setting up print sharing with CUPS. When I try to add a network printer on XP, it always says I don't have the correct printer name or the printer has been disconnected from the network. (I'm using a wireless connection) The printer works fine from my desktop, except when I set up cups to locate a network printer. Cups sets up a printer but I cannot print a test page. Cups gave the printer this name: tp0. That's the printer name I put into XP, and which it does not accept. I've also tried Canon_i560-TurboPrint. That doesn't work. I have "pinged" the laptop and it does respond. 

Does anyboy have an idea what's wrong or can anybody give me a check list to follow to track down the fault? Should I post the smb.conf file or the cups.conf file?

---

### Post by WelterPelter on 2006-03-05
Set up the printer as a "local" printer (NOT a network printer). 
Then, using Webmin, add it as a printer share to samba. 
I had to try a thousand different things before figuring this out. It *works*, at least on my network.

---

### Post by lakelovers on 2006-03-05
Thanks for the suggestion. I have the printer now set as local and it prints okay from my desktop but the XP laptop is stilll not accessing the printer. I must have something wrong in winmin. This is like the proverbial needle in the hay stack. I'll keep trying though I think I may have beat your thousand tries. I think I'm going in circles.

---

### Post by lakelovers on 2006-03-06
I am absolutely amazed and befuddled: I can't get my laptop XP machine to use my desktop Ubuntu printer no matter what I do.  As I've said, I have tried every method/instruction I can find on this forum and through internet searches. 

Here's my current cupsd.conf:

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin


<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.2.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 192.168.2.*
</Location>

<Location /printers>
 AuthType None
 Order Deny,Allow
 Deny From None
 Allow From All
</Location>

What needs correcting and added?
Would I be wise to uninstall Samba?
How can I tell whether it's my Ubuntu box or my XP box or both that is haywire?
Should I post the smb.conf file? (I have it back to the initial configuration, I believe)

---

