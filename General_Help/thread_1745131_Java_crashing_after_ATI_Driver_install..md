---
title: "Java crashing after ATI Driver install."
date: 2011-04-30
forum: General Help
---

### Post by Cam! on 2011-04-30
I just installed 11.04, and DL'd the newest proprietary drivers from ATI. I have an ATI Radeon HD 6850 graphics card.

Anyway, I boot up minecraft, and it just crashes after I log in. Also, the OS seems to run slower.

---

### Post by greybirds on 2011-05-01
Java, Minecraft and ATI's proprietary driver don't play well together on Linux. Search here, Minecraft forums and [http://getsatisfaction.com/mojang](http://getsatisfaction.com/mojang) and you'll see lots of people with the same issue. Typically the game works fine with the open source drivers (although you get very low frame rates), and crashes while building/loading a world or a few seconds after.

Someone on Get Satisfaction claimed installing a 64-bit version of Linux (instead of the 32-bit version most people download) and using Sun's version of Java solves this problem. I tried it today and it's working really well. This might not be an option for you, though, since you're reinstalling Ubuntu and 64-bit has some issues with certain hardware and software. 

Since this was an experiment, I simplified things by using Linux Mint's DVD edition, which uses Sun's Java by default, and I used the version of ATI's proprietary driver that comes on the DVD. It should work just as well on Ubuntu, but you'll have to make certain you uninstall the Java version Ubuntu uses.

Hope this helps.

Edit: Here's the link to the Get Satisfaction thread: [http://getsatisfaction.com/mojang/topics/ubuntu_sun_java_ati_hd5850_fglrx_drivers_crash](http://getsatisfaction.com/mojang/topics/ubuntu_sun_java_ati_hd5850_fglrx_drivers_crash)

---

### Post by Cam! on 2011-05-01
I'm using 64bit Ubuntu, with Sun Java 6, and I'm using the FOSS drivers. There's no difference. I'm still getting 10-20FPS.

---

