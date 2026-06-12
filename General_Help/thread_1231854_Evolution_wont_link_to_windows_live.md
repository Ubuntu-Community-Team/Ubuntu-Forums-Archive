---
title: "Evolution wont link to windows live"
date: 2009-08-05
forum: General Help
---

### Post by amenfex on 2009-08-05
This is my first time posting. 

I've only been using linux for a few days, and everything has worked just fine until now.

I tried to link evolution to my windowslive account and it wouldn't work. I also tried thunderbird but that didn't work either.

A link or any type of feed back would be appreciated.

---

### Post by amenfex on 2009-08-05
Anyone?

---

### Post by jrusso2 on 2009-08-05
These are the new settings

Our POP service requires that you use Secure Sockets Layer (SSL) with the POP and SMTP connection and use SMTP authentication. This is to ensure that your email address and password are not subject to tampering. The settings are the following:

    * POP: pop3.live.com (port 995)
    * SMTP: smtp.live.com (port 25)
          o Note: make sure you check the box that indicates that your outgoing server requires authentication (in most mail clients this is not checked by default). 
    * Username: your full email address
    * Password: your Windows Live ID password 

Works in Thunderbird. Probably in Evolution too but I hate it.

---

### Post by amenfex on 2009-08-06
Excellent! :D

The port settings helped. 

I got thunderbird to work but i don't know where to find the port settings on evolution.

In fact, the issues with evolution got worse. Did I enter the wrong settings?

This is my setup for my live and gmail account.

**[COLOR=SeaGreen]Live account[/COLOR]**
(Receiving Mail)
Server Type: Pop
Server: pop3.live.com
Security Connection: SSL encryption
Authentication: Password
[COLOR=Sienna][I][am i suppose to check the the "Disable support for all POP3 extentions"?. Right now, it's unchecked)

[/I][COLOR=Black](Sending mail)
Server type: SMTP
Server: smtp.live.com (Server requires authentication box is checked)
Security connection: SSL encryption
Authentication: Plain
[/COLOR][/COLOR]
[B][COLOR=Red]
GMAIL account[/COLOR][/B]
(Receiving Mail) 
Server Type: Pop
Server: pop.gmail.com
Security Connection: SSL encryption
Authentication: Password

(Sending mail)
Server type: SMPT
Server: smtp.gmail.com
Security Connection: SSL encryption 
Authentication: Plain


Those settings are right or....?

---

### Post by plucky on 2009-08-06
For evolution port settings,when you specify the server, use ```
pop3.live.com:995
``` for receiving email and ```
smtp.live.com:25
```for sending email.

Good luck

---

### Post by ShutterAce on 2009-08-06
I had to set server to 

```
smpt.live.com:587
```

and  security to TSL to get mine to work right.

FYI

---

### Post by YakPackin on 2011-01-12
ShutterIce is on the money! thanks very much

---

