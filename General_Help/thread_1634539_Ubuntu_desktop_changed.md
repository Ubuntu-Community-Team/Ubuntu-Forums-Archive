---
title: "Ubuntu desktop changed"
date: 2010-11-30
forum: General Help
---

### Post by MKO32 on 2010-11-30
Hi all,
 
I installed Ubuntu server 10.10 just fine. I had a nice desktop and my network printers
are installed, so everything was oke. But when I booted up the next day something weard happened. My desktop had changed and when I click a menu item it takes a long time before it respond. When I start the internet browser is takes some time before it fires up. In the search box when I try to type something it takes a long time before the word is showing. When I go into a terminal screen I have the same problem by typing a command.
 
So I have no idea what has happened during powerdown or booting up but I'm not realy amused about this. Is there a way I can roll back to the default without loosing my network printer configurations? When I put the indtall cd of Ubuntu in the system there is a option to repair a corrupt system, but I can't use it because of lacking knowlegde of wat to do next.
 
I hope someone can help me with this problem.
 
Thanks

---

### Post by TeoBigusGeekus on 2010-11-30
Type 
```
top
```
in terminal when experiencing this lagging to see what's eating up cpu/ram.

---

### Post by sikander3786 on 2010-11-30
Welcome to the forums :-)

> I installed Ubuntu server 10.10 just fine. 

I hope it is not Ubuntu Server but Ubuntu Desktop instead as you are trying to run internet browser etc i.e, some gui stuff.

If you don't see anything eating up your RAM or CPU, we need some more information regarding your hardware specs, graphics card, graphics drivers version etc.

Also, is compiz enabled? If yes did you try switching to metacity for the time being and see if the problem persists?

```
metactiy --replace
```

---

### Post by MKO32 on 2010-11-30
> **sikander3786 said:**
> Welcome to the forums :-)
 
 
 
I hope it is not Ubuntu Server but Ubuntu Desktop instead as you are trying to run internet browser etc i.e, some gui stuff.
 
If you don't see anything eating up your RAM or CPU, we need some more information regarding your hardware specs, graphics card, graphics drivers version etc.
 
Also, is compiz enabled? If yes did you try switching to metacity for the time being and see if the problem persists?
 
```
metactiy --replace
```
 
It is Ubuntu Server and I use the Gnome desktop. I can't see wy I shouldn't. 
 
I did work with this setting for a couple of days and it is certainly not related to the hardware as it is all new stuff. What strikes me is why it behaves from one day in the other the way it does now. How can I find out what is eating up my memory?
 
What do you mean by "compiz" or "metactiy"? I just installed the server pretty much standard and 'did not do any modifications to the system.

---

### Post by MKO32 on 2010-11-30
> **TeoBigusGeekus said:**
> Type 
```
top
```
in terminal when experiencing this lagging to see what's eating up cpu/ram.
 
Thank you for your reply. I will check it out.

---

### Post by Dans564 on 2010-11-30
If your not using your computer as a server why are you using the server edition?????????

---

### Post by MKO32 on 2010-12-01
> **Dans564 said:**
> If your not using your computer as a server why are you using the server edition?????????
 
I'm going to use it as a server but because I find it easer to install stuff for the network printers etc. 
 
Second it is a way to get to know Ubuntu better and on top of that once everything is setup there won't be any need for the desktop enviroment . But in the meantime all of this is not explaining this miss-behaviour of Ubuntu. If there are no alterations done by me I expect it to behave the same way as it did the day before. So with all the questions asked why I use gnome my problem is not solved. 
 
So I'm waiting for someone who knows what I should do to fix this and help me with that, that it's all.
 
Thank you

---

