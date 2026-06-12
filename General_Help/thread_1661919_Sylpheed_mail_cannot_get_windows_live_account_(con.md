---
title: "Sylpheed mail cannot get windows live account (connection failed)"
date: 2011-01-07
forum: General Help
---

### Post by searchfgold6789 on 2011-01-07
Hi, I finally managed to install lubuntu onto this old laptop, and I noticed it came with "Sylpheed mail client" integrated into lubuntu-desktop. I entered in my name, username, and password, and pop3.live.com for the incoming mail (pop3 server), and smtp.live.com for the outgoing mail (smtp server), but whenever I attempt to get mail for my windows live email account the connection fails.
How do I make it not-fail?
Thanks,
 - searchfgold

---

### Post by luigi_mb on 2011-01-07
> **searchfgold6789 said:**
> Hi, I finally managed to install lubuntu onto this old laptop, and I noticed it came with "Sylpheed mail client" integrated into lubuntu-desktop. I entered in my name, username, and password, and pop3.live.com for the incoming mail (pop3 server), and smtp.live.com for the outgoing mail (smtp server), but whenever I attempt to get mail for my windows live email account the connection fails.
How do I make it not-fail?
Thanks,
 - searchfgold

I don't know much about Windows Live, but check the following configuration items:

- ports (under Advanced)

- SSL

- Authentication (under Send)

/luigi

---

### Post by searchfgold6789 on 2011-01-08
I messed around with all of the options under SSL, Send and Receive, but no luck...

---

### Post by ellgor on 2011-01-08
Hi,

Are you sure that "pop3.live.com" is the correct address, mine reads "pop.gmail.com" for the in, in the box provided and obviously "smtp.gmail.com" for the out, hope this helps.

Regards, Ellgor.

---

### Post by searchfgold6789 on 2011-01-08
Thank you much for the help :D
I double-checked everything and specified the correct pop3 port. But now, all I get is a message saying "Session timed out". What does that mean? Have I really double-checked everything I needed to?
 - search

---

### Post by luigi_mb on 2011-01-08
"Messing around  with all of the options under SSL, Send and Receive" is not advisable: the number of possible combinations of the various settings is quite large.  It is unlikely you selected the right combination. Try to find the proper instructions from Live.com or wherever you have your email account. 

/luigi

---

### Post by searchfgold6789 on 2011-01-08
> 
Here’s the information to configure your account on your preferred e-mail client:
 
 - POP3 Server: pop3.live.com (port 995)  
 - SMTP Server: smtp.live.com (port 25)   
{Note: If port 25 has been blocked in your network or by your ISP, you can set SMTP port to 587 with TLS or SSL Encryption depending on the client in use}

Note: Please make sure to check the box that indicates that your outgoing server requires authentication (in most e-mail clients, this is not checked by default). 
 - Username: your full e-mail address 
 - Password: your Windows Live ID password
 
Also, our POP3 service requires that you use Secure Sockets Layer (SSL) with the POP and SMTP connection and use SMTP authentication.  This is to ensure that your e-mail address and password are not subject to tampering.

For instruction on how to add your e-mail account to Microsoft Outlook Express, click here.

For instruction on how to add your e-mail account to Microsoft Outlook, click here.

If you are having problems retrieving your mails from an email client even after following these steps, please write a post in Email Client and Device issues forum.
I matched those specifications. No luck, just the time-out message :(

---

### Post by searchfgold6789 on 2011-01-09
Bump :(

---

### Post by ellgor on 2011-01-09
Hi again,

Just checking, are you sure that "live.com" is the correct address for the mail server, it doesn't seem very specific, like MSlive or similar? also try not putting the 3 after the pop.

Regards, Ellgor.

---

### Post by searchfgold6789 on 2011-01-09
I'm sure. I have tried the alternatives you presented to me; they result in "connection failed".
I have tried to specify a domain name (the one for Windows Live is mail.live.com). It just keeps getting the same error, "session timed out."

---

### Post by luigi_mb on 2011-01-09
The devil is in the details... Please take snapshots of all the tabs (Basic, Receive, Send, Compose, SSL, Advanced) under Configuration > Account Preferences and post them here. 

/luigi

---

### Post by ellgor on 2011-01-10
Hi again,

The password you enter in the boxes for setting up, is it for the live site as opposed to your user password on unix?

Regards, Ellgor

---

