---
title: "i accidently removed my admin rights now there are no admins on my computer how do i"
date: 2009-12-06
forum: General Help
---

### Post by garry123 on 2009-12-06
i accidently removed all the admin rights from my computer and i dont know how to get them back i have a dell mini so i cant re boot the system using a cd. please help.

---

### Post by fluffman86 on 2009-12-06
boot into Recovery Mode by pressing ESC or holding shift while the computer is booting, then select recovery mode with the arrow keys and press enter.

choose to boot into a root shell.

When you are at a command prompt, type:

adduser garry admin && reboot now

where garry is the user you use to log into the system normally.

---

### Post by garry123 on 2009-12-06
im pushing esc and shift but both buttons arent doing anything. 
 
the screen just says mbr 2sa: and a little flashing light.

---

### Post by TransitMan on 2009-12-07
Dell Mini? 
Try F2 or F10 and see if that doesn't get you something.

---

### Post by aysiu on 2009-12-07
Entering recovery mode on a Dell Mini is tricky.

Instructions here, though:
[https://help.ubuntu.com/community/DellMini9#Booting%20into%20Recovery%20mode](https://help.ubuntu.com/community/DellMini9#Booting%20into%20Recovery%20mode)

---

### Post by teward on 2009-12-07
If recovery mode fails, you might be stuck having to reinstall from a USB stick, or use a USB stick to load a LiveCD image onto it.

On a different computer, burn the image for an Ubuntu disk to a USB drive, then boot onto the USB stick from the laptop, use the Live image to mess with your install.  At the worst, you'll need to reinstall.  But you can use the Live image to get access to your data (hopefully).

---

### Post by aysiu on 2009-12-07
You do **not** need to reinstall.

If you absolutely cannot boot into recovery mode (even after reading that link I just posted), you can use the live USB to mount your drive and edit the /etc/group file to add yourself back to the *admin* group.

First, though, try the link I posted.

---

