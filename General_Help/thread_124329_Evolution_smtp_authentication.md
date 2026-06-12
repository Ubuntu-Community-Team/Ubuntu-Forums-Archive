---
title: "Evolution smtp authentication"
date: 2006-02-01
forum: General Help
---

### Post by mxa055 on 2006-02-01
hi,

for the past few days I am trying to setup evolution as my mail client (I had thunderbird until now). I am having problems when trying to send an e-mail from my domain's account. Although my setting are identical to thunderbirds for that account and I enter the exact same password again and again for smtp, I get an authentication failed error.

pop works fine with the same settings. Also gmail.com pop and smtp also work fine. I tried changing as many parameters as possible (security, login type etc) but nothing seems to work.

Any clue what options do I have?

```

sending : AUTH LOGIN

received: 334 VXN....hbWU6
sending : bS5hc2lt....QHFuZS5ncg==

received: 334 UG....vcmQ6
sending : aG9idW....mb3p1Cg==

received: 535 Incorrect authentication data

```

```

received: 250-SIZE 52428800
received: 250-PIPELINING
received: 250-AUTH PLAIN LOGIN
received: 250 HELP
sending : AUTH PLAIN AG0uYXNpbWFrb3Bv.........AaG9idWRvMWVmb3p1Cg==

received: 535 Incorrect authentication data

```

---

### Post by dcstar on 2006-02-01
[QUOTE=mxa055]hi,

for the past few days I am trying to setup evolution as my mail client (I had thunderbird until now). I am having problems when trying to send an e-mail from my domain's account. Although my setting are identical to thunderbirds for that account and I enter the exact same password again and again for smtp, I get an authentication failed error.
.......[/QUOTE]
Most SMTP servers of ISPs do not require authentication from their customers, try not using it.

---

### Post by mxa055 on 2006-02-01
Well this one does...tried it and the smtp request just hanged for a while and then gave a general error (cannot remember exact error message right now, but nothing of great help)

---

### Post by dcstar on 2006-02-01
[QUOTE=mxa055]Well this one does...tried it and the smtp request just hanged for a while and then gave a general error (cannot remember exact error message right now, but nothing of great help)[/QUOTE]
What happens when you (in a terminal):

telnet your-smtp-server 25

---

### Post by mxa055 on 2006-02-02
[QUOTE=dcstar]What happens when you (in a terminal):

telnet your-smtp-server 25[/QUOTE]

I get welcomed:

```

Trying 70.*.*.*...
Connected to *.*.
Escape character is '^]'.
220-kia.websitewelcome.com ESMTP Exim 4.52 #1 Thu, 02 Feb 2006 05:59:44 -0600
220-We do not authorize the use of this system to transport unsolicited,
220 and/or bulk e-mail.

```

---

### Post by mxa055 on 2006-02-02
I just tried to sent without authenticating again so as to write down the error message, so here it is:```
sending : EHLO [192.168.1.102]
received: 250-kia.websitewelcome.com Hello [192.168.1.102] [62.*.*.*]
received: 250-SIZE 52428800
received: 250-PIPELINING
received: 250-AUTH PLAIN LOGIN
received: 250-STARTTLS
This server supports STARTTLS
received: 250 HELP
sending : MAIL FROM:<*@*.*>
received: 250 OK
sending : RCPT TO:<*@gmail.com>
received: 550-ppp46-adsl-74.*.*.* ([192.168.1.102]) [62.*.*.*]:2423 is
sending : QUIT
received: 550-currently not permitted to relay through this server. Perhaps you have not

```

---

### Post by mxa055 on 2006-02-02
I wanted to ask... what are the disadvantages if I just don't use my websites smtp and I just use postfix with direct delivery setup locally on my PC? (so far it seems to work fine)

---

### Post by dcstar on 2006-02-02
[QUOTE=mxa055]I wanted to ask... what are the disadvantages if I just don't use my websites smtp and I just use postfix with direct delivery setup locally on my PC? (so far it seems to work fine)[/QUOTE]
Just the work is done in your PC's SMTP program, and not the other SMTP server.

There can also be an issue where the remote mail server (you are sending to) does a lookup of your IP address to verify that you are who you say you are (and not a Spammer), and that can cause mail rejection in some cases.

---

### Post by dcstar on 2006-02-02
[QUOTE=mxa055]I just tried to sent without authenticating again so as to write down the error message, so here it is:```
sending : EHLO [192.168.1.102]
received: 250-kia.websitewelcome.com Hello [192.168.1.102] [62.*.*.*]
received: 250-SIZE 52428800
received: 250-PIPELINING
received: 250-AUTH PLAIN LOGIN
received: 250-STARTTLS
This server supports STARTTLS
received: 250 HELP
sending : MAIL FROM:<*@*.*>
received: 250 OK
sending : RCPT TO:<*@gmail.com>
received: 550-ppp46-adsl-74.*.*.* ([192.168.1.102]) [62.*.*.*]:2423 is
sending : QUIT
received: 550-currently not permitted to relay through this server. Perhaps you have not

```[/QUOTE]
That's fine, no authentication and you can't send e-mails to addresses outside of that server, do you have a dialogue from when Evolution tries to authenticate?

---

### Post by mxa055 on 2006-02-02
[QUOTE=dcstar]Just the work is done in your PC's SMTP program, and not the other SMTP server.[/QUOTE]
even if I don't have a local smtp server the workload should be the same since I am sending emails to the smtp server anyway, right? So what difference does it make where work is done?

