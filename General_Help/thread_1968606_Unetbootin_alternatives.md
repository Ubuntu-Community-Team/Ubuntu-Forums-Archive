---
title: "Unetbootin alternatives"
date: 2012-04-29
forum: General Help
---

### Post by Ghost_Mazal on 2012-04-29
Lo all ,

can you guys give me some good alternatives to Unetbootin. I have been getting a lot of misses with it and getting unbootable usb's a lot lately.

Thank you

---

### Post by codemaniac on 2012-04-29
Here is a list for your reference .
[http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems](http://en.wikipedia.org/wiki/List_of_tools_to_create_Live_USB_systems)

---

### Post by Ghost_Mazal on 2012-04-29
Any specific ones that anybody can recommend ?

---

### Post by sudodus on 2012-04-29
Honestly, I have better experience with Unetbootin than with other tools to make USB boot drives. But there are always exceptional cases, where some other tool might be better. Try the built-in tool in Ubuntu (***Startup disk creator*** or something similar depending on language). Or clone the iso file directly according to this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")
You can also try ***multisystem***

But you might have another problem.
- The iso files are faulty, check with md5sum
- The USB drive is starting to fail, if it has fat32, check/repair it with chkdsk /f from Windows.
- There is some connection problem (worn or warped contact device). Try another USB drive and another USB port.
- Do you have problems only from or to one or several computers? If only one computer, what could make it different?

---

### Post by kurt18947 on 2012-04-29
> **sudodus said:**
> Honestly, I have better experience with Unetbootin than with other tools to make USB boot drives. But there are always exceptional cases, where some other tool might be better. Try the built-in tool in Ubuntu (***Startup disk creator*** or something similar depending on language). Or clone the iso file directly according to this link
[[COLOR=Red]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")
You can also try ***multisystem***

But you might have another problem.
- The iso files are faulty, check with md5sum
- The USB drive is starting to fail, if it has fat32, check/repair it with chkdsk /f from Windows.
- There is some connection problem (worn or warped contact device). Try another USB drive and another USB port.
- Do you have problems only from or to one or several computers? If only one computer, what could make it different?

I've had about the best luck with Unetbootin as well.  One problem I have is that my main desktop machine (Gigabyte  MA785GM-US2H) will only boot from a USB drive if the drive is first formatted in Windows.  A factory format will give a failure message every time. A USB key with factory format or formatted with Gparted will boot on an older Gigabyte M.B. or notebook, just not on the one M.B. with Award modular BIOS.

Edit:  Oops, Unetbootin *did* work.  I just downloaded a 32 bit .iso of 12.04 and wanted to create a live USB using 12.04 64 bit.  Unetbootin didn't see the freshly formatted USB drive.  Ubunutu's startup disk creator did work correctly this time.  I tried the live USB on a couple different machines and it booted correctly each time.  I'd had failures with it in the past.

---

### Post by RJARRRPCGP on 2012-04-29
> **Ghost_Mazal said:**
> Lo all ,

can you guys give me some good alternatives to Unetbootin. I have been getting a lot of misses with it and getting unbootable usb's a lot lately.

Thank you

Known issue. With Ubuntu, it will create a USB stick that just displays "Boot error" and nothing else.

---

### Post by Cheesemill on 2012-04-29
I've always found the most successful solution to be just to use dd:
```
sudo dd if=/path/to/filename.iso of=/dev/sdc
```
Where sdc is the correct partition identifier for your flash drive.

***[COLOR=Red]WARNING - This will erase all data on the specified device, so make sure you double check first.[/COLOR]***

---

### Post by Ghost_Mazal on 2012-04-29
> **Cheesemill said:**
> I've always found the most successful solution to be just to use dd:
```
sudo dd if=/path/to/filename.iso of=/dev/sdc
```Where sdc is the correct partition identifier for your flash drive.

***[COLOR=Red]WARNING - This will erase all data on the specified device, so make sure you double check first.[/COLOR]***

dd doesn't work at all.

The boot sequence now doesn't even see the stick at all.

---

### Post by Ghost_Mazal on 2012-04-29
And now I can't even use the USB stick again :( 

It keeps giving mount errors , I can't even wipe the partition and create a new one.

---

### Post by C.S.Cameron on 2012-04-29
usb-creator that comes on the Live CD works best for me, it can be run from the Live CD as Startup Disk Creator.
It used to come in the iso as a Windows executable, but I don't see the exe file in the 12.04 iso.

---

### Post by RJARRRPCGP on 2012-04-29
IIRC, **dd **worked like a charm for Squeeze. ;)

---

### Post by sudodus on 2012-04-30
> **Ghost_Mazal said:**
> And now I can't even use the USB stick again :( 

It keeps giving mount errors , I can't even wipe the partition and create a new one.
Too bad it does not work for you. I have been quite happy with the dd method (that I try to make safer with a script according to the link in post #4). Anyway, the following method works to restore the USB drive after that adventure.

Wipe the CD file system!
 
I should add, that if you want to re-use a USB drive that has been used like this, you should wipe it with dd (overwrite with zeros), otherwise grub-install doesn't want to write into the mbr area, because it recognizes the CD file system, iso9660.

Run the following commands to identify your USB drive and find its linux drive letter.
```
sudo fdisk -lu
``` and ```
sudo blkid
```

Finally wipe the USB drive with the following command. 
```
sudo dd if=/dev/zero of=/dev/sd[COLOR="Red"]X[/COLOR] bs=4096
``` where it is ***very important*** that you replace [COLOR="red"]X[/COLOR] by the *linux* drive letter for your USB drive and nothing else. The target drive will be completely wiped, not even PhotoRec can do anything after that operation.

And after that you can use ***gparted*** to make a new partition table (for example MBR) and suitable partition(s) for example FAT32 with boot and lba flags.

---

### Post by sudodus on 2012-04-30
> **RJARRRPCGP said:**
> IIRC, **dd **worked like a charm for Squeeze. ;)
+1+
[klx]ubuntu 11.10, 12.04
clonezilla
webconverger

---

### Post by leon951 on 2012-11-11
MultiSystem liveUsb best IMO
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
btw make sure your usb's name has no space in it or it wont work.

---

