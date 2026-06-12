---
title: "How can I boot from USB using Grub?"
date: 2012-04-10
forum: General Help
---

### Post by HotForLinux on 2012-04-10
How can I boot a linux system in an USB memory stick that uses the syslinux bootloader in a PC with Ubuntu+Grub (legacy grub) but that it has not the option to boot from USB in the BIOS?

Inside the USB:

```

casper/
    filesystem.size
    filesystem.squashfs
    initrdf.gz
    initrd.gz
    initrds.gz
    vmlinuz

isolinux/
    boot.cat
    memtest
    isolinux.bin
    isolinux.cfg
    vesamenu.c32

ldlinux.sys
preseed/
README.diskdefines
syslinux/
    boot.cat
    memtest
    syslinux.bin
    syslinux.cfg
    vesamenu.c32


```

---

### Post by oldfred on 2012-04-10
Some have reported this works:

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

My BIOS boots directly, so I have not had to try it.

---

### Post by HotForLinux on 2012-04-10
> **oldfred said:**
> Some have reported this works:

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

My BIOS boots directly, so I have not had to try it.


Sorry, but I don't see how. Is it true what they say?

---

### Post by idoitprone on 2012-04-10
> **HotForLinux said:**
> Sorry, but I don't see how.

So let me get this straight?

Ubuntu have grub legacy and your trying to boot your usb

it shouldnt be that hard, just chainload the usb

edit your menu.lst file
and append this


```
# USB entry
title usb
 rootnoverify (hd1,0)
 makeactive
chainloader +1
```Arch have great docs on grub legacy
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

---

### Post by gleedadswell on 2012-04-10
I found this

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/")

very useful for learning how to do it.  It guides you through reformatting a usb drive with a fresh, bootable FAT32 partition, installation of grub2 to the usb and provides you with some simple example grub.cfg files.

---

### Post by HotForLinux on 2012-04-11
> **idoitprone said:**
> 

edit your menu.lst file
and append this


```
# USB entry
title usb
 rootnoverify (hd1,0)
 makeactive
chainloader +1
```Arch have great docs on grub legacy
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

Yes, I want to know how can I boot a linux system in a USB mem stick (aka pendrive) plugged in a PC whose BIOS cannot be configured to boot the PC off an USB drive.
Right now the PC boots with legacy GRUB, and the system in the USB has a syslinux bootloader which, unless there's a need to change it, I would like to leave it.

Thanks but I don't see what does (hd1,0) have to do with the USB. How will grub guess I want to boot the USB with those commands?

---

### Post by HotForLinux on 2012-04-11
> **gleedadswell said:**
> I found this

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

very useful for learning how to do it.  It guides you through reformatting a usb drive with a fresh, bootable FAT32 partition, installation of grub2 to the usb and provides you with some simple example grub.cfg files.

How?. I don't want to reformat a usb, I don't see why should I install grub2 in the usb and I don't see how could I boot it in a PC whose BIOS cannot be configured to boot from the USB.

