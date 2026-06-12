---
title: "How can i connect my xbox 360 via ethernet to get on xbox live in ubuntu?"
date: 2009-08-08
forum: General Help
---

### Post by Austin 'D' King Wehmeyer on 2009-08-08
Hello I am very new to Ubuntu, so please keep replys' noobish! Thanks, to give you an idea of my understanding of Ubuntu, the most advance thing I have dont is installed Wine without package manager, I used terminal ect. 

[COLOR=Blue]OK so now to my question! I use to connect my xbox 360 to my laptop via ethernet and get on xbox live with internet connetion sharing or bridging connections! Now i am wonder how I can do that in Ubuntu? I have the 9.0.4 version of Ubuntu I think, and i have built in wifi that is working and one ethernet port. I heard that it is possible so please help. Thanks you to every one for reading this![/COLOR] :)

---

### Post by Tclarkie on 2009-08-08
create a wired net work

in prefferences one of the network utils allows u to create a wired network

---

### Post by 3rdalbum on 2009-08-08
Network Manager can do connection sharing. Right-click the NM applet and click Edit Connections. Click on your wireless connection and click Edit. Under "IPv4 Settings", choose "Shared to other computers" in the Method popup menu.

I have not had occasion to try this, but I have heard that this works.

---

### Post by Austin 'D' King Wehmeyer on 2009-08-08
Thanks you so much!!! Im glad I got Ubuntu! Thanks both of you guys! :D:D:D

---

### Post by hooless on 2009-08-16
> **3rdalbum said:**
> Network Manager can do connection sharing. Right-click the NM applet and click Edit Connections. Click on your wireless connection and click Edit. Under "IPv4 Settings", choose "Shared to other computers" in the Method popup menu.

I have not had occasion to try this, but I have heard that this works.

hmmm, tried it on my computer and it didn't work at all...

---

### Post by joek1997 on 2009-08-16
I tried this and it did not work for me either.   Also, wouldn't it make more sense to share the wired connection instead of the wireless connection?  I tried that, and it did not seem to work either.  Can someone provide a user-friendly, noob-friendly step-by-step guide for that does *not* involve the use of Ubuntu's "console" to get Xbox 360/Live through a wired connection to a PC on a wireless network using Ubuntu 9.04.

---

### Post by hooless on 2009-08-16
> **joek1997 said:**
> I tried this and it did not work for me either.   Also, wouldn't it make more sense to share the wired connection instead of the wireless connection?  I tried that, and it did not seem to work either.  Can someone provide a user-friendly, noob-friendly step-by-step guide for that does *not* involve the use of Ubuntu's "console" to get Xbox 360/Live through a wired connection to a PC on a wireless network using Ubuntu 9.04.

indeed. I also tried sharing the wired connection, but the XBOX give me a "can't get an IP address" error, or something similar to that. I have also tried the brctl command- unless I failed to correctly bridge using that, it won't work for me. sadness....:cry:

---

### Post by donkeypuncharex on 2009-08-30
I have a homemade desktop pc with a wireless internet card installed. In NC in preferences leave your wireless connection alone. But for your wired connection set your IPv4 to shared to other computer. For your settings for xbox, set your IP address to auto, but you have to manual set you DNS address. 

I screwed around for about 30 minutes and figured this out. It should work if you have your dns set correctly and your wired connection correct.

---

### Post by hooless on 2009-08-31
> **donkeypuncharex said:**
> I have a homemade desktop pc with a wireless internet card installed. In NC in preferences leave your wireless connection alone. But for your wired connection set your IPv4 to shared to other computer. For your settings for xbox, set your IP address to auto, but you have to manual set you DNS address. 

I screwed around for about 30 minutes and figured this out. It should work if you have your dns set correctly and your wired connection correct.

um. that didn't work I don't think.... anything else?

---

### Post by chestnuts_2 on 2009-09-08
Wow i am a complete nub to this and i got lucky!!! woot i wanted to play halo 3 badd lol i right clicked on the thing at the top with the bars then edit connections and i shared both the wireless connection and the WIRED connection. i did all that after the xbox was plugged in then i tested the connection and it worked yay me. hahaha

---

### Post by apoth on 2009-09-09
I need to look at this tonight for my 360 too, otherwise I think I'm going to have to pay out for an ethernet over powerline bit of kit.

---

### Post by apoth on 2009-09-09
Weird.

This didn't work via system/preferences/network connnections.

But it did, doing the exact same thing via the network manager applet!

Just choose the shared IPv4 option on the wired interface, the wireless configured as it would be, and it worked. XBox complains that it's behind NAT but I'm sure that either doesn't matter or is resolvable.

---

### Post by s12en7s120 on 2009-09-13
This is my problem.... I have 2 NICs in my computer. I have been able to do this with windows but I am trying to stray away from the Windows. I have eth0 active and created a new connection called Wired Connection 1. I have tried setting up the IP settings and its not working. I have a DHCP internet connection and no router. I want to be able to connect online from my XBox 360 from my computer. how do I do this. and yes I already tried what was told earlier and didn't work. I have been scooping out for about 5-6 hours non stop reconfiguring the settings but I just can't find the right settings.

---

