---
title: "getting the GNU GRUB version 1.99-12ubuntu5 screen"
date: 2012-04-12
forum: General Help
---

### Post by toolm on 2012-04-12
I had edubuntu on my pc. I made a new partition for installing windows xp for dualbooting. I didn't back-up grub or do anything. I installed windows on the new partition and now windows can't load without the live USB. (I'm using a usb because I don't have a HD)

So, I put newest edubuntu verison on a usb and I run edubuntu Live. I installed grub and now when I reboot with my HDD  I get the grub screen.


I want to have edubuntu as my main OS, and XP as my second. Can you point me to a tutorial for this? I found many tutorials and none helped me. I'm a newbie. 

Is is better to just delete all partitions and install XP on a new one and then just install edubuntu via XP, or can I somehow fix all this problems?

---

### Post by PhantomTurtle on 2012-04-12
You are supposed to install Windows first. You can still update grub, see here for more instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by toolm on 2012-04-12
> **PhantomTurtle said:**
> You are supposed to install Windows first. You can still update grub, see here for more instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I tried following that but I couldn't run boot-repair from the live edubuntu. When I type boot-repair in terminal it doesn't start. And I can't find to start it manually (I was using sudo too)

---

### Post by PhantomTurtle on 2012-04-12
> **toolm said:**
> I tried following that but I couldn't run boot-repair from the live edubuntu. When I type boot-repair in terminal it doesn't start. And I can't find to start it manually (I was using sudo too)

You have to install it first. To install follow these instructions: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). And yes, it's ok to install this while on a live cd.

---

### Post by toolm on 2012-04-12
> **PhantomTurtle said:**
> You have to install it first. To install follow these instructions: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). And yes, it's ok to install this while on a live cd.
I did. I installed it and I couldn't run it via terminal

---

### Post by PhantomTurtle on 2012-04-12
just open it by searching it from the dash. or if you have gnome classic look under applications. Use the gui. Use the second link I provided.

---

