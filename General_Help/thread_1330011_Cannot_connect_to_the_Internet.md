---
title: "Cannot connect to the Internet"
date: 2009-11-18
forum: General Help
---

### Post by chrislionheart on 2009-11-18
I just installed a clean copy of the latest Ubuntu 9.10. 
When I went to connect to the Internet using the DSL option, it didn't work.

I mean I created a new connection in the DSL option, and then when I tried connecting it it just doesn't get connected. 

I never had this problem when I was using the 9.04 version. 

Please help!

---

### Post by baskar007 on 2009-11-18
> **chrislionheart said:**
> I just installed a clean copy of the latest Ubuntu 9.10. 
When I went to connect to the Internet using the DSL option, it didn't work.

I mean I created a new connection in the DSL option, and then when I tried connecting it it just doesn't get connected. 

I never had this problem when I was using the 9.04 version. 

Please help!
hmmm, (i think) 9.10's network manager have some problem in DSL and wireless connections. I had same issue on 9.10, now i am using old version of network manager (that is 0.7 ). Now i can connect my wireless without any problems. 

try with network-manager-gnome 0.7

---

### Post by chrislionheart on 2009-11-18
bro, how do I get the old network manager??

do I go to the software center and download it???

---

### Post by lidex on 2009-11-18
How exactly are you connecting? Ethernet to dsl router/modem? Wireless broadband pcmcia card or usb dongle?

---

### Post by chrislionheart on 2009-11-18
dsl     .....          I got my internet through my cable provider......   I got that cablenet...... 

Where I put the username and password

---

### Post by chrislionheart on 2009-11-18
[SIZE=4]I got some solution of the major problem

but can someone please explain me in a bit more detail.....   please since I am new to Linux.

Check this link

[http://coding-corner.blogspot.com/2009/11/linux-dsl-problem-ubuntu-910.html](http://coding-corner.blogspot.com/2009/11/linux-dsl-problem-ubuntu-910.html)

Please help!!!
[/SIZE]

---

### Post by baskar007 on 2009-11-18
i have old networkmanager in my ubuntu9.4 backup.
here i uploaded for you.:popcorn:

Good-luck.

---

### Post by lidex on 2009-11-18
To change pppoeconf settings enter these commands in a terminal:
first
```
sudo -s
```
then
```
pppoeconf
```
It should then walk you through a series of questions. Answer each with yes.

---

