---
title: "Ubuntu Help - USB - Partitions"
date: 2011-06-22
forum: General Help
---

### Post by cmd.exe on 2011-06-22
Hi guys,
I need someone to explain how installing ubuntu on a usb effects anything, I know you have to do partitions or something but I was wondering, if I wanted my USB to be Ubuntu only do I have to make partions also do partions change the amount of space you can store files on with ubuntu? Like if I wanted to install some stuff and put some files on will it use space on the ubuntu partion or the second one.
cmd

---

### Post by nothingspecial on 2011-06-22
It's up to you, you get to choose when you install. How big is this usb drive? How do you intend to install ubuntu?

---

### Post by jerrrys on 2011-06-22
if you want to keep it simple, just install per this

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

and use the "persistance option".  this is where your changes will be keep

---

### Post by oldfred on 2011-06-22
If your flash drive is 4GB or less, jerrrys suggestion on persistence is best or maybe all you can do.

If your flash is 8GB or more then you can do a full install which is like any install to a second drive, but with some settings to reduce writes.

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by cmd.exe on 2011-06-23
> **jerrrys said:**
> if you want to keep it simple, just install per this

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

and use the "persistance option".  this is where your changes will be keep
:popcorn: I really just want to keep it simple and I'm not sure which USB I might be using I'm guessing a 4 gig or less since I use my 8gb for high file transfers. Do I just download the iso and burn it to the usb then boot the usb on the bios like you install windows?

---

### Post by wildmanne39 on 2011-06-23
> **cmd.exe said:**
> :popcorn: I really just want to keep it simple and I'm not sure which USB I might be using I'm guessing a 4 gig or less since I use my 8gb for high file transfers. Do I just download the iso and burn it to the usb then boot the usb on the bios like you install windows?Hi, yes you just download and then burn the iso, and change bios to boot from the usb stick. I have seen people having trouble putting ubuntu on a four gig because it says it requires 4.4, I believe if you have that issue there is a workaround but I am not sure what it is.

---

### Post by cmd.exe on 2011-06-23
Officeworks sells 4 gig usbs for $7 so I might get one soon. Should I get 64 bit or 32 bit?
Also I saw this article.
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by wildmanne39 on 2011-06-23
Hi, I run 64 bit, but the choice is yours, it runs a little faster in high demanding applications. The instructions for make pendrive is on the download page of ubuntu, that will tell the latest way to make it, I would do what it says.

---

### Post by cmd.exe on 2011-06-24
> **wildmanne39 said:**
> Hi, I run 64 bit, but the choice is yours, it runs a little faster in high demanding applications. The instructions for make pendrive is on the download page of ubuntu, that will tell the latest way to make it, I would do what it says.
Ok I got a 64 bit windows so I'm gonna install 64 bit, I'll hopefully get a 4 gig soon and I found the setup on the website. Thanks guys, I'll do this in the next few days.

---

### Post by C.S.Cameron on 2011-06-24
With a 4GB stick you can do a Persistent install using Startup Disk Creator from the Live CD, (or you can extract usb-creator.exe from the iso for use in Windows).

This setup uses FAT32 file system so you can access it from Windows for file transfer.

To access these files when booted from the drive you will find them in the folder cdrom. you may need to use gksu nautilus.

If you need more than the 4GB persistence allowed by the FAT32 system you can make a casper-rw partition.

---

### Post by cmd.exe on 2011-06-25
I'm going to install it today, 64 bit. I think my USB is a FAT32 and I'm just downloading the iso file from the Ubuntu site.

---

