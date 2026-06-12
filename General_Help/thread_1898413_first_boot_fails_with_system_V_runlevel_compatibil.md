---
title: "first boot fails with system V runlevel compatibility"
date: 2011-12-21
forum: General Help
---

### Post by anees.sw on 2011-12-21
Hi this is my first post here.
I am a new ubuntu user migrating from winblows. i created a live usb using an iso image for ubuntu 11.10. The installation went without a problem but I got a black screen when I booted up for the first time.  After searching online i put 'nomodeset' option while booting. The boot now hangs with the following message 

fsck from util-linux 2.19.1
/dev/sda5: clean 
 * stopping Failsafe boot delay                [OK]
 * ...
 * ...
 * ...
 *Stopping System V runlevel  compatibility     [OK]


Also if I power down I down hear the hard disk stop spinning ( I am assuming thats what i hear). I hear it if I manually power down in windows.




So I installed Ubuntu 9.04 which installed and booted fine( no wireless and graphics though)

I installed Ubuntu 11 again but had the same problem. I can boot into recovery but I have no idea how to fix this from there. 


p.s I am dual booting win7 and I have an ATI radeon 5470. I tried install x64 version from alternative downloads

---

### Post by emmomalick on 2011-12-21
Did you try the steps of changing parameters correctly? Give one more try to edit "nomodeset". Follow from here.

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by anees.sw on 2011-12-21
i tried radeon.modeset=0 option instead of nomodeset this time. Now i get the error.

*Stopping Save Kernel Message              [OK]

---

### Post by anees.sw on 2011-12-22
fixed it by installing again using default iso image instead of alternate

---

### Post by emmomalick on 2011-12-22
Fine. Have fun. :D

---

