---
title: "No network"
date: 2011-06-01
forum: General Help
---

### Post by Lloydb39 on 2011-06-01
Finally got xubuntu 10.10 booted from CD on my Dell Inspiron 1150, which has a Celeron processor. But, I can't get it to pick up my home wireless network. (Even Puppy, which I tried earlier, was able to do that.) The wireless connection menu doesn't show it available. I would like to install it over Windows XP and use only Linux, but I can't get it to do that, apparently, without an Internet connection. Does anyone have a suggestion?

---

### Post by seawolf167 on 2011-06-01
Check to see if any hardware drivers are available (plug it in via an Ethernet cable in the meantime while you check for possible drivers)

System -> Administration -> Hardware Drivers

the drivers won't be "saved" since you are booted in a LiveCD Environment, but on a "real" install, they would be installed normally

---

### Post by Lloydb39 on 2011-06-01
The Help file recommended that, too. The problem: My menu doesn't have "Administration" and "Wireless Drivers" under "System."

---

### Post by seawolf167 on 2011-06-01
In Xubuntu it might be called "Restricted Drivers Manager" instead of "Hardware Drivers"

---

### Post by linuxinstalledfromhdd on 2011-06-01
If you click on System, and then Adminstration, and you look at the bottom of that list of applications, you should find "Windows Wireless Devices" .

If you don't see it, then you don't have ndiswrapper to install Wireless Win Drivers for your wireless adapter/pci-card/whatever.  You need to have that program to install drivers that are not detected during installation.

Was your wireless turned on and installed physically in the computer when you did the installation?

---

### Post by Lloydb39 on 2011-06-01
Additional Drivers is found under System on my menu. I installed the Broadcom driver, rebooted, hooked up to Ethernet, now have wireless and I am installing Xubuntu, erasing Windows. The die is cast. I hope this works...

---

### Post by Lloydb39 on 2011-06-01
Uh oh. The grub pc package failed to install. That means it won't boot. Now what?

---

### Post by seawolf167 on 2011-06-02
> **Lloydb39 said:**
> Additional Drivers is found under System on my menu. I installed the Broadcom driver, rebooted, hooked up to Ethernet, now have wireless and I am installing Xubuntu, erasing Windows. The die is cast. I hope this works...

If you have the STA drivers available, use those instead of the older B43 drivers

> **Lloydb39 said:**
> Uh oh. The grub pc package failed to install. That means it won't boot. Now what?

Reinstalling GRUB is very easy, all you need is a Ubuntu LiveCD and [this link here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2"). Follow the step-by-step instructions and you'll be good to go in no time.

Let us know how it works for you and if you have any other issues.

---

