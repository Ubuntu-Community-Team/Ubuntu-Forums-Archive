---
title: "Some Quick Questions Before Installing Ubuntu 9.10"
date: 2009-12-31
forum: General Help
---

### Post by manco on 2009-12-31
Okay, I've been thinking about this for awhile now and I've decided I'm going to dual-boot my laptop with Vista Home (currently installed) and Ubuntu 9.10

1) If for some reason I don't want Ubuntu & GRUB on my laptop anymore, how easy is it to delete them? (i.e. like my laptop was before I installed Ubuntu)

2) For now, my HDD will be partitioned primarily for Windows Vista.  If I want to adjust my Windows vs Ubuntu partition ratio, how easy is it?

3) My laptop is a Dell Inspiron 1525.  It has the Media Direct button.  If I install Ubuntu, will I have any problems with the Media Direct button working correctly?

Thanks

---

### Post by kestrel1 on 2009-12-31
If you use a WUBI install you would be OK, but I don't think 9.10 currently works with wubi. You could go back to 9.04 if you want a wubi install though.
If you want to adjust the partition ratio it shouldn't be too much problem, but Vista may get upset. To be honest I would be inclined to use Virtual Box to try ubuntu before you install it properly. That way you will see if you like it or not.

---

### Post by Syndri on 2009-12-31
Burn the iso image to a cd
follow the on screen instructions
it is very simple to install
DONT use wubi
it messed up my install and i had to reinstall windows 7 and  ubuntu

---

### Post by kevinatkins on 2009-12-31
To check whether the Media Direct button will work, just boot the machine from the Ubuntu Live CD - nothing will get installed to your hard drive, but you will be able to ascertain that things work to your satisfaction. Just remember that performance from the Live CD will be slow and not indicative of the sort of speed you'll get from a proper hard disk installation.

---

### Post by aklo on 2009-12-31
> **manco said:**
> Okay, I've been thinking about this for awhile now and I've decided I'm going to dual-boot my laptop with Vista Home (currently installed) and Ubuntu 9.10

1) If for some reason I don't want Ubuntu & GRUB on my laptop anymore, how easy is it to delete them? (i.e. like my laptop was before I installed Ubuntu)

2) For now, my HDD will be partitioned primarily for Windows Vista.  If I want to adjust my Windows vs Ubuntu partition ratio, how easy is it?

3) My laptop is a Dell Inspiron 1525.  It has the Media Direct button.  If I install Ubuntu, will I have any problems with the Media Direct button working correctly?

Thanks


1.  Can't comment as i've never tried uninstalling before.

2. It is easy using the partition tools in ubuntu however occasionally stuff happens unexpectly so no guarantees, do your backup if neccessary. If you want to resize your windows partition, from what i've read when i did it last time (1 month ago) , you got to defragment your drive to make sure your win vista files are all move to the front of the disk...because when you resize your partition, files that are fragmented all around the drive will be lost resulting in corrupted files in your win vista...not very sure about it but better to be safe than sorry. Can't guarantee the results but i've tried it and nothing happened to me :D


3. No idea.

---

### Post by Pesky_Programmer on 2009-12-31
I am unfamiliar with Windows Vista but I am sure that you can get a recovery disk for Vista if one did not already come with your laptop. You will want to look into this before you install Ubuntu. You may also want to back up anything of importance to a Usb Drive or cds/dvds, just in case.
 
Here is some background you will need to know to better understand how your computer boots.
 
The first thing to load in your computer is the bios. You can think of this as a small operating system that is located on your mother board. One of the most important functions of the bios is to find a MBR(master boot record) on a device, whether it be on a CD, HD, or usb Drive. Once a MBR is found the bios fallows the instructions contained with in that file, telling it where the rest of the OS is. Currently Your MBR simply points to the Windows partition on your computer and it loads windows.
 
When you install Ubuntu as a multi boot OS it will create a new partition on your drive where Ubuntu will be installed. At the same time it will overwrite the MBR for your HD and instead of loading Windows or Ubuntu it will load GRUB. GRUB is a special tool that allows you to choose what OS to load. However Grub will be installed into the Ubuntu Partition.
 
That being said this is how you would have to uninstall Ubuntu if you don't like it. 
 
**Step 1:**Using either Gparted live or a Windows Partition tool delete the Ubuntu partition. 
BE CAREFUL NOT TO DELETE WINDOWS.
Then expand your windows partition to take up the unallocated space.
 
**Step 2:**Now when you reboot your laptop whats left of GRUB will try to load and have an error. This is because GRUB was located on the partition that you just deleted and the MBR is being told to only look for grub. So you must boot from the Windows Recovery disk to restore the MBR to its orignal state. I am unsure how to do this in vista but in Windows XP you simply use "fixmbr" command in the recovery console. Once done you computer will boot into Windows as it did before you installed Ubuntu.
 
I hope this helps if you need further explanation you can PM me.:)

---

### Post by manco on 2009-12-31
Thanks for all the replies.

I'm going to start by backing up my data, and then deleting an unused partition on my HDD.

I'll check out the Media Direct thing while on the Ubuntu live CD as well.

---

### Post by Strongman332 on 2009-12-31
if it uses media direct 3.5 or higher you are safe

---

### Post by manco on 2009-12-31
> **Strongman332 said:**
> if it uses media direct 3.5 or higher you are safe
Looking under "About Media Direct" it says it's version 3.5.4706 :)

---

### Post by manco on 2010-01-01
Just finished the install of 9.10 on my laptop; works great.

Haven't checked out Media Direct; when I press the button in Ubuntu it brings up Rhythmbox :confused: but that doesn't really bother me.

But I'm having great compatibility right now and I love it.  Currently I'm doing a dual-boot with Vista Home, but if I like Ubuntu enough I might go solely to Linux :KS

Happy New Year everyone!!!

---

