---
title: "Tracing question  (proxy)"
date: 2010-11-18
forum: General Help
---

### Post by Chondro_Biak on 2010-11-18
I have a setup and I am curious if it can be tracked or traced... 

Let me start off by saying, I am not doing anything wrong here and my IS department is well aware of this... I am only asking the question because they don't know how to trace/track it...

Here is my setup:
I am running Squid on my home desktop... Essentially turning my home PC into my own personal Proxy... 

At work (Windows XP) I have a program saved to the computer called plink.exe...
From the command prompt, I point to the location of my plink.exe file... Then type in [plink.exe -L port#:myIP:Port# -l username myip]
It then prompts for my password...

Then I have a portable copy of Firefox installed on a flash drive... I change my network settings to look at "Manual Proxy Configuration" and set my HTTP Proxy to "localhost" and my port to the open port... 
I also have the portable app settings to delete all history and cookies, etc... 


How can this be tracked by my IS department?

---

### Post by Chondro_Biak on 2010-11-18
So to clarify...

When I browse the web I am browsing through my homes IP... Which means all the websites that my company blocks are not blocked to me... 

How can they track/trace/see my internet usage?

---

### Post by Chondro_Biak on 2010-11-18
I have a setup and I am curious if it can be tracked or traced...

Let me start off by saying, I am not doing anything wrong here and my IS department is well aware of this... I am only asking the question because they don't know how to trace/track it...

Here is my setup:
I am running Squid on my home desktop... Essentially turning my home PC into my own personal Proxy...

At work (Windows XP) I have a program saved to the computer called plink.exe...
From the command prompt, I point to the location of my plink.exe file... Then type in [plink.exe -L port#:myIPort# -l username myip]
It then prompts for my password...

Then I have a portable copy of Firefox installed on a flash drive... I change my network settings to look at "Manual Proxy Configuration" and set my HTTP Proxy to "localhost" and my port to the open port...
I also have the portable app settings to delete all history and cookies, etc...


How can this be tracked by my IS department?

So to clarify...

When I browse the web I am browsing through my homes IP... Which means all the websites that my company blocks are not blocked to me...

How can they track/trace/see my internet usage?

---

### Post by uRock on 2010-11-18
Duplicate threads merged. Please do not create multiple threads on the same subject.

Thanx,
uRock

---

### Post by uRock on 2010-11-18
If they know about it, then why are you worried about them tracking your usage. The protocol you are using is easy to pick out from regular network traffic using Wireshark or TCPDump. There may be ways around this, but it is beyond the scope of these forums to explain the bypassing of security measures put in place by the owners of the systems you are using.

Thread Closed.

---

