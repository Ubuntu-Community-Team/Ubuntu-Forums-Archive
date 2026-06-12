---
title: "how can install grub boot loader?"
date: 2011-03-15
forum: General Help
---

### Post by Gianmaria on 2011-03-15
Hi

under ubuntu how can i install grub boot loader ?

is there a program that let me do it ?

i would like to add a grub load to an hard disk , and maybe to an usb stick and to a floppy disk

how can i do it?

thanks

---

### Post by dabl on 2011-03-15
I dunno about a floppy diskette -- not sure what the point of putting grub on a floppy would be.

However, for a USB stick or a hard disk drive, it is not difficult.  Let's say you have a USB stick with a single ext2 partition, and you installed some kind of modern Linux (i.e. that uses Grub2) on it, so there is /boot with kernel image, and /boot/grub with grub files, and /etc/default/ with a grub configuration file.

You can insert this USB stick in your computer, and it will be automatically mounted at /media/diskx, but you need to "sudo umount" it.  Now it is still inserted, but not mounted.  Run ```
sudo fdisk -lu
```

Let's say it is listed as /dev/sdd1

So, make a mount point:

```
sudo mkdir -p /mnt/USBSTICK
```

Now, mount the USB stick:

```
sudo mount -t ext2 /dev/sdd1 /mnt/USBSTICK
```

Now install grub on it:

```
sudo grub-install --root-directory=/mnt/USBSTICK  /dev/sdd
```

Now you have it installed -- note that we use the device name "sdd" not the partition name "sdd1", for installing grub.  Now unmount the USB stick:

```
sudo umount /dev/sdd1
```

After you try booting it, it should boot, but if there is a problem, you can edit the scripts at /etc/grub.d/ the same as for a normal Linux installation.  You can also edit /boot/grub/grub.cfg, but any edits there will not survive an "update-grub" cycle.

Hope this helps.

---

### Post by Gianmaria on 2011-03-15
> **dabl said:**
> I dunno about a floppy diskette -- not sure what the point of putting grub on a floppy would be.

However, for a USB stick or a hard disk drive, it is not difficult.  Let's say you have a USB stick with a single ext2 partition, and you installed some kind of modern Linux (i.e. that uses Grub2) on it, so there is /boot with kernel image, and /boot/grub with grub files, and /etc/default/ with a grub configuration file.

You can insert this USB stick in your computer, and it will be automatically mounted at /media/diskx, but you need to "sudo umount" it.  Now it is still inserted, but not mounted.  Run ```
sudo fdisk -lu
```Let's say it is listed as /dev/sdd1

So, make a mount point:

```
sudo mkdir -p /mnt/USBSTICK
```Now, mount the USB stick:

```
sudo mount -t ext2 /dev/sdd1 /mnt/USBSTICK
```Now install grub on it:

```
sudo grub-install --root-directory=/mnt/USBSTICK  /dev/sdd
```Now you have it installed -- note that we use the device name "sdd" not the partition name "sdd1", for installing grub.  Now unmount the USB stick:

```
sudo umount /dev/sdd1
```After you try booting it, it should boot, but if there is a problem, you can edit the scripts at /etc/grub.d/ the same as for a normal Linux installation.  You can also edit /boot/grub/grub.cfg, but any edits there will not survive an "update-grub" cycle.

Hope this helps.
**yes thanks a lot**
i can  do it with an hard disk , i mean the same procedure ?

i guess i will try
by the way i used to work with comand line under windows , but under ubuntu i don't know nothing
a program could be more easy i guess for the novice

---

### Post by dabl on 2011-03-15
> **Gianmaria said:**
> **yes thanks a lot**
i can  do it with an hard disk , i mean the same procedure ?



Yes, exactly the same.

> 

i guess i will try
by the way i used to work with comand line under windows , but under ubuntu i don't know nothing a program could be more easy i guess for the novice

"Linux isn't Windows".   :lolflag:

---

### Post by oldfred on 2011-03-15
Just installing grub to a device does not automatically set up the full grub.cfg menu that lets you boot other devices like an update-grub from Ubuntu does.

When I installed grub2 to my USB flash drive I had to manually create a grub.cfg and add boot stanzas. 

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

If booting a hard drive you can add boot stanzas for any operating system on the drive, but it has to be bootable or have another boot loader to chainload to.

---

### Post by WlaadDyaab on 2011-03-15
> **Gianmaria said:**
> Hi

under ubuntu how can i install grub boot loader ?

is there a program that let me do it ?

i would like to add a grub load to an hard disk , and maybe to an usb stick and to a floppy disk

how can i do it?

thanks

Do you mean that you want Windows to load before Ubuntu as soon as you open you computer?

---

### Post by Gianmaria on 2011-03-17
> **dabl said:**
> Yes, exactly the same.



"Linux isn't Windows".   :lolflag:
yes i know
i bought photoshop otherwise ubuntu is so awesome that i would like to put windows in the trash;)

does the ubuntu cd have a recovery feature for the grub?
i mean with a graphic gui?

**thanks**

---

### Post by dabl on 2011-03-17
> **Gianmaria said:**
> 

does the ubuntu cd have a recovery feature for the grub?
i mean with a graphic gui?



No, not directly, and not with a GUI. It has the needed grub-pc package with supported commands, for use at the CLI.

I'm afraid your search for GUI tools to use with Grub is not going to be successful. Grub is a very small, special purpose bootloader, designed only to start up the real OS.  Aside from the non-productive bloat that a GUI tool would add, Grub is not designed to be "easy for novices" -- novices should not normally be playing with it, lest they break the computer.

Here's a lot of information about it, with links to other sources: [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by Gianmaria on 2011-03-20
> **dabl said:**
> No, not directly, and not with a GUI. It has the needed grub-pc package with supported commands, for use at the CLI.

I'm afraid your search for GUI tools to use with Grub is not going to be successful. Grub is a very small, special purpose bootloader, designed only to start up the real OS.  Aside from the non-productive bloat that a GUI tool would add, Grub is not designed to be "easy for novices" -- novices should not normally be playing with it, lest they break the computer.

Here's a lot of information about it, with links to other sources: [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

thanks
but i think about a possibility to be not able to load ubuntu , for a mbr corruption
in this scenario i can boot ubuntu,rihgt?

windows cd has a recovery feature in the installtion cd

i mean in this scenario ,could the ubuntu installation cd fix the mbr (the grub loader)?
if yes how
thanks for your kindness

---

### Post by oldfred on 2011-03-20
No you cannot boot the hard drive, but neither can windows if the MBR is corrupted. The windows recovery is for disk or system issues like the Ubuntu recovery in the grub menu.

If you have either grub or windows issues you use the Ubuntu liveCD to repair the MBR. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

