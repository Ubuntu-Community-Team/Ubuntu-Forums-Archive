---
title: "Alt. email client"
date: 2009-12-01
forum: General Help
---

### Post by johnhdsi on 2009-12-01
Hi all, so I'm progressing through my 9.10 install quite well at this point. I have not had any major issues that could not be resolved so I am moving on to other things. Evolution is installed by default in Ubuntu however I would like to use another email client if possible to access my hotmail acct., any suggestions?

john

---

### Post by audiomick on 2009-12-01
try thunderbird from mozilla.
[http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)

It is available from the Ubuntu repositories via Synaptic Package Manager.
I am not sure if it is in the main, or in universe or multiverse. I have them all enabled.

I used Thunderbird for quite a while before I started using Evolution, and was more than happy with it. It also runs on Windows.

---

### Post by mo.reina on 2009-12-01
claws mail

---

### Post by camaron1 on 2009-12-01
> **johnhdsi said:**
> Hi all, so I'm progressing through my 9.10 install quite well at this point. I have not had any major issues that could not be resolved so I am moving on to other things. Evolution is installed by default in Ubuntu however I would like to use another email client if possible to access my hotmail acct., any suggestions?

john
I did not manage to set up Thunderbird with Hotmail (but I think it depends on the antiquity of your account give it a try). Otherwise Thunderbird is very good as you could expect from Mozilla people

---

### Post by rudy.b on 2009-12-01
Thunderbird is a popular choice for email client on Linux.  I haven't used it in a few years so I can't speak from recent experience though.  I use Opera Mail, which is included with Opera's web browser.

For setting up Hotmail in an email client, these are the settings that work for me:

**Incoming**
[LIST]
[*]Server: pop3.live.com
[*]Port: 995
[*]TLS: yes
[*]Username: <full hotmail email address>
[*]Password: <hotmail password>
[/LIST]

**Outgoing**
[LIST]
[*]Server: smtp.live.com
[*]Port: 25
[*]TLS: yes
[*]Username: <full hotmail email address>
[*]Password: <hotmail password>
[/LIST]

As far as I know, Hotmail still doesn't support IMAP.

---

### Post by dcstar on 2009-12-01
> **johnhdsi said:**
> Hi all, so I'm progressing through my 9.10 install quite well at this point. I have not had any major issues that could not be resolved so I am moving on to other things. Evolution is installed by default in Ubuntu however I would like to use another email client if possible to access my hotmail acct., any suggestions?


Do you just want a different client or you cannot get Evolution to access Hotmail?

---

### Post by johnhdsi on 2009-12-02
I wanted to use evolution if possible but I didn't know the correct settings for using hotmail through Evolution so I was looking for alt. choices that were a bit easier to set up. However now that Rudy.B posted up some config. choices I think I can get Evolution up and running or try one of the alt. choices (Thunderbird, Opera). thanks for the info you guys it's much appreciated, people like you make this forum what it is and I want to throw a HUGE thank you to everyone who takes the time out of their day to help noobs like me. :popcorn:


John

---

### Post by trixman on 2009-12-02
i use evolution email and so far its quite nice. it has nice features such as contacts & calender & loads the mail in super fast. a solid program.

---

### Post by fluffman86 on 2009-12-02
mutt

---

### Post by johnhdsi on 2009-12-02
> **dcstar said:**
> Do you just want a different client or you cannot get Evolution to access Hotmail?

Well I tried getting Evolution set up but it's not accessing my acct. I followed the POP set-up posted before but it just sits there waiting..not sure if I missed something. Anyone have any ideas? I didn't see any place to setup ports in evolution so maybe thats the problem?

---

### Post by dcstar on 2009-12-02
> **johnhdsi said:**
> Well I tried getting Evolution set up but it's not accessing my acct. I followed the POP set-up posted before but it just sits there waiting..not sure if I missed something. Anyone have any ideas? I didn't see any place to setup ports in evolution so maybe thats the problem?

smtp/pop.server:then_port

---

### Post by johnhdsi on 2009-12-02
I filled in the SMTP and also the POP server fields, what I did not see in the set up is where you could enter in the port number. Is there a screen I'm missing here? I'm having a similar issue with Empathy not connecting to a yahoo acct. for IM so I am wondering if the ports are blocked by default? 

This is gonna sound VERY dumb and I apologise in advance but is **smtp/pop.server:then_port** a terminal command I should run?

It's weird because even when I try to get the supported authentication from the server it just sits forever, almost like theres no internet connection but there is as I can conect and browse the web freely. The sae thing with Empathy, I set the account up and I get authentication failed msg. Not sure if the 2 are directly linked to each other??

---

### Post by anselm on 2009-12-03
> **rudy.b said:**
> Thunderbird is a popular choice for email client on Linux.  I haven't used it in a few years so I can't speak from recent experience though.  I use Opera Mail, which is included with Opera's web browser.

For setting up Hotmail in an email client, these are the settings that work for me:

**Incoming**
[LIST]
[*]Server: pop3.live.com
[*]Port: 995
[*]TLS: yes
[*]Username: <full hotmail email address>
[*]Password: <hotmail password>
[/LIST]

**Outgoing**
[LIST]
[*]Server: smtp.live.com
[*]Port: 25
[*]TLS: yes
[*]Username: <full hotmail email address>
[*]Password: <hotmail password>
[/LIST]

As far as I know, Hotmail still doesn't support IMAP.
[B]
Incoming[/B]

Incoming should be SSL encryption ,Also authentication should be password for receiving mail.

**Sending**
authentication should be plain

---

### Post by johnhdsi on 2009-12-03
Thank you very much I'll give it a go. I think Hotmail just hates evolution lol..


Edit: Set it up with the new info you gave me and it works like a freakin charm! Much thanks again to all!

---

