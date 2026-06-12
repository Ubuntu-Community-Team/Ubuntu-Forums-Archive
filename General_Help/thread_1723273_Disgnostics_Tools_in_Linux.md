---
title: "Disgnostics Tools in Linux"
date: 2011-04-06
forum: General Help
---

### Post by inukai on 2011-04-06
Hello, this might seem a little vague but my lappy has been acting choppy, but when I look at my CPU/RAM usage it's barely at 50% (I mean I have 4 cores and during the periods of choppyness one or two of them are at 50% and the others are at 0% and then the cores swap usage) What I'm asking is for some tools, built-into 10.10 or otherwise that might help me figure out what's happening. 

I'm also having some problems with my wireless network connection. Using the default wireless manager or even using WCID my connection is shaky at best. If I am downloading a torrent my manager will say I'm connected to my network, but my internet connection won't work. This is localized to my computer, and only when I'm on Linux. So if there's any type of network diagnostic tool or a way to see what's happening with my network, where the packets are sent, where the packets get dropped and with what error code or something like that, can I get some names?

---

### Post by techunit on 2011-04-06
I use some simple commands to see what to use but here are a few.

```
top
```
This little command will tell you even with out a GUI what apps are slowing down your computer
```
sensors
```
This one will tell you core temps really useful if your using a lot of power.
```
man apt-get
```
I could spend an hour explaining to you how apt functions and how to use it to diagnose problems but you can run this command and it will open a manual.

There are really tons of commands that will provide information about your system.

As for your problem you are quite vague in your problem description but you might need to install some restricted drivers or remove some restricted drives lighten the load on your system or simply just get more ram.

---

### Post by inukai on 2011-04-06
Thanks for the quick reply. Those commands will be very useful. I'm sorry I can't be more specific but that's what I know. If it happens again I will add details.

---

### Post by techunit on 2011-04-06
Good Luck It can I guess tell you when and why your computer is getting hot and how to debug apt.

---

