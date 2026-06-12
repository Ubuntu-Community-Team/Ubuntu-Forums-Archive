---
title: "Can't boot up, i think i killed my computer! HELP PLEASE!"
date: 2011-03-16
forum: General Help
---

### Post by igotsanevo4g on 2011-03-16
I decided to poke around and check to see if i could enable desktop effects on my PC, and it said that it needed to install a new proprietary nvidia driver, so i said why not and installed it.

It prompted me to reboot, so i did and when it booted back up it would NOT boot into the GUI or anything, just to the terminal said - "Ubuntu 10.10 julie tty1" and wanted me to enter username/password, so i did and still no luck, its as if all i can access is the terminal.

Ive tried updating GRUB, and all the other recovery options and im totally at a loss. I cant even boot into my dual boot WinXP, im typing this from my phone.

Can anyone help me out here, i really really do not want to format and reinstall.

PLEASE HELP :(

---

### Post by falko on 2011-03-16
You can try to boot from a live/rescue CD (such as the Ubuntu Live CD or Knoppix), mount the hard drive, do a chroot and run
```
sudo sh NVIDIA* --uninstall
```
to uninstall the Nvidia drivers.

This should give you the idea: [http://www.howtoforge.com/how-to-reset-a-forgotten-root-password-with-knoppix](http://www.howtoforge.com/how-to-reset-a-forgotten-root-password-with-knoppix)

---

### Post by marshmallow1304 on 2011-03-16
Perhaps the nVidia driver is not configured correctly.  Try
```
sudo nvidia-xconfig
sudo reboot
```

---

### Post by igotsanevo4g on 2011-03-16
No go on the configuring nvidia drivers and i cant make a live cd because the computer is dead :/

---

### Post by Coder68 on 2011-03-16
Download a live CD on the computer you are using to post this.  Or, if you are that desperate, buy one from Ubuntu.  I would think you have some friends that could burn a disc for you.

Good luck,

C68

---

### Post by igotsanevo4g on 2011-03-16
Typing this from my phone lol

I'll see if i can get ahold of one.

Any other ideas guys?

---

### Post by mma8x on 2011-03-16
If you can boot into a terminal, why can't you run the commands listed above from there?

---

### Post by igotsanevo4g on 2011-03-16
I have tried them, no success.

---

### Post by igotsanevo4g on 2011-03-16
I have tried em, they didnt work.

---

### Post by falko on 2011-03-16
But you installed this computer with the Ubuntu Live CD, didn't you? Then you can use this Live CD to rescue your computer.

---

### Post by igotsanevo4g on 2011-03-16
Of course i did, but of course when i actually need the Live CD again, its no where to be found.

---

### Post by sml156 on 2011-03-16
I copied this from  [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
this will fix windows but not Linux

Well, it’s actually fairly easy to fix the in XP and Vista. All you have to do is load up the Recovery Console and  run a simple command. All of your data, applications, settings, etc are  still intact on the drive and once the MBR is fixed, the computer will  load normally.
 So how can you repair your damaged MBR? Here are the steps to follow:
 1. First, restart your computer with the Windows XP setup disk in the  CD drive. If you don’t have your original disk, borrow one or download a  ISO image from a torrent site.
 2. When prompted, boot from the CD drive by pressing any key. If  Windows loads automatically, you will first have to enter the BIOS setup  and change the order of the boot devices to start with the [[COLOR=#960000][/COLOR]]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/#")
.
 [[IMG]http://helpdeskgeek.com/wp-content/pictures/2009/02/changebootorder-thumb.png[/IMG]]("http://helpdeskgeek.com/wp-content/pictures/2009/02/changebootorder.png")
 3. Once the setup loads, you will see the option to press **R** to repair a Windows installation.
 [[IMG]http://helpdeskgeek.com/wp-content/pictures/2009/02/repairwindows-thumb.png[/IMG]]("http://helpdeskgeek.com/wp-content/pictures/2009/02/repairwindows.png")
 4. Once the Recovery Console loads up, you will have to type in a  number that corresponds to your Windows installation. This is normally  just 1. and then type in the Administrator password.
 [[IMG]http://helpdeskgeek.com/wp-content/pictures/2009/02/recoveryconsole-thumb.png[/IMG]]("http://helpdeskgeek.com/wp-content/pictures/2009/02/recoveryconsole.png")
 5. Now at the prompt, type in **fixmbr**. Your damaged  MBR will now be replaced with a new master boot record and your computer  should now be able to boot properly. Note that you may also want to run  the **fixboot** command to repair the boot sector with a new one.
 Also, make sure you only use these commands on a system with one  operating system installed. If you have more than one operating system  installed, fixmbr and fixboot could mess up everything.

---

### Post by igotsanevo4g on 2011-03-16
Screw it, ill just do fresh installs after extracting what i can.

nothing to important was on there thank god.

---

