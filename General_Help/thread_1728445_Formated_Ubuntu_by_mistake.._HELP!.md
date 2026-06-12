---
title: "Formated Ubuntu by mistake.. HELP!"
date: 2011-04-13
forum: General Help
---

### Post by lifeinthaboot on 2011-04-13
I had 3 partitions on my hard dive, Windows 7, Ubuntu, and just junk on the other. I installed Ubuntu in a way where it went to the GRUB filesystem? first, where it ask me to start in linux kernel 2.38.6 (can't really remember the kernel exact name) which was ubuntu, some other options, recovery mode, and at the very bottom was the one to go to Windows 7. I was in Windows and I wanted to get rid of my junk partition but I formated the Ubuntu partition by mistake. Now when it boots up it saying;        error: unknown filesystem. grub rescue>

I hope there is a way to save my files on Windows. I tried to reinstall Windows 7 back on my computer but it wouldn't go through since the grub startup thing is the main one, not the windows one. I hope someone understands me.

Thanks to anyone who can help me solve this newbie problem :D

---

### Post by Enigmapond on 2011-04-13
You can boot into an Ubuntu LiveCD and access any files that are still intact. They will be under "Places".

---

### Post by danjahner on 2011-04-13
If you are planning to reinstall Ubuntu, doing so on the deleted partition will fix your boot problems. It will reinstall grub and return to the practice of allowing you to select either Ubuntu or Windows on startup. 

If you want to revert back to only Windows, you will need to boot from a Windows CD and select the option to repair your Windows installation.

---

### Post by matt-fender on 2011-04-13
> **lifeinthaboot said:**
> I had 3 partitions on my hard dive, Windows 7, Ubuntu, and just junk on the other. I installed Ubuntu in a way where it went to the GRUB filesystem? first, where it ask me to start in linux kernel 2.38.6 (can't really remember the kernel exact name) which was ubuntu, some other options, recovery mode, and at the very bottom was the one to go to Windows 7. I was in Windows and I wanted to get rid of my junk partition but I formated the Ubuntu partition by mistake. Now when it boots up it saying;        error: unknown filesystem. grub rescue>

I hope there is a way to save my files on Windows. I tried to reinstall Windows 7 back on my computer but it wouldn't go through since the grub startup thing is the main one, not the windows one. I hope someone understands me.

Thanks to anyone who can help me solve this newbie problem :D

Well you have two choices, you can insert a liveCD and install Ubuntu to the now formatted partition, which will then restore GRUB, giving you the option to boot into Win7 again.

Or you can boot from CD with your Windows7 disc and restore the mbr

---

### Post by wilee-nilee on 2011-04-13
As suggested you can reinstall Ubuntu in the deleted partition, or you can just reload the mbr of the HD with the MS bootloader, which is done from the recovery or install dvd, it will boot you just need some help there.

You could also just install another bootloader to the mbr called lilo from a live Ubuntu cd to get to windows. What would you like to do of these 3 choices?

---

### Post by lifeinthaboot on 2011-04-13
Thanks guys :D. That was faster than I could have hoped. I'm going to try just installing Windows and installing Ubuntu back when 11.04 comes out or if that fails I will just install Ubuntu back like you suggested. I would just delete Windows but I have all my files on that drive. Portable hard drives, here I come.

---

### Post by matt-fender on 2011-04-13
Heres a helpful bit of documentation which will aid you in recovering your MBR to your existing windows installation

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by lifeinthaboot on 2011-04-13
Thanks everyone! I got it back working. I love you all!... in a Ubuntu community way :popcorn:

---

### Post by matt-fender on 2011-04-13
> **lifeinthaboot said:**
> Thanks everyone! I got it back working. I love you all!... in a Ubuntu community way :popcorn:

Awesome! so what did you choose to do? :popcorn:

---

### Post by lifeinthaboot on 2011-04-13
> If you want to revert back to only Windows, you will need to boot from a Windows CD and select the option to repair your Windows installation.

That is the one I used. I reinstalled Ubuntu also. Kinda bummed I lost my stuff on Ubuntu but I'm nowhere near frustrated as I was thinking I lost all my data on my computer. Thanks everyone for your help.

---

