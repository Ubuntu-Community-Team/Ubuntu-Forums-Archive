---
title: "Blank screen when I turn on"
date: 2010-07-29
forum: General Help
---

### Post by someone235 on 2010-07-29
Sometimes, when I turn on my PC, I get a blank screen with a little white cursor in the top right corner. Then I pres Alt+Ctrl+Del, and the PC is restarted, and works normal. What can be the reason?

---

### Post by robsoles on 2010-07-29
Sounds like a hardware issue.

Does it give you the same behavior if you have a boot CD in?

---

### Post by aeiah on 2010-07-29
do you go into grub first? if so next time you have to do this, when you finally get to your desktop open a terminal and issue dmesg. you'll see all the boot stuff and it should report your previous issues higher up.

if you dont get to grub, then it isnt a linux problem per se. do you have unusual storage devices attached? my netbook doesn't boot if i have a usb drive stuck in it, even if the drive doesn't contain bootable information. perhaps this has happened, or perhaps you have two hdds with the 'bootable' flag set (you can check this in gparted). if you've got two devices with the boot flag, for me my motherboard just locks up, but perhaps your motherboard tries to boot from the first one it sees, and sometimes its the wrong one.

---

