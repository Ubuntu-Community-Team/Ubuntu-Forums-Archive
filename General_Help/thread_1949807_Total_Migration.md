---
title: "Total Migration"
date: 2012-03-31
forum: General Help
---

### Post by Watchlord on 2012-03-31
Well...not sure where to start. I'm still a bit new to Ubuntu. Anyway, I'm running 11.04 on netbook (one hard drive). I'm triple booting Windows XP, Ubuntu 11.04, and Backtrack 5 btw. 
 
 
I will be getting a new desktop and a new notebook. I've spent hours customizing my netbook. Everything from the icons in burg/grub to all the fancy compiz things. I really don't want to have to try to remember everything I did and repeat it on two computers.
 
 
Is there a program or method that will let me essentially clone everything on the HDD or partition and move it to new hardware. I don't mind tweaking it to work with the new computer, just digging up my customizations is painful.
 
 
I will be dualbooting on the new computers as well, so if it will let me clone the bootloader too, that'd be great.
 
 Sorry for the noobish post, I'm generally good with this kind of thing. It's been a long day, so any help would be greatly appreciated.

---

### Post by Paddy Landau on 2012-03-31
Three different ideas for you:

If you make a fresh installation of Ubuntu, you can just copy the *entire* home folder (/home/user), including all hidden folders and files, to your new installation. That will not clone the drive, but it will carry across all your settings and data.

If you want to clone the *entire* drive (not a good idea with Windows), you can use [CloneZilla]("http://www.clonezilla.org/"). It runs from a CD or USB. Afterwards, you will need to change your computer's name in all three systems (Windows, Ubuntu and Backtrack) to prevent conflict on the network with the first computer.

If you want to clone just Ubuntu, do a clean installation of Ubuntu on the new computer (to get the bootloader installed). Then use CloneZilla to clone just the Ubuntu partition. Afterwards, you will have to repair Grub.

---

### Post by Watchlord on 2012-03-31
The third option looks best. I have custom themes, profile pics, icons, login screens, compiz, etc. So I should install Windows, then Ubuntu. After that, I can clone Ubuntu from the netbook and write over the new Ubuntu which is on the new computers. Are you saying Ubuntu will recognize the hardware changes automatically and it will look exactly the same?

---

### Post by Lars Noodén on 2012-03-31
Copying the /home folder will get your configurations.  

You can copy the applications that you've installed or uninstalled using dpkg and apt-get

```

dpkg --get-selections > pkgs.list

```

Then on the new machine:

```

sudo dpkg --set-selections < pkgs.list
sudo apt-get dselect-upgrade

```

---

### Post by Watchlord on 2012-03-31
What about save games and system wide changes I've made?

---

### Post by Paddy Landau on 2012-03-31
> **Watchlord said:**
> Are you saying Ubuntu will recognize the hardware changes automatically and it will look exactly the same?
Yes, it should -- assuming that it has the drivers for that hardware. Linux is great like that.

> **Watchlord said:**
> What about save games and system wide changes I've made?
Copying across the home folder will carry the settings across. Remember that, whilst Windows holds settings in the Registry (which affects all users), Linux holds settings in the home folder (which affects only the user). There are no "Registry" settings to copy across in Linux. Two users in Linux cannot change each other's settings.

---

### Post by Lars Noodén on 2012-03-31
> **Watchlord said:**
> What about save games and system wide changes I've made?

Saved games should be in the home directory of the user that was playing.  

For system-wide configurations, you can backup /etc

---

### Post by Watchlord on 2012-03-31
Can I just copy the bootloader and update it too in the terminal? I will probably copy the entire Ubuntu partition just to be sure.

---

### Post by Paddy Landau on 2012-04-01
> **Watchlord said:**
> Can I just copy the bootloader and update it too in the terminal?
Possibly. CloneZilla, I believe, can clone the bootloader. The problem is that the bootloader points to a specific place; will that place still be the same on the new system? That's why I suggested (in my third option) to install Ubuntu before cloning over it.

---

### Post by Watchlord on 2012-04-01
I will install a dummy copy of Ubuntu and then write over it with the cloned version. I have experience repairing and custimizing bootloaders with backgrounds and Icons (I installed Windows after Ubuntu). I just don't know how to copy it. I think BURG (I think it runs on top of GRUB) can addapt to new OSs with an update, I just want to keep my custom icons and backgrounds for BURG. It took forever to get it to work.

---

### Post by Paddy Landau on 2012-04-01
BURG, as I understand, was a fork of Grub; in other words, it does not run on top of Grub but rather is an enhancement of Grub.

You can try, as an experiment, cloning the boot sector across the partitions, but as I have no experience of doing that (except when cloning an entire drive), I cannot say what issues you may have.

---

### Post by Watchlord on 2012-04-01
I just don't know how to copy the bootloader and where to put it on the new computer.

---

### Post by Paddy Landau on 2012-04-01
> **Watchlord said:**
> I just don't know how to copy the bootloader and where to put it on the new computer.
Sorry, I can't help you there. I would imagine that CloneZilla would know, but don't try it if you have any valuable data on your disk -- you may wipe out your partitions! You may have to decide to live with Grub, as (I believe) Burg is no longer maintained.

---

### Post by oldfred on 2012-04-01
The MBR has two parts. One is the bit of boot code used to find the rest of the boot code on the hard drive. And the last bit is the partition table. 

If you you attempt to copy the entire MBR you will copy partition table and that will totally corrupt system. It is not difficult to use liveCD or USB to reinstall grub2's boot loader to a MBR. UUID may be in grub, fstab and a few other places that should be reset depending on how you copy. Many have issues with the clone, which really works best to restore a system or to move  exactly the same size drive when old drive is not used again.

Often a new install and copy /home and a few settings from /etc(if manually edited) works the easiest.

If new system happens to have newer gpt partition table do not attempt to copy system as it has more internal structures.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by Watchlord on 2012-04-01
Can I migrate the /home and /etc folder from a 32 to a 64 install?

---

### Post by oldfred on 2012-04-01
Yes, but I would verify each /etc setting first. If changing versions/upgrading an old setting in /etc may conflict with the new version or not be required anymore.

All the settings and data in /home will convert. I did it back with 9.04 as 32 bit to 9.10 as 64bit. While you can upgrade /home settings, you cannot necessarily go back to previous version as new settings may conflict with older version. Also really should not share /home. I found that the setting in /home were tiny and now I just copy to a new install. My /home is about 1 or 2GB with 75% of that as .wine with Windows version of Picasa(3.8).

---

### Post by Paddy Landau on 2012-04-01
I would concur with oldfred. I have found it easier to back up the data, do a clean installation of Ubuntu, and restore the data. There are not many settings that you lose by doing that, and often many of the old settings do not "fit" with the newer version of Ubuntu.

You can selectively restore settings as needed if they are held in hidden folders (e.g. .gimp, .thunderbird), but it is harder when they are stored in gconf or dconf.

I only once cloned an entire partition of Ubuntu to another machine, and I had a specific reason for doing so then; there were a few items that needed changing afterwards (e.g. UUID and network name).

---

### Post by Watchlord on 2012-04-01
Thanks everyone.

---

