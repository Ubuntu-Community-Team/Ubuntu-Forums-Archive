---
title: "MultiOs Usb boot device"
date: 2009-10-26
forum: General Help
---

### Post by LinScape on 2009-10-26
Is there anyway to make a usb hold more than 2 operating systems? because i was planning to use my 8GB USB drive, partition it and install the following linux operating systems: KasperSky RescueCD Puppy Linux Ubuntu Karmic koala PCLinuxOS Fedora  but i dont know how make all the Operating systems bootable... can someone tell me how to do this?

---

### Post by mechro on 2009-10-26
Choose the one whose boot manager you prefer. Install that one last.

Having said that, getting more than one or two operating systems in 8GB is wildly optimistic.

---

### Post by Giblet5 on 2009-10-26
Go have a chat with the guys on pendrivelinux.com - that is what they do.

They'll even sell you the sticks.

---

### Post by lcs81 on 2009-10-27
you can try this page
[http://ubuntuforums.org/showthread.php?t=1288604&highlight=usb+boot+install](http://ubuntuforums.org/showthread.php?t=1288604&highlight=usb+boot+install)

---

### Post by teward on 2009-10-27
Just be careful having more than 2 primary partitions on your USB drive at once, because I've seen 8GB USB drives die when they have more than a certain number of partitions (usually once it gets past 3).

---

### Post by LinScape on 2009-11-03
wow never knew that more than 2 partitions could kill a usb device!

---

### Post by leorolla on 2009-11-03
Did it finally work?

When you make a Live USB, does it also get a MBR?

---

### Post by LinScape on 2010-05-09
No.

---

### Post by leorolla on 2010-05-10
Boot from Ubuntu, open GParted, and partition the USB.

Then boot from a LiveUSB of the distro that you want to install, plug in your 8GB USB and tell the installer to install to some of its partitions.

---

### Post by LinScape on 2010-06-15
But wouldn't the installer overwrite the MBR or something and cause a previous Linux installation not to appear? (like if i install Ubuntu first and then Windows and Windows replaces grub with its own boot loader).  But if i use multicd.sh with unetbootin would it work?

---

### Post by leorolla on 2010-06-15
> **LinScape said:**
> But wouldn't the installer overwrite the MBR or something and cause a previous Linux installation not to appear? (like if i install Ubuntu first and then Windows and Windows replaces grub with its own boot loader).  But if i use multicd.sh with unetbootin would it work?

Install Windows first.

If that's not possible (you have already installed Ubuntu), then you can fix this USB's MBR by booting from another USB. (A simpler way is to boot Ubuntu and ask GRUB to install itself to the Ubuntu partition. In this case, after Windows steals your MBR all you have to do is remove the boot flag from the Windows partition and add this flag to the Ubuntu partition.)

---

### Post by C.S.Cameron on 2010-06-15
With this method you can put multiple O/S on a thumb drive.

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by LinScape on 2010-06-17
@leorolla
how do i exactly ask grub to install itself to the correct partition?

@C.S.Cameron
it seems that the link you posted to the script downloads
the linux isos and installs them to the usb, correct?
but is it possible to modify the script since i already
have the isos on my hard drive and i can't afford to download them again.

it would be also easy to install all the operating systems first and then install ubuntu at the end?

---

### Post by leorolla on 2010-06-17
> **LinScape said:**
> @leorolla
how do i exactly ask grub to install itself to the correct partition?

@C.S.Cameron
it seems that the link you posted to the script downloads
the linux isos and installs them to the usb, correct?
but is it possible to modify the script since i already
have the isos on my hard drive and i can't afford to download them again.

it would be also easy to install all the operating systems first and then install ubuntu at the end?

The script will work but it will be only for fun (or rescue).

If some of these installations are meant for real use, like installing other programs and updating the kernel, you'd better give them a partition. You can't update the Karmic install with this type of iso booting for instance. Even if you have persistent memobry, updating the kernel will render it unbootable.

In the script you can supress the "wget" lines as long as a file with the same name is already present at the "-P" path, or you already have a file with the "-O" path/name.

Installing GRUB to the partition:
Boot with the Ubuntu 9.10+ installation.
Run ```
df /
``` to know which partition it is. Suppose it is /dev/sdb1.
Then run ```
sudo grub-install /dev/sdb1
```It may spit a warning message and maybe you will need to run the same command with a --force or such.

Note: 8GB is too little to have Ubuntu, Fedora and all the others.

---

### Post by C.S.Cameron on 2010-06-17
> it seems that the link you posted to the script downloads
the linux isos and installs them to the usb, correct?
but is it possible to modify the script since i already
have the isos on my hard drive and i can't afford to download them again.

I just ran the first part of the script, I did my own menuentries and loaded my own previously downloaded iso's.

---

### Post by oldfred on 2010-06-17
I did the same as C.S.Cameron, but also looked at this site:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)

Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount  the isos.

---

### Post by emarkay on 2010-06-18
> **leorolla said:**
> If some of these installations are meant for real use, like installing other programs and updating the kernel, you'd better give them a partition. You can't update the Karmic install with this type of iso booting for instance. Even if you have persistent memobry, updating the kernel will render it unbootable.

Could this be what is happening here in this thread - Updating Lucid on USB "Panics Kernel"?   Let me know here if so: [http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Thanks!

---

