---
title: "Help: How can I make a stable and permanent link to my Windows folers?"
date: 2010-11-28
forum: General Help
---

### Post by zhaotianwu on 2010-11-28
My computer is Windows + Ubuntu dual boot system. In Ubuntu, I want to make links on my desktop to folders in my Windows partition (NTFS) so that I can access them without having to go through Place=>Win=>Document and Settings=>My document...... procedures every  time.
However, I realize that the link that I made by right clicking it doesn't last long. Once I log out or restart Ubuntu, all these links are forgotten by Ubuntu, and if I click on them again, the system would report error opening them. 

Is there a way to setup a shortcut (that is stable and permanent) on your ubuntu desktop that allows you to access your Windows folders with ease? Thanks.

---

### Post by gerowen on 2010-11-28
Try making symbolic links.  Open a terminal and do the following:
```

cd Desktop
ln -s *pathtowindowsfolder*

```

---

### Post by zhaotianwu on 2010-11-28
> **gerowen said:**
> Try making symbolic links.  Open a terminal and do the following:
```

cd Desktop
ln -s *pathtowindowsfolder*

```

Is there a graphical way of doing it? And what does "*pathtowindowsfolder*" mean?#-o

---

### Post by Vaphell on 2010-11-28
1. yes, there is - right click on the folder you want to link to, there will be an option to create a symbolic link (no idea how the option is called in English, but it creates a 'copy' of the dir with an little arrow icon added). Move that link file wherever you want.
2. it means the path of the target directory in the folder hierarchy, most probably your partition is mounted in /media/Windows/ (or something similar) so this will be the beginning of the full path, followed by the part that looks just like in windows (/mount/windows/ is an equivalent of C: ). Simply mount it, navigate to /mount and see.

i suspect that your partitions are not automounted at boot, so probably you need to investigate the configuration of fstab file, which is responsible for mounting the partitions.

---

### Post by garvinrick4 on 2010-11-28
You can just simply chunk out a bit of hard drive and make a partition in NTFS and have
it mount in your linux and will be in use by windows as a # like G: and a sda# in Linux. Anything you want to use in both copy to NTFS partition.

---

### Post by zhaotianwu on 2010-11-29
> **garvinrick4 said:**
> You can just simply chunk out a bit of hard drive and make a partition in NTFS and have
it mount in your linux and will be in use by windows as a # like G: and a sda# in Linux. Anything you want to use in both copy to NTFS partition.

Pardon me for my ignorance, but I'm genuinely a beginner to Ubuntu. So, what is "mount"?:confused:

---

### Post by gerowen on 2010-11-29
> **zhaotianwu said:**
> Pardon me for my ignorance, but I'm genuinely a beginner to Ubuntu. So, what is "mount"?:confused:

Basically a "mount" or "mount point" is like a drive letter in Windows.  Any volume that you access on your computer is "mounted" before it is accessible, and it shows up like a folder.  For example, you plug in a thumb drive.  Most newer distributions will mount it automatically for you and put a nifty little icon on the desktop.  If you were to look in the address bar though it would "appear" that the contents of the thumb drive reside on your hard drive because it would read something like /media/thumbdrive; however this is just an empty folder where the device's partition was mounted.  You can do this manually however for special situations.  The "easiest" way is with the Ubuntu disk utility.  Let's say, as you stated earlier, that your hard drive is partitioned between Ubuntu and Windows.  If you click "System"->"Administration"->"Disk utility", you'll see all of the disks on your computer.  If you highlight the hard drive, you'll see your Windows partition.  If it's not already mounted you can highlight the windows partition just by clicking on it and clicking "Mount Volume".  Once you do this, I "believe" (could be wrong I don't have any windows installations on my hard drive) it will place an icon on your desktop, or under your "Places" menu.  If you want to know the folder that it has mounted your windows partition under just look in the Disk Utility window for the area that says "Mounted At" while the windows/NTFS partition is highlighted.

You've got the information to make the link you wanted, but since you're new I thought I would explain mounting.  I've attached a screenshot of the disk utility with the areas I mentioned highlighted.  If you want to get into the guts of using the command line to mount stuff manually, you can find a whole world of resources on google.

---

### Post by Megaptera on 2010-11-29
Useful guide here for sharing data between Ubuntu & Windows or "how to use a third partition between Linux and Windows to act as a storage partition."

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

