---
title: "Totally screwed up my GRUB boot"
date: 2009-11-02
forum: General Help
---

### Post by FallenArms on 2009-11-02
Ok, so I originally was dual-booting Win7 Beta and Ubuntu.  That was working fine, though Grub called Win7 "Windows Vista (loader)", but that's not a big deal.  Anyways, I was trying to load Windows 2000 in there as well.  I set up a partition and installed it to that partition.  GRUB still showed only one Windows loader.  When I booted that one, it gave me Windows 2000.  Well, I decide, I'd rather have 7 than 2000 if I have to choose, so I deleted the partition with Windows 2000.  You're probably face-palming right now, but what's done is done.  I'm really tired and not thinking through my actions.

So the end of the story is, now my "Windows Vista (loader)" GRUB option takes me to an error that Windows 2000 is missing stuff to load (obviously), and I can't figure out how the heck to get Windows 7 back.  Could someone point me in the right direction?  Windows 7 was the original OS on this machine, so it's in the first partition (Dell Utility Partition is Partition 0) of the main drive (I have two hard drives).  It's labelled "C" in Windows, but of course, Linux doesn't use drive names.

---

### Post by jnew93 on 2009-11-02
Open up a terminal (under accessories), run this command:

```
sudo update-grub
```

then enter your password. Tell me if that works.

---

### Post by FallenArms on 2009-11-02
> **jnew93 said:**
> Open up a terminal (under accessories), run this command:

```
sudo update-grub
```then enter your password. Tell me if that works.
Thanks for replying.  It didn't.

---

### Post by louieb on 2009-11-02
Just to point you in the right direction. Microsoft has its own way of setting up multi-booting  2 installs of Windows. Only one install gets a boot loader. Delete that install and there is no way you can boot the other with GRUB. 

When a windows install is selected in the  GRUB menu - GRUB just passes control to the windows boot loader. 

I've read where you can get a copy of the Windows boot loader files and put them in your windows install. Have not tried it so don't know if that will work or not.
 
Does not sound like GRUB is the problem or the fix. You will need to get the windows boot loader fixed.  [Multibooters, Windows]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by FallenArms on 2009-11-02
Well, crap.  Things aren't looking good.  Luckily, I can access my Windows 7 partition from Ubuntu and back up all the data to my second hard drive, then use my Windows 7 ISO to reinstall the OS and format the HDD.  It's a pain, but less of a pain then trying to understand the Windows bootloader.  I'd just abandon Windows at this point and go all Ubuntu, but I need it for Zune and Visual Studio (my computer doesn't support virtualization).

Edit: Well, crap again, because while I know how to create a bootable USB drive from an ISO file in Windows, I don't know how to do it in Ubuntu.

---

### Post by dmgExP on 2009-11-02
I have been dual-booting linux and Windows XP on an older machine for ages.  I came across the perfect solution for that box: *create a boot stiffy!*

This is a good solution for any machine (with a stiffy drive) where the primary OS is Windoze.
It allows the Win-bootloader to manage the MBR and gives you the freedom to install and re-install Ubuntu as often as you like without the possibility of screwing up Windoze.

Simply format the stiffy with **mke2fs /dev/fd0**.
Mount the disk and create a /boot/grub subdirectory.
copy the files from Ubuntu /boot/grub into the new directory.
start **grub** and enter commands:
[INDENT][COLOR="Blue"][B]root (fd0)
setup (fd0)
quit[/B][/COLOR]
[/INDENT]

With this method you get no confusing boot menus when there are other users of the machine.
The **menu.1st** file on the boot stiffy is also easy to access and modify if necessary.

---

### Post by FallenArms on 2009-11-03
I get an error trying that:

mke2fs 1.41.9 (22-Aug-2009)
Could not stat /dev/fd0 --- No such file or directory

The device apparently does not exist; did you specify it correctly?


Seems like a simple problem...

---

### Post by RobOrr on 2009-11-03
if it helps, stiffy means floppy drive. If you're going to use phrases that may not be immediately obvious (my cousins, both 15, probably don't even know what a floppy disk IS) then please state what you mean as an aside or something. I got confused by what you were talking about until I saw you calling fd0. 

Most modern laptops don't have floppy disk drives, my desktop doesn't either.

 I don't know which version of Ubuntu you're using, but in Jaunty and Karmic (and maybe Intrepid and Hardy - can't remember) there is an option under System >  Administration called USB startup Disk Creator. This'll let you install a CD image onto the usb stick - you run BIOS and set USB to boot first, and this will work like a liveCD, which will let you edit grub and so forth.

Hope this helps. If you're looking for a USB stick that replaces your boot completely, I'm of no use, however googling grub USB bootloader got me tons of links. Hopefully one of those may help you.

---

### Post by sliketymo on 2009-11-03
Here: [http://ubuntuforums.org/showthread.php?t=1035999,]("http://ubuntuforums.org/showthread.php?t=1035999,some") good info.You might want to consider using EasyBCD if you are not comfortable with grub just yet.

---

### Post by FallenArms on 2009-11-03
I can't seem to get the USB Startup Disk Creator to work with any ISO file I have on my computer.  I can find it in the file browser, but it doesn't load into the program.  I already have a live CD of Ubuntu, but I don't think that'll do me much good.  Since Ubuntu somehow got installed to my second hard drive (I didn't mean to do that, but whatever), it's safe for me at this point to wipe my main drive completely and start from scratch-- I think.  Anyways, what I need now is to use either my Windows 7 ISO or my Windows XP ISO to create a USB bootable image for installation, then install it and format the main drive in the process.  How can I do that in Ubuntu?

---

