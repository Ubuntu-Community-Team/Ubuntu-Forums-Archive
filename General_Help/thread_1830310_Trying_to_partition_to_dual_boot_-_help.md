---
title: "Trying to partition to dual boot - help?"
date: 2011-08-21
forum: General Help
---

### Post by adamhum3 on 2011-08-21
I'm currently running Elementary OS Jupiter, which is based on Ubuntu 10.10 anyway.

I want to dual-boot Windows 7 Professional.

I'm trying to partition my drive using gparted, however when trying to unmount, I get the error 'Could not unmount /dev/sda1 The partition could not be unmounted from the following mount points: /'

When I try running 'fdisk -l /dev/sda', I get 'Cannot open /dev/sda'

Any tips, or is there an easier way I can dual boot?

Cheers, 

Adam

---

### Post by cllewis91592 on 2011-08-21
well if you have a windows and an ubuntu cd you could do [this.]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") 

I haven't had a chance to try it myself but it seems like it should work. (if you want to do a clean install on your whole system that is.)

hope this helps in some way or another!

---

### Post by Nytram on 2011-08-21
I think it's because the root file system / needs to be always mounted. A way around it, is to boot from a live disk, usb or cd/dvd, and use gparted from there.

EDIT: Just checked on my system, and gparted cannot unmount root. Boot from a live disk instead.

---

### Post by catilley1092 on 2011-08-21
You shouldn't need GParted. Everything that you need to install any variant of Ubuntu is in the installer disc.

After booting from the disc, you have 2 options, try or install the OS, click install. Follow the prompts.

When you get to the partitioning section, you'll see your drive. Make sure that Windows 7 is defragged well, should you need to shrink it for the install.

You'll need 3 partitions, your main (/), home, & swap. The main can be as small as 10240GB, your home as large as desired, and your swap equal to the amount of your installed RAM (up to 4GB, or 4096MB).

Hope this helps!

Cat

---

### Post by adamhum3 on 2011-08-21
I'm not sure if I explained properly lol, I already have Elementary OS installed, I want to keep this how it is, but add Windows 7 on top of it, is this possible?

---

### Post by oldfred on 2011-08-21
Do you have a primary partition sda1-sda4 available  or have you used them all? Windows will only install to a NTFS primary partition set as active in windows or with boot flag from gparted or to unallocated free space with a primary partition available. 

Some have said gparted formated NTFS is not always read correctly by window's installer other have had it works.

---

### Post by adamhum3 on 2011-08-21
> **oldfred said:**
> Do you have a primary partition sda1-sda4 available  or have you used them all? Windows will only install to a NTFS primary partition set as active in windows or with boot flag from gparted or to unallocated free space with a primary partition available. 

Some have said gparted formated NTFS is not always read correctly by window's installer other have had it works.

I'm honestly not too sure. In gparted I have:

 /dev/sda1        ext4
 /dev/sda2        extended
     /dev/sda5    linux-swap

---

### Post by Topsiho on 2011-08-21
Then you have the possibility to create two primary partitions (/sda3 and /sda4) if there is space on the disk.

I can't advise you on how to proceed installing Windows. Always thought it should be installed first, as it claims all the disk space, but recently read it claims all available (that is: unallocated) disk space.

If that's so, you should create some unallocated disk space and install Windows in that.

Topsiho

---

