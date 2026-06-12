---
title: "Problems getting online with an Acer Aspire 5720"
date: 2010-06-09
forum: General Help
---

### Post by noreg on 2010-06-09
Hey!
For long I've had problems with a slow Windows Xp-laptop, so today I decided to install Ubuntu on it.

The problem now is that I cant get online. I have an Acer Aspire 5720. My network card is called Broadcom BCM4311 802.11b / g WLAN.

What do I do? I've googled around and found various forum posts where I'm told that I must write various things in Terminal, which have not yet worked.

I have also visited [this site]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure"), where this is the first step: Open System &#8594; Administration &#8594; Networking.
But the problem is that I can not find the "Networking" under "Administration".

Could anyone here help me? I have no experience with Linux what so ever, so please be gentle.

Ninja-edit: I tried reading through [this]("http://ubuntuforums.org/showthread.php?t=896713"), but I fell off at ***Make the .ko file***

---

### Post by noreg on 2010-06-09
bump!

---

### Post by makins on 2010-10-28
Ok, so this was along time ago and you've probably fixed it.. or given up. But what you should be able to do is firstly put your ubuntu disk in and then go into synaptic package manager (in system -> administration) and go into package (I think, this is from memory) then repositories and tick the ubuntu live cd. Finally go back to the package manager and reload and search for "bcm" and tick on "bcmw-kernel module" (I think) click apply and install. Then reboot and it should work fingers crossed :)

---

