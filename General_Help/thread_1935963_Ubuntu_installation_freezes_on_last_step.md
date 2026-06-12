---
title: "Ubuntu installation freezes on last step"
date: 2012-03-05
forum: General Help
---

### Post by lubi on 2012-03-05
I have problems installing Ubuntu 11.10. I run installation from my USB and installing it alongside my Windows XP as dual boot. I don't use Wubi i install it direct on hard drive.
I get to the point where it asks me to restart in order to complete installation, and after clicking "restart" next screen shows up with command lines, 
Last line says:"*Asking all remaining processes to terminate..." and just freezes there.
Same thing happens when trying to install lubuntu.

*additional info
-i don't wanna use wubi
-MD5 of image is ok
-i tried installation with multiple option (with 3rd party software, without it, with manual created partitions, with automatic created...)
-checked file system before and after installing with multiple software (gparted, chkdsk, HDD regenerator...)
-same thing happens when trying to install lubuntu

---

### Post by sanderj on 2012-03-05
It could very well be that Ubuntu did install correctly. So have you tried booting from the harddisk (after removing the USB stick)?

---

### Post by lubi on 2012-03-05
after i click "restart", screen should appear asking me to remove my installation media (USB stick in my case) and  press enter. That screen does appear but it never gets to the point  asking me that, it just freezes and last line says:"*Asking all remaining processes to terminate..."  so my only choice to manually restart.  GRUB bootloader appears, and ubuntu seems to be loading and it gets to  the log in screen although i choose "log in automaticly" option in  installation process. and that log in screen wont accept my username or  password

same exact thing happens with lubuntu

---

### Post by sanderj on 2012-03-05
> **lubi said:**
> after i click "restart", screen should appear asking me to remove my installation media (USB stick in my case) and  press enter. That screen does appear but it never gets to the point  asking me that, it just freezes and last line says:"*Asking all remaining processes to terminate..."  so my only choice to manually restart.  GRUB bootloader appears, and ubuntu seems to be loading and it gets to  the log in screen although i choose "log in automaticly" option in  installation process. and that log in screen wont accept my username or  password

same exact thing happens with lubuntu

So I would say Ubuntu is actually installed. Right?

If so, it's a matter of the correct login. Does you user name appear in the screen? Have you written down your username/password? No mistake in capital / small letters?

---

### Post by lubi on 2012-03-05
Login is correct, i know my username and password im using same ones for years. And of course im aware of uppercase and lowercase letters.

I dont think its installed correctly because i was installing Ubuntu before and i know how does correct installation looks like. After whole installing process (selecting language, installing it along windows, checking 3rd party, connecting to wifi waiting for progress bar to complete...) little window comes up asking to restart. And when you press that button appears screen with command lines and last line says remove your installation media and press enter. That's how correct installation should look alike. In my case it never gets to the point asking me to remove media and press enter, it just hungs at last line :"Asking all remaining processes to terminate..." so i have to reboot my computer on power button otherwise it would stay like that forever. And after that manual reboot GRUB appears, i choose ubuntu and press enter, ubuntu is loading, login screen appears (although it shouldn't because in installation i checked "login automatic" box) and it won't accept my username and password.

---

### Post by lubi on 2012-03-05
i was just installing Lubuntu
problem is still same.
for last couple of days i was trying it over 20 times

---

### Post by lubi on 2012-03-06
bump :(

---

