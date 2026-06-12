---
title: "Wireless internet problem"
date: 2009-08-07
forum: General Help
---

### Post by lynx93 on 2009-08-07
Hello!
 
I installed ubuntu several weeks ago but something with internet is not okay. So with wired internet whenever I want to connect I always have to install it in terminal, with password username and everything. Is that normal?
 
About wireless im sure that my laptop is able to use it because I used it before with an other operation system. If I click the network stuff icon there is just 1 option avaible: manual configuration, and I dont understand it because on my brothers laptop there is writed the wireless and wired internet list.
 
Can someone help me how to solve the problem?
 
Thanks!

---

### Post by lynx93 on 2009-08-09
Help please :D

---

### Post by SuaSwe on 2009-08-09
Hello!

First things first: can we have some more details about the operating system and computer, e.g. what version of Ubuntu, what computer make/model, do you know what wireless card you're using, etc.

Also, what do you mean by "So with wired internet whenever I want to connect I always have to install it in terminal, with password username and everything"? Walk us through what you do when you connect by ethernet. I assume you're using a router to connect and not, say, a USB modem.

And finally, please paste the output of (from terminal):

> ifconfig

---

### Post by lynx93 on 2009-08-09
hey Im useing ubuntu 8.04, hardy heron and i have a Toshiba NB100 netbook

---

### Post by Narada on 2009-08-09
> **lynx93 said:**
> hey Im useing ubuntu 8.04, hardy heron and i have a Toshiba NB100 netbook

You forgot this part:
[quote=SuaSwe]Also, what do you mean by "So with wired internet whenever I want to connect I always have to install it in terminal, with password username and everything"? Walk us through what you do when you connect by ethernet. I assume you're using a router to connect and not, say, a USB modem.

And finally, please paste the output of (from terminal):

Quote:
ifconfig [/quote]
:P

---

### Post by lynx93 on 2009-08-10
ohh yea, there I meant, when I plug in enthernet cabel, internet doesnt works, so every time I have to run in terminal > pppoeconf.
Is this the problem why I cant connect to wireless servers?
So, actually I can when I know the password, but like in bigger cafes or stuff like that wifi is free, and no password is needed, so I cant connect to it.

---

### Post by zkriesse on 2009-08-10
Most likely you just need to run the wireless setting(s) in the wireless menu....can you send me a screenshot?

---

### Post by abrari on 2009-08-10
pppoeconf is the cause of such bad things.

try what suggested on this thread:

[http://ubuntuforums.org/showthread.php?t=1153758&highlight=pppoeconf+broke+network](http://ubuntuforums.org/showthread.php?t=1153758&highlight=pppoeconf+broke+network)

---

### Post by lynx93 on 2009-08-10
Hm I dont really know what is wireless menu, when I tap on wireless settings in gives out network manager, so here it is:

---

### Post by zkriesse on 2009-08-10
can you tell me what kind of options it gives you?

---

### Post by P4man on 2009-08-10
what kind of router/modem/access point do you have ?
What kind of internet connection ? (im assuming adsl?)

If you cant use a router to establish the PPPoE connection with your provider, then use the network manager rather than pppoeconf (which disables network manager, and therefore the ability to easily configure wireless networks).

Right click on the network icon in the system tray > edit connections > DSL > configure your PPPoE there (again, if need be, its so much easier if your router does that for you).

---

