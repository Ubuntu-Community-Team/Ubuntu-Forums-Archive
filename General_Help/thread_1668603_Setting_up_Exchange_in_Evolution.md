---
title: "Setting up Exchange in Evolution"
date: 2011-01-16
forum: General Help
---

### Post by lucidvista on 2011-01-16
[FONT="Arial"][/FONT] [SIZE="5"][/SIZE] I am trying to set up my school e-mail in evolution. They use exchange 2007. When  I set it up on my iPod touch, it wouldn't work unless I put in my exchange domain. Where would I put that in evolution?

---

### Post by Dokuganryu07 on 2011-01-17
I have found a solution that works for me.  


The settings in evolution are as follows:

**DISCLAIMER** - Do not PING someone elses server without their permission.


you must first find the IP address of your e-mail server, try either:

A) asking an admin for the IP
B) using an IP finding service, such as FindMyIP.com (I do not know if this site is still active.)

C) use EtherApe, login to your email server, and hit the refresh button, etherape will give you a graphical representation, which server has sent you information, double click that server to view it's IP.


ok, so you have the IP address, great, what next?


Now, go into Evolution and click "add new account."  For server type select "IMAP" (even though the server is exchange, exchange 2007 does not work with evolution.)  Ok, now for the "server/server name" slot, type the IP address.  For username, type the name you use to log on, for example:

[email]johnny1234@example.com[/email]

Johnny1234 would be your username.


select "no encryption/ no security."  Now you should be able to receive emails from the server.  To send emails, set up the SMTP settings with the same IP address.

Please note, if your email address is in this format:

[email]example@exch.example.edu[/email],  With a clear ".exch" in front of it, there is an alternative method that may need to be used.


for server, type "Seed.exch.example.edu" replacing example with your school.  Do the same for the SMTP server, and you should be golden.


I struggled for 5 days to solve this problem, and I now have Outlook Web Access 2007 in Evolution.  Hope this helps, it worked for me and several friends.

---

