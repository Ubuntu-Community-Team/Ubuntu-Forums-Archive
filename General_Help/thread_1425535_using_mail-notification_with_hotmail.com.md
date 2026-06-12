---
title: "using mail-notification with hotmail.com"
date: 2010-03-09
forum: General Help
---

### Post by sathyashrayan on 2010-03-09
My system specification: 

I am using PC(stand alone) with the following system config.. 

AMD Sempron(tm) processor 
2500+ 
704 MB RAM 
ASUS mother board.. 
ubuntu version 9.10 

Problem: 

When I try to configure mail-notification with hotmail.com mail services, it shows the following error..

(unhandled windows live hotmail mailbox(cannot execute "GetLive": failed to execute child process "GetLive" (No such file or directory))  

Any help?

---

### Post by sathyashrayan on 2010-03-09
wlm does not supported in mail-notification?

---

### Post by sathyashrayan on 2010-03-13
any one?

---

### Post by kerry_s on 2010-03-13
are you using the right settings?

pop3.live.com 
port 995
ssl

---

### Post by sathyashrayan on 2010-03-13
> **kerry_s said:**
> are you using the right settings?

pop3.live.com 
port 995
ssl

How to set these pop3 settings in mail-notification?

---

### Post by kerry_s on 2010-03-13
> **sathyashrayan said:**
> How to set these pop3 settings in mail-notification?

your right it's broken. 
do you have gmail?

i have mine setup so gmail pops my other mail & i have gmail in mail-notification.

---

### Post by sathyashrayan on 2010-03-14
> **kerry_s said:**
> your right it's broken. 
do you have gmail?

i have mine setup so gmail pops my other mail & i have gmail in mail-notification.

Thanks a lot for trying to help me out. Yes i do have gmail and with mail-notification with gmail working great. But not with hotmail. I am having two emails and as of now both are important for me. I do use amsn to get email notification by being invisible. But I prefer to be offline with amsn and read mails through online rather than pop3 access. All i need is just a Indication that "you have got a mail" kind of thing. Thanks

---

### Post by kerry_s on 2010-03-14
> **sathyashrayan said:**
> Thanks a lot for trying to help me out. Yes i do have gmail and with mail-notification with gmail working great. But not with hotmail. I am having two emails and as of now both are important for me. I do use amsn to get email notification by being invisible. But I prefer to be offline with amsn and read mails through online rather than pop3 access. All i need is just a Indication that "you have got a mail" kind of thing. Thanks

yeah, that's what it does. have gmail grab your hotmail & mail-notification will tell you have mail, you read it in gmail like any other mail.
give it a try.

ps: you know it just accured to me, i haven't even gone to hotmail in over 2 years. lol

here's what my settings look like.

---

### Post by JMLM70 on 2010-11-29
have you tried "pop3.live.com:995"? if it does not work search google for hotmail port for your account type and write "pop.server.domain:port" and give it a try...

---

### Post by ElQanah on 2011-02-09
google up the new ppa of mail-notification with ssl enabled and setup your hotmail account using pop3 with:
server:  pop3.live.com
enable the tsl/ssl in the connection options
user:  your full email address at hotmail.

hope this help you or any other searching for this issue.

---