[QUOTE=dcstar]does a lookup of your IP address to verify that you are who you say you are[/QUOTE]
what do you mean verify I am who I say I am? If the email's domain matches the smtp server's domain?
Can't that be fixed by changing the MX records on my site (although I can only find one and no backup MX record)

[QUOTE=dcstar]That's fine, no authentication and you can't send e-mails to addresses outside of that server, do you have a dialogue from when Evolution tries to authenticate?[/QUOTE]

yes it's the two code quotes in my first post. The first one is using LOGIN and the second one using PLAIN as authentication type (if I am not mistaken)


PS: btw thanks for the time and effort you are putting on helping me.

---

### Post by dcstar on 2006-02-02
[QUOTE=mxa055]what do you mean verify I am who I say I am? If the email's domain matches the smtp server's domain?
Can't that be fixed by changing the MX records on my site (although I can only find one and no backup MX record)
......
[/QUOTE]
When your SMTP server sends out a message to another SMTP server, it tags it with a "Sent by [email]joe-blow@wherever.com[/email]" thing, and this usually default to your Ubuntu account and domain name!

You usually have to change the SMTP configuration file to put in a valid e-mail address, and sometimes the remote server tries to check if the IP your are sending from actually matches the domain of the e-mail address - if not then you can experience some sending rejections.

I had this issue when using the Ubuntu "Bug Buddy" system to report a bug, their e-mail system rejected the messages tagged with the (non) domain my system was set up with. A few changes to my Postfix configuration files and all is well now.

---

### Post by dcstar on 2006-02-02
[QUOTE=mxa055]
......
yes it's the two code quotes in my first post. The first one is using LOGIN and the second one using PLAIN as authentication type (if I am not mistaken)
......[/QUOTE]
Ahh yes, well that looks like a problem with the protocols used by Evolution and that particular SMTP server, could well be a bug in either (or both) of them.

What happens when you use the Evolution "Check for Supported Types" function?

---

### Post by mxa055 on 2006-02-02
[QUOTE=dcstar]Ahh yes, well that looks like a problem with the protocols used by Evolution and that particular SMTP server, could well be a bug in either (or both) of them.

What happens when you use the Evolution "Check for Supported Types" function?[/QUOTE]
 
Everything except PLAIN & LOGIN gets striked through. I tried both with the results shown on my first post. I just can't find what thunderbird does that evolution doesn't and sucessfully logins.

[QUOTE=dcstar]A few changes to my Postfix configuration files and all is well now.[/QUOTE]Wouldn't mind a few pointers for my configuration :-D

---

### Post by dcstar on 2006-02-04
[QUOTE=mxa055]Everything except PLAIN & LOGIN gets striked through. I tried both with the results shown on my first post. I just can't find what thunderbird does that evolution doesn't and successfully logins.
......[/QUOTE]
Possibly the Authentication protocols available in Evolution don't match the ones available in Thunderbird, and that particular SMTP server uses one of these missing ones. It wouldn't be the first time that this has occured, there are a lot of "legacy" protocols around that people assume have been superseded and don't bother to support any longer.

If possible, you may want to ask the people who administer the SMTP server what protocols they support (or try and find out in the Thunderbird logs somehow).

As for configuring your SMTP stuff, you have to look in the particular man pages for the system you are using, there are usually default settings in the configuration files which are easy to change.

---

### Post by mxa055 on 2006-02-04
[QUOTE=dcstar]Possibly the Authentication protocols available in Evolution don't match the ones available in Thunderbird, and that particular SMTP server uses one of these missing ones. It wouldn't be the first time that this has occured, there are a lot of "legacy" protocols around that people assume have been superseded and don't bother to support any longer.[/QUOTE]

So I guess this doesn't qualify as a bug, but more as a missing feature of evolution...:-? 
> As for configuring your SMTP stuff, you have to look in the particular man pages for the system you are using, there are usually default settings in the configuration files which are easy to change.

Does the domain that the server use have to be the same with the domain that my e-mail is part of? (say server1.example.com for [email]user@example.com[/email])

Again thanks for all the help.

---

### Post by dcstar on 2006-02-04
[QUOTE=mxa055]I just tried to sent without authenticating again so as to write down the error message, so here it is:```
sending : EHLO [192.168.1.102]
received: 250-kia.websitewelcome.com Hello [192.168.1.102] [62.*.*.*]
received: 250-SIZE 52428800
received: 250-PIPELINING
received: 250-AUTH PLAIN LOGIN
received: 250-STARTTLS
This server supports **STARTTLS**
......

```[/QUOTE]
Ah ha!, a little research shows that you might be able to log into this server using port 587

Try changing to the server to whatever.smtpserver.com:587, and set "Use Secure Connection" to "Always"

---

### Post by mxa055 on 2006-02-06
[QUOTE=dcstar]Ah ha!, a little research shows that you might be able to log into this server using port 587

Try changing to the server to whatever.smtpserver.com:587, and set "Use Secure Connection" to "Always"[/QUOTE]

Darn, and this looked very promising... nope it doesn't work :-k 
I get a connection refused. Worth the try though...

---

### Post by mxa055 on 2006-02-07
Finally I found it!!! :mrgreen: :mrgreen: :mrgreen: 

I changed the @ symbol with + in the username field and it worked. It seems that thunderbird and outlook both try different combinations for the @ sign but evolution doesn't.

> **So anyone that has problem with logging on to their smtp server using evolution try changing the @ sign with the + sign in the username field ,e.g. [email]user@example.com[/email] -> user+example.com.**

**dcstar thanks a lot for all your help!**

---