(I suppose that I only need the commands I should give to grub to boot the usb, but I don't know if that is possible and how.)

---

### Post by idoitprone on 2012-04-12
> **HotForLinux said:**
> Yes, I want to know how can I boot a linux system in a USB mem stick (aka pendrive) plugged in a PC whose BIOS cannot be configured to boot the PC off an USB drive.
Right now the PC boots with legacy GRUB, and the system in the USB has a syslinux bootloader which, unless there's a need to change it, I would like to leave it.

Thanks but I don't see what does (hd1,0) have to do with the USB. How will grub guess I want to boot the USB with those commands?

(hdx,y)

the x refers to the drive number, which should be the usb and the y refer to the partition number
(hd1,0) refers to harddrive 2 and partition 1 which should be your usb

read the arch docs.

You have to add that entry to menu.lst of your pc grub legacy
Grub will chainload to the usb which it should be doing to boot off the usb

plug in the usb and post output of ```
blkid
```

---

### Post by HotForLinux on 2012-04-12
> **idoitprone said:**
> (hdx,y)

the x refers to the drive number, which should be the usb and the y refer to the partition number
(hd1,0) refers to harddrive 2 and partition 1 which should be your usb

read the arch docs.

You have to add that entry to menu.lst of your pc grub legacy
Grub will chainload to the usb which it should be doing to boot off the usb

plug in the usb and post output of ```
blkid
```

In Grub's command line I write:
rootnoverify (hdx,0)
makeactive

(for x=1,2,3,4,5)

And I receive an:
[COLOR=Red]Error 21: Selected disk does not exist[/COLOR]

**blkid** shows the partitions in the HD as:
sda1, sda2,... together with their UIDs,
and the two partitions in the USB drive as: 
sdb1 and sdb2 (the one with the bootloader) together with the UIDs. So, I understand that it should be (hd1,1) for Grub,  but gives the same error message after the **makactive** command for all (hdx,1) and for every combination of x and y I try.

What I think is that those commands must work only in PC's whose BIOS can be configured to boot off an USB drive. Isn't it like that? or ... any other suggestion?

---

### Post by iponeverything on 2012-04-12
usb boot from the bios is possible because a skeleton usb driver is built into the bios. -- booting to usb from grub won't be possible if the system can't see it.

---

### Post by HotForLinux on 2012-04-12
> **iponeverything said:**
> usb boot from the bios is possible because a skeleton usb driver is built into the bios. -- booting to usb from grub won't be possible if the system can't see it.

I don't understand what you mean neither in the first sentence nor in the second. You are talking about all PCs, the new ones, some, or the one I'm talking about?

---

### Post by iponeverything on 2012-04-12
i know its hard to follow.

In systems where there is a BIOS option that allow booting from USB, there is very basic USB driver built into the BIOS. This basic fact is the reason that the USB device is available as bootstrap option. 

If the system in question does not have a USB driver built into the BIOS, the system is blind to its existence.. follow?

---

### Post by HotForLinux on 2012-04-12
> **iponeverything said:**
> i know its hard to follow.

In systems where there is a BIOS option that allow booting from USB, there is very basic USB driver built into the BIOS. This basic fact is the reason that the USB device is available as bootstrap option. 

If the system in question does not have a USB driver built into the BIOS, the system is blind to its existence.. follow?


"the system is blind to its existence..."... therefore Grub can't boot it in any way..... right?

---

### Post by iponeverything on 2012-04-12
> **HotForLinux said:**
> "the system is blind to its existence..."... therefore Grub can't boot it in any way..... right?

Correct -

---

### Post by HotForLinux on 2012-04-12
I have never updated a Bios and this PC is more or less 6 years old. Do you think it is worth updating it, if there is an update? I mean, even if this functionality is not available in the update (which I ignore if it is possible). Also, is it risky to update the BIOS?

---

### Post by iponeverything on 2012-04-12
generally a BIOS update is not risky. If there is one available - there is usually information about what the update addresses with update.  BIOS updates usually just address bugs -- I have never seen one add missing functionality.

I wouldn't update if your not having any issues.

---

### Post by HotForLinux on 2012-04-12
Thank you, iponeverything. I'll mark the thread as solved, then.

---

### Post by HotForLinux on 2012-04-13
I want to do the same thing but with an Apple MBP3,1 system that has rEFIt and Grub2 installed.
I want to know how can I boot the system in the USB. Maybe instructing Grub to do so.
When I boot with the USB plugged in, there's an icon for each system installed: MacOS, Ubuntu ,.. and an icon for the USB: Tux with an USB drive. But I cannot boot choosing that option because a message says that booting with external devices is not supported.

I still don't know if this happens always, but at least once after playing with Grub at boot time, trying to boot the system in the USB, and then choosing to boot Ubuntu, Ubuntu started with the pointer (cursor) frozen. Only after unplugging the USB I could use the touchpad to move the pointer.
I will post this in an Apple Thread and post here the link.

Link to the similar problem in Apple+Grub2:
[http://ubuntuforums.org/showthread.php?p=11840641](http://ubuntuforums.org/showthread.php?p=11840641)

---

