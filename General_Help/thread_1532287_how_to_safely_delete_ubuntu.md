---
title: "how to safely delete ubuntu"
date: 2010-07-16
forum: General Help
---

### Post by jonreed1991 on 2010-07-16
i do not have a dual boot. i had windows 7, installed lucid, and got rid of windows 7. i was wondering how to get rid of lucid and install windows 7.

ps. i have windows 7 installation disk

please help!

---

### Post by Nick_Jinn on 2010-07-16
Windows automatically deletes Ubuntu. Windows hates competition. That is why you have to install windows first if you want to dual boot.

There are some improvements in windows 7 but there are also some quirks and even more hardware problems than there is in Ubuntu.....windows is designed to suck money out of your pocket.

I would keep a distro of linux on hand just in case...its great for free software.



but yeah, Windows will delete everything. It doesnt even give you the option of dual booting like linux does. If you try to install windows it will delete everything, like it or not.




Otherwise, boot from CD and install Gparted, unmount the hard drive (Can only be done when booting from CD or pen drive) and delete the partitions before installing. 


If Ubuntu was too hard for you, maybe try Linux Mint....its easier to use than Ubuntu. Just make sure you dual boot it AFTER you install Windows 7, not before.

---

### Post by jonreed1991 on 2010-07-16
thanks a lot for your quick reply.

i am looking for a fresh start, and an empty, brand new hard drive after installing windows 7, so no worries there. 

i am still curious though as to how and when i install gparted and how to unmount the hard drive.

i was just thinking of going to disk utility and removing the partition from there... but im not sure how ill be able to install windows after that

---

### Post by dcstar on 2010-07-16
> **jonreed1991 said:**
> thanks a lot for your quick reply.

i am looking for a fresh start, and an empty, brand new hard drive after installing windows 7, so no worries there. 

i am still curious though as to how and when i install gparted and how to unmount the hard drive.

i was just thinking of going to disk utility and removing the partition from there... but im not sure how ill be able to install windows after that

Windows installs Windows, there is nothing for **you** to do.

---

### Post by WorMzy on 2010-07-16
> **Nick_Jinn said:**
> Windows automatically deletes Ubuntu.

Er. Not quite. It'll certainly overwrite the MBR so that you can't *boot* into anything other than Windows, but you can partition your system so that any original OS' remain, and Windows gets installed to it's own partition.

OP: If you want to remove Ubuntu completely, just use the Windows installer to delete your Ubuntu and Swap partitions, then install Windows to the entire disk.

---

### Post by jonreed1991 on 2010-07-16
when i put the windows 7 installer cd in my computer pretty much does what it does for games, such as the sims 3. instead of running the disk it comes up as a folder with a bunch of documents

---

### Post by WorMzy on 2010-07-16
What? Where did you get that idea? :confused:

---

### Post by jonreed1991 on 2010-07-16
???? what idea??

---

### Post by WorMzy on 2010-07-16
The idea that you couldn't use Windows on your PC again, which you edited away just before I posted. :P

You need to restart your PC and boot into the disk to use the Windows installer.

---

### Post by jonreed1991 on 2010-07-16
hahahaa i had a feeling you responded to my pre-edited reply. 

but anyways, im a huge noob.

so explain, if you would, i restart my computer and put the windows installer disk in while my computer is booting up? (dont laugh! lol)

---

### Post by WorMzy on 2010-07-16
Leave the disk in the disk drive when you restart the PC, when it powers on and shows the POST screen, it should say something like 'Press Del to enter bios settings', at this point you need to press a specific key to bring up the "Boot to device" menu. Unfortunately, there's no way for us to know what this key will be on your PC, though it'll probably be Esc, F1, F2...F12, or Del, so keep an eye out for a message telling what to press, or just press as many of those keys as you can and hope that one of them will show the boot device menu. When you get the boot device menu, choose to boot from the CD drive.

Alternatively, you can enter the BIOS settings and change the boot order of devices there. You'll need to make the CD drive the first device on the boot list.

NOTE: If you see the grub screen, or the Ubuntu logo, then you've gone too far. You'll need to restart and try again.

---

### Post by jonreed1991 on 2010-07-16
WorMzy i couldnt have asked for a better reply. you've been most helpful and i'll give this a try in a couple hours when i have my installation disk on me (currently not home). =) thanks so much!

---

### Post by WorMzy on 2010-07-16
No worries. I forgot to say that you should try just leaving the disk in the drive and letting the PC boot normally the first time you try, your PC could be set up so that it automatically boots from a disk if there's a bootable one present in the disk drive. If it detects the CD as bootable, you'll probably be prompted to press any key to boot from it.

---

### Post by Nick_Jinn on 2010-07-16
> **WorMzy said:**
> Er. Not quite. It'll certainly overwrite the MBR so that you can't *boot* into anything other than Windows, but you can partition your system so that any original OS' remain, and Windows gets installed to it's own partition.

OP: If you want to remove Ubuntu completely, just use the Windows installer to delete your Ubuntu and Swap partitions, then install Windows to the entire disk.


You are correct actually for store bought windows 7. However, a lot of re-installation disks only have the option of erasing entire disk. 

So if you are using a store bought windows 7 you can delete the partitions manually when installing, but some of the system disks dont have that option and will only restore your entire system to factory settings.....if you have a system restore disk you probably dont need to do anything. If you bought an upgrade or have a bare bones, then you can either delete with Gparted from pen drive or delete from windows installer if it has that.


I was thinking primarily about system restore disks, but you cant go wrong if you boot with a pen drive or CD, install Gparted from the software manager (or its equal in standard Ubuntu) and delete the partition from there.....I dont think you can delete the partition from a mounted disk/drive, and it has to be mounted if you are using it, right?

---

### Post by WorMzy on 2010-07-16
Ah, you could be right there, I've only ever really installed Windows from OEM disks and the Vista recovery disk that came with my PC, it could be that some recovery disks are designed to just use the whole of a hard drive.

---

