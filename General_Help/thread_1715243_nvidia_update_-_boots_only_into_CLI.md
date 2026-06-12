---
title: "nvidia update - boots only into CLI"
date: 2011-03-26
forum: General Help
---

### Post by uveryames on 2011-03-26
im very new to ubuntu.  using 10.10 right now.  i updated my nvidia driver and now i can not boot into GUI.  i've tried the "sudo /etc/init.d/gdm restart" , startx , "dpkg-reconfigure xserver-xorg"...with no luck.  

im receiving this error:  

ERROR: API Mismatch: the nvidia kernal module has version 260.19.06, but this nvidia driver has version 260.19.29.

Fatal Server Error: no screen found

(EE) Screen(s) found, but none have usable configuration.  

im using nvidia GeForce GT 130m for my laptop.  

im very new and do not know how to really work my way around linux yet.  so if you help plz be very specific.  i appreciate the help and thank you all in advance.

---

### Post by uveryames on 2011-03-26
bump.  

ive tried:

sudo service gdm stop, start
sudo /etc/init.d/gdm restart
sudo dpkg -reconfigure xserver-xorg
sudo dpkg -reconfigure -phigh xserver-xorg

all fail. im still stuck in terminal. 

i also tried removing 'quiet splash' in the grub menu and replacing it with nomodeset then ctrl x to restart. that failed as well. 

im lost. i ran lspci | grep vga: 

00:02:0 VGA compatible controller: intel corp mobile 4 series chipset integrated graphics controller rev 07

01:00:0 VGA compatible controller: nvidia corp G96 [geforce GT 130M] (rev a1)

thanks for any more help

---

### Post by gsimpson on 2011-05-28
I booted into safe mode when failed to do full boot. (Mint 11) I was able to disable the nvidia driver that was causing the trouble and now boots ok

---

### Post by wildmanne39 on 2011-05-28
> **gsimpson said:**
> I booted into safe mode when failed to do full boot. (Mint 11) I was able to disable the nvidia driver that was causing the trouble and now boots ok
Hi, thats good, sorry I did not see your post sooner.

---

