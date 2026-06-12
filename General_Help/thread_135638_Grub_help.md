---
title: "Grub help"
date: 2006-02-24
forum: General Help
---

### Post by lgmdaniel on 2006-02-24
I moved my Ubuntu partition to the beging of a disk so thats my disk layout looked like this:
[FONT="Courier New"]
[B]Disk 1: <ubuntupartitiion><RiseFSdatapartition><swap>
Disk 2: <XPpartition><fat32datapartition>[/B][/FONT]

Original layout.
[B]
[FONT="Courier New"]Disk1: <oldXPpartion><ext3><ubuntupartition><swap>
Disk2: <newXPpartition><fat32datapartition>[/B][/FONT]

The ubuntu was fine as was the xp, though I did have to reinstall grub with the ubuntu disk. But both OS's showed up, so I booted in to ubuntu to be sure it worked then shutdown. But it seems after rebooting in to Ubuntu the XP boot option has vanished and I can't seem to get it to boot no matter what I put in 
'/boot/grub/menu.lst' file.
Can someone give the correct details?

This is my partition information and minor details.
```
daniel@grinch:~$ sudo parted /dev/hda print
Disk geometry for /dev/hda: 0.000-78167.250 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
3          0.000  14668.725  primary   ext3        boot
1      14668.786  78166.757  extended              lba
6      14668.787  71892.443  logical   reiserfs
5      77143.039  78166.757  logical   linux-swap
Information: Don't forget to update /etc/fstab, if necessary.

daniel@grinch:~$ sudo parted /dev/hdb print
Disk geometry for /dev/hdb: 0.000-58644.140 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  20042.028  primary   fat32       boot, lba
2      20042.029  58643.525  extended              lba
5      20042.060  58643.525  logical   fat32
Information: Don't forget to update /etc/fstab, if necessary.

```

And this is my menu.list

```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-k7
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

This is also my disk details:
```
daniel@grinch:~$ lshw -C disk
WARNING: you should run this program as super-user.
  *-disk:0
       product: Maxtor 6Y080P0
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       capacity: 76GB
  *-disk:1
       product: IC35L060AVVA07-0
       vendor: Hitachi
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       capacity: 57GB
  *-cdrom
       product: TOSHIBA DVD-ROM SD-R1002
       vendor: Toshiba
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       capabilities: packet

```

---

### Post by shams2 on 2006-02-24
try this one for xp:
title           Windows NT/2000/XP (loader)
root            (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader     +1

---

### Post by lgmdaniel on 2006-02-24
Thanks, that works and it apears to boot of the disk. Though now I get a invalid system disk error, so I guess I've stuffed the windows MBR. Would using the recovery console be my best choice?

---

### Post by lgmdaniel on 2006-02-25
bump anyone?

---

### Post by lgmdaniel on 2006-02-27
Hello?

---

### Post by lgmdaniel on 2006-02-28
looks like I'll have to break it myself...

---

### Post by Sutekh on 2006-02-28
If you think you've killed the MBR, boot up a WinXP install CD and get into the recovery console ('R') and use the command fixmbr

This link has more info [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx")

Once Windows is up, then you can try re-install GRUB.  Although I didn't understand your re-partitioning.  Did you change anything on the second hard disc (hdb)?

---

### Post by lgmdaniel on 2006-03-01
[QUOTE=Sutekh]If you think you've killed the MBR, boot up a WinXP install CD and get into the recovery console ('R') and use the command fixmbr

This link has more info [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx")

Once Windows is up, then you can try re-install GRUB.  Although I didn't understand your re-partitioning.  Did you change anything on the second hard disc (hdb)?[/QUOTE]

Nope nothing was touched.. just the first disk.

---

### Post by Rog131 on 2006-03-02
Have you tried this ?

Restore Grub
From Ubuntu Document Storage Facility

HOWTO: Restore GRUB (if your MBR is messed up)

Restoring GRUB (the GRand Unified Bootloader) is quite simple in Ubuntu; instead of going through all of the "gain root access" steps, and playing with confusing shell commands, you can simply use the Ubuntu installation CD to restore it without going through all of the previous hassles. 

More:
[http://doc.gwos.org/index.php?title=Restore_Grub](http://doc.gwos.org/index.php?title=Restore_Grub)

---

### Post by R3linquish3r on 2006-03-03
Becaureful using Rog131's way though. You need to go through all the menu's in order as if you were re-formatting and re-installing ubuntu. When you get to the partition table MANUALLY EDIT it and make sure you open your Root (and home or any others you have) and SWAP and make sure it says NOT to reformat. Then continue, it wont show any drives that will be changed and you will get some errors but you will finally get to the boot loader.

---

