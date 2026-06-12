---
title: "NVIDIA DRIVERS + MINT64 FIX-ish like thing!!"
date: 2010-08-31
forum: General Help
---

### Post by hellrazor236 on 2010-08-31
I came across this problem yesterday when I had just installed Mint. You install the latest nVidia drivers, the next time you boot everything works. You go into nVidia X Server Settings and it tells you there's no log and to run nvidia-xconfig as root, and then restart the X server. You run it, and reboot.

You then boot into Mint and everything is at 640x480, you look into hardware drivers and it says the drivers are active and in use, you go into nVidia X Server Settings and it tells you that they aren't. After doing some poking around you eventually find yourself at the point where Mint boots into a window saying that it can't start the drivers, and that it's running in low graphics mode and gives you a bunch of options.

This is where it starts.


Choose to boot into a console, login and run [FONT=Lucida Console]**startx**[/FONT]. Tadah! All of a sudden everything works perfectly!

Note that you will have to do this everytime you boot. There's probably a better way to workaround it (say making it run startx at startup), but that's how I did it.

---

### Post by an0dos on 2010-08-31
> **hellrazor236 said:**
> I came across this problem yesterday when I had just installed Mint. You install the latest nVidia drivers, the next time you boot everything works. You go into nVidia X Server Settings and it tells you there's no log and to run nvidia-xconfig as root, and then restart the X server. You run it, and reboot.

You then boot into Mint and everything is at 640x480, you look into hardware drivers and it says the drivers are active and in use, you go into nVidia X Server Settings and it tells you that they aren't. After doing some poking around you eventually find yourself at the point where Mint boots into a window saying that it can't start the drivers, and that it's running in low graphics mode and gives you a bunch of options.

This is where it starts.


Choose to boot into a console, login and run [FONT=Lucida Console]**startx**[/FONT]. Tadah! All of a sudden everything works perfectly!

Note that you will have to do this everytime you boot. There's probably a better way to workaround it (say making it run startx at startup), but that's how I did it.

I run 64bit Mint with the latest nvidia drivers without the above problems. What you may need to do is:

1) disable KMS
2) blacklist the nouveau driver
3) run nvidia-xconfig and then nvidia-settings

---

### Post by ellgor on 2010-09-01
Hi,

Here is a guide that I found that simply works:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

