---
title: "Compiz with Ubuntu - Assistance Needed"
date: 2011-07-02
forum: General Help
---

### Post by Xirre on 2011-07-02
So, I have a MacBook Pro with 8GB RAM, Two 2.7GHz Intel Core i7 Processors, Bluetooth, Built in SD Card Reader, MATSHITA DVD-R UJ-898(Writes, Re-Writes, etc), Broadcom 57765-B0 Ethernet Card, FireWire Port Max 800MB/sec, Intel HD Graphics 3000(Type:GPU), and a few other features that I don't think would be neccesary to list. 

This is a MacBook Pro 2011 8GB RAM and 500GB Hard Drive Laptop running on Mac OS X 10.6.7 Snow Leopard. Though, I run Windows Vista(To code with certain programs) and I recently installed Ubuntu on this Mac as well. Windows and Mac OS X work fine. Only windows can't support high graphical games..

What my problem mainly is that I am running a virtual machine to use Windows and Ubuntu. My main problem is why can I not get Compiz to work? I have the Oracle VirtualBox v4.0.8 GUI.

I have installed TeamViewer so if anybody is willing to do some 1-on-1 help with me I'd very so much appreciate it. Thank you everybody! :KS:KS:KS:KS:KS:KS

---

### Post by wildmanne39 on 2011-07-02
> **Xirre said:**
> So, I have a MacBook Pro with 8GB RAM, Two 2.7GHz Intel Core i7 Processors, Bluetooth, Built in SD Card Reader, MATSHITA DVD-R UJ-898(Writes, Re-Writes, etc), Broadcom 57765-B0 Ethernet Card, FireWire Port Max 800MB/sec, Intel HD Graphics 3000(Type:GPU), and a few other features that I don't think would be neccesary to list. 

This is a MacBook Pro 2011 8GB RAM and 500GB Hard Drive Laptop running on Mac OS X 10.6.7 Snow Leopard. Though, I run Windows Vista(To code with certain programs) and I recently installed Ubuntu on this Mac as well. Windows and Mac OS X work fine. Only windows can't support high graphical games..

What my problem mainly is that I am running a virtual machine to use Windows and Ubuntu. My main problem is why can I not get Compiz to work? I have the Oracle VirtualBox v4.0.8 GUI.

I have installed TeamViewer so if anybody is willing to do some 1-on-1 help with me I'd very so much appreciate it. Thank you everybody! :KS:KS:KS:KS:KS:KS
Hi, what version of ubuntu are you running?
I have just got 11.04 with the cube and all to work, I first had to enable 3d support in virtualbox, install guest additions, and the extension pack, you do not need to install a driver for your video card, virtualboxes driver works great, here is a guide you can use to setup the cube and many effects, I wrote it for natty.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by Xirre on 2011-07-03
I have 11.04 . I just want to edit my Ubuntu it'll look cool. Then I'm going to start coding my game. But I just can't seem to get this to work..

Edit: I just saw that I "do not" have my 3D activated. I pressed "Host + N" to get my details. I think I changed the settings "after" I installed Ubuntu.. I don't know if it will work. If it does I'll edit this again to say whether or not this thread had been solved. Thanks for the help. That link provoked me to look further in my systems settings.

---

### Post by wildmanne39 on 2011-07-03
> **Xirre said:**
> I have 11.04 . I just want to edit my Ubuntu it'll look cool. Then I'm going to start coding my game. But I just can't seem to get this to work..

Edit: I just saw that I "do not" have my 3D activated. I pressed "Host + N" to get my details. I think I changed the settings "after" I installed Ubuntu.. I don't know if it will work. If it does I'll edit this again to say whether or not this thread had been solved. Thanks for the help. That link provoked me to look further in my systems settings.Hi, remember you do not need to install any extra video card drivers to make it work in virtualbox, just make sure you have guest additions installed and in display setting in virtualbox enable 3d support, then follow the guide and you will be fine, also since you are using virtualbox you should go ahead and take a snapshot before you change the settings in compiz.

---

### Post by Xirre on 2011-07-03
It works. I just needed to turn on my 3D Acceleration and install the VBox Guest Additions. Thanks!

---

### Post by wildmanne39 on 2011-07-03
> **Xirre said:**
> It works. I just needed to turn on my 3D Acceleration and install the VBox Guest Additions. Thanks!Hi, your welcome did you use the guide in the link I gave you if so please let me know what you think of it,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Xirre on 2011-07-03
I marked it. And the guide was great. It told me everything I needed to know. I'm going to install a second Ubuntu so I can run my own server. If you check General help or just search my posts you can see that I have another post that asks for some assistance on making an automated server. Do you think you can help out with that or is that too much? o.O

---

### Post by wildmanne39 on 2011-07-03
> **Xirre said:**
> I marked it. And the guide was great. It told me everything I needed to know. I'm going to install a second Ubuntu so I can run my own server. If you check General help or just search my posts you can see that I have another post that asks for some assistance on making an automated server. Do you think you can help out with that or is that too much? o.O
Hi, I have not set up a server, so I will leave that to the people who have done it before, I am glad the guide helped you.

---

