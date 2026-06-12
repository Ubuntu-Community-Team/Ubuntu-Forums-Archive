---
title: "install xp?"
date: 2011-01-26
forum: General Help
---

### Post by soryu on 2011-01-26
can i  install win xp to dual boot from ubuntu?

---

### Post by sikander3786 on 2011-01-26
Yes you can.

1. Windows needs a primary partition to boot from.

2. You need to recover Grub for dual booting Ubuntu/Windows after you are finished with Windows install.

If you need us to help you recovering Grub, once Windows is installed, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

If you feel confident and can do it yourself, see here.

[http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html](http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html)

---

### Post by HermanAB on 2011-01-26
Howdy,

Unless XP is for playing games, use VMware Player or Virtualbox.

---

### Post by sanderj on 2011-01-26
> **soryu said:**
> can i  install win xp to dual boot from ubuntu?

If you mean "boot *with* ubuntu", the answer is Yes.

Most easy way:
1) Remove everything from the harddisk, including partitions 
2) Install Windows XP (using the whole harddisk)
3) Install Ubuntu as second operating system: the Ubuntu install will take care of shrinking the Windows partition, and setting up the dual boot

HTH

---

### Post by soryu on 2011-01-26
thanks, looks like i'm going to have to install xp then reinstall ubuntu to dual boot.
easier. :lolflag:

---

### Post by Rubi1200 on 2011-01-26
> **soryu said:**
> thanks, looks like i'm going to have to install xp then reinstall ubuntu to dual boot.
easier. :lolflag:
No, I don't agree. The idea that Windows **must** be installed first is a fallacy.

If you can tell us more about your current setup we can tell you the best way to go about this.

There is no reason to wipe the drive clean, lose data and settings, and start all over again (unless you want to of course).

You can create space for Windows and install it. Of course, it will overwrite the MBR, but with 2 commands you can have GRUB back in control and with 1 more be happily booting Windows and Ubuntu.

From within Ubuntu or a LiveCD, post the output of these commands:

```
sudo parted -l

sudo fdisk -lu
```

---

### Post by matt_symes on 2011-01-26
Hi

> looks like i'm going to have to install xp then reinstall ubuntu to dual boot.

Why ? I'm with Rubi1200 on this one. There are plenty of people here who can talk you through the process of reinstalling grub.

Kind regards

---

### Post by soryu on 2011-01-28
let's do this.

 _____________________________________
/ Future looks spotty. You will spill \
\ soup in late evening.               /
 -------------------------------------
       \   ,__,
        \  (oo)____
           (__)    )\
              ||--|| *
mint01@mint01-desktop ~ $ sudo parted -l
[sudo] password for mint01: 
Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  28.7GB  28.7GB  primary   ext4            boot
 2      28.7GB  30.0GB  1283MB  extended
 5      28.7GB  30.0GB  1283MB  logical   linux-swap(v1)


mint01@mint01-desktop ~ $ sudo fdisk -lu

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000837d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    56123391    28060672   83  Linux
/dev/sda2        56125438    58632191     1253377    5  Extended
/dev/sda5        56125440    58632191     1253376   82  Linux swap / Solaris
mint01@mint01-desktop ~ $ 


:popcorn:

---

### Post by Rubi1200 on 2011-01-28
Thanks for posting the output.

How much space do you want to allocate to Windows?

Your drive only has 30GB.

How much free space is left on sda1?

This command will tell us:

```
df -Th
```

---

### Post by soryu on 2011-01-28
i'm thinking about 3gb.

/ "I don't mean to be rude - but what are \
| you saying?"                            |
|                                         |
\ Husse Oct 1 2007                        /
 -----------------------------------------
  \
   \
       ___  
     {~._.~}
      ( Y )
     ()~*~()   
     (_)-(_)   
mint01@mint01-desktop ~ $ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     27G   20G  5.9G  77% /
none      devtmpfs    369M  236K  368M   1% /dev
none         tmpfs    375M  112K  375M   1% /dev/shm
none         tmpfs    375M   84K  375M   1% /var/run
none         tmpfs    375M     0  375M   0% /var/lock
none         tmpfs    375M     0  375M   0% /lib/init/rw

---

### Post by Rubi1200 on 2011-01-28
To be honest, I don't think that is enough space even for a default XP install.

---

### Post by CharlesA on 2011-01-28
3GB is too little space for XP.

I have an install of XP in a VM and it's currently using 2.79GB on a 8GB drive. You need some free space for the OS to function.

---

### Post by nogoodnamesleft on 2011-01-28
By default a real installation of XP will create a page file ("swap file") equal to 1.5x the amount of installed RAM.

I can confirm that it installs and runs reliably in a 5GB disk partition, on a machine with 1GB of RAM (which means it makes a 1.5GB page file) without needing to adjust page file or registry size (which can grow huge). It could obviously go smaller. That's just the lower boundaries of my testing.

However once you add apps then your mileage may vary. Not all windows apps are clever enough to install all of their components outside of the windows folders so it isn't always possible to put all parts of all apps into a separate partition. Furthermore, they're equally dumb when it comes to uninstallation, and usually leave bits behind somewhere.

---

### Post by soryu on 2011-01-29
ill free up some space and go 6gb.

---

### Post by soryu on 2011-01-29
mint01@mint01-desktop ~ $ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     27G   19G  6.1G  76% /
none      devtmpfs    369M  236K  368M   1% /dev
none         tmpfs    375M  116K  375M   1% /dev/shm
none         tmpfs    375M   84K  375M   1% /var/run
none         tmpfs    375M     0  375M   0% /var/lock

---

### Post by Rubi1200 on 2011-01-29
Even if 6GB is enough, but what will you do with the Ubuntu install? It also needs space for saving documents, updates etc.

If you are able, I would consider one of two things; either buy another hard-drive with more space or buy an external drive/USB stick to use for saving files, pictures etc.

---

### Post by soryu on 2011-01-29
thanks for the info.
i do have an external drive.  i just plan to use  xp i when i can't do some thing in mint.
wont be saving to many things?

---

### Post by Rubi1200 on 2011-01-29
Okay, then there is probably no reason not to do it.

Create the partition for XP, make sure it is a primary partition, install, then reinstall GRUB.

The commands to reinstall GRUB from the LiveCD:

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Run ```
sudo update-grub
``` after rebooting to pick up the Windows install.
This assumes you leave Ubuntu as sda1 and don't move it or anything.

---

### Post by soryu on 2011-01-29
how do i  create the partition and make it primary?

---

### Post by CharlesA on 2011-01-30
> **soryu said:**
> how do i  create the partition and make it primary?
Use gparted to resize the current Ubuntu partition and create a new primary partition. Just make sure to back up your data before doing so.

---

### Post by soryu on 2011-01-30
trying to resize partiion but don't have option.
do i need to unmount?
tried to unmount got a message saying need to unmount manually.
dont know how to.

---

### Post by CharlesA on 2011-01-31
In order to resize partitions, you would need to boot off a livecd and launch gparted. Just be sure you back up any data you want to keep in case something goes wrong.

---

