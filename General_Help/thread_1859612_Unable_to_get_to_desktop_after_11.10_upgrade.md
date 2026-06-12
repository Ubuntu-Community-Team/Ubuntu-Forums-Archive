---
title: "Unable to get to desktop after 11.10 upgrade"
date: 2011-10-14
forum: General Help
---

### Post by tubaguy50035 on 2011-10-14
After I upgraded to 11.10, my virtual machine was no longer booting.  It would just sit at the purple Ubuntu screen.  I've seen a couple of different posts including this [one]("http://ubuntuforums.org/showthread.php?t=1859203") about Ubuntu not booting after upgrading.  I've followed all of the steps in the given post, and I have Ubuntu booting.  I get to a command line prompt asking me to log in.  My question is, how do I get my desktop back?

---

### Post by tubaguy50035 on 2011-10-14
Unlike the people in the two other posts I've found, I cannot get past the Ubuntu purple screen by selecting an older version of the kernel.  Any ideas?

---

### Post by garvinrick4 on 2011-10-14
> **tubaguy50035 said:**
> After I upgraded to 11.10, my virtual machine was no longer booting.  It would just sit at the purple Ubuntu screen.  I've seen a couple of different posts including this [one]("http://ubuntuforums.org/showthread.php?t=1859203") about Ubuntu not booting after upgrading.  I've followed all of the steps in the given post, and I have Ubuntu booting.  I get to a command line prompt asking me to log in.  My question is, how do I get my desktop back?
If you get to a command line prompt log in give password and:
```
sudo /etc/init.d/lightdm restart
```See if that gets you to a log in screen.
If not:
log in
```
sudo dpkg-reconfigure lightdm
```choose lightdm instead of gdm if a selection.

---

### Post by tubaguy50035 on 2011-10-14
I issued the first command and it started doing something and then started stopping a bunch of processes, and then got stuck.  Upon running the second command, I'm told "dkpg-reconfigure: command not found"

---

### Post by tubaguy50035 on 2011-10-14
I think you meant dpkg  :)

I set it to lightdm and I got two warnings saying:
environment variable DPKG_MAINTSCRIPT_NAME missing
environment variable DPKG_MAINTSCRIPT_PACKAGE missing


Rebooting now...


And it boots to a blank screen with a blinking cursor in the upper left hand corner of the screen.

---

### Post by fritz269 on 2011-10-14
Heres a crude way I fixed this issue, It works with 10.10, 11.04, and 11.10. Make a Ubuntu install disk and boot to up to where it ask you if you want to install or demo. click on the power button and choose to shut down. Remove the disk and reboot. It works for me.

---

### Post by tubaguy50035 on 2011-10-14
> **fritz269 said:**
> Heres a crude way I fixed this issue, It works with 10.10, 11.04, and 11.10. Make a Ubuntu install disk and boot to up to where it ask you if you want to install or demo. click on the power button and choose to shut down. Remove the disk and reboot. It works for me.

That did nothing.

---

### Post by garvinrick4 on 2011-10-14
Boot into your Live Cd (install cd using Try Ubuntu) get internet working.
```
sudo fdisk -l
``` (lower case L)
pick out your linux install. 
I will use sda5 for this use your own and copy and paste these one at a time.
```
sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
apt-get purge gdm
``````
apt-get install -reinstall lightdm
``````
apt-get update; apt-get upgrade
``````
dpkg --configure -a
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot
```Seems like a lot but all we are doing is getting into the / of your install and getting rid of
gdm, reinstall lightdm and updating and upgrading system and checking for broken packages.
You seem to have something amiss and cannot boot properly this might do it for you.

---

### Post by tubaguy50035 on 2011-10-14
I ran all of those commands.  I can now boot to a command line for linux 3.  Still no desktop.  The only issue I had, was I was unable to umount /mnt/dev.

---

### Post by garvinrick4 on 2011-10-15
> The only issue I had, was I was unable to umount /mnt/dev.
Do not worry about it.

Can you run
```
startx
```
or
```
sudo /etc/init.d/lightdm restart
```

 > I can now boot to a command line for linux 3
Does this mean you can boot into Unity but not Gnome3 (gnome-shell)
or not getting any Graphic User interface at all in both.

---

### Post by tubaguy50035 on 2011-10-15
Garvin, I appreciate your help.  I just ended up re-installing straight from 11.10.  For the record, I was on 11.04.  I had done no customization to it.  I basically just used it for the Ubuntu Terminal.

---

### Post by garvinrick4 on 2011-10-15
> I basically just used it for the Ubuntu Terminal.
Did you by chance have server version of 11.04 installed?

Anyway glad you are running.

---

### Post by tubaguy50035 on 2011-10-15
I did not.  It was the desktop version.  I have server installed on a different box :D  But not this virtual machine.

---

