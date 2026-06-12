---
title: "Recent daily update broke acpi-related things"
date: 2012-03-08
forum: General Help
---

### Post by MorrisseyJ on 2012-03-08
One of my most recent updates broke a number of things, most of which appear to acpi related.

1. Brightness controls no longer work (fn+F8 and fn+F9)
2. Only skip forward (for a media player) works (fn+F12), skip backwards (fn+F10) no longer does 
3. Suspend on lid-close appears to have stopped working - the box is checked in my power preferences
4. Fan appears to have stopped working - this is a rather urgent problem given that i'm in 35 deg heat with 90% humidity...

I am using the Gnome 3 desktop and running 11.10 on a thinkpadx121e.

I have tried installing tpb, but to no avail.

Does anyone know how i go about finding out what's causing the problem, or how i can fix it?

Thanks,

j

---

### Post by MorrisseyJ on 2012-03-09
Still no luck on this however after sifting through some more google searches on acpi-related problems for ubuntu, i saw references to kernel panic. 

This reminded me that i had seen the creation of a paniclog file in my home folder. So maybe it wasn't the update that did it.

In case this is useful for anyone who thinks they can help resolve my problem, the contents of the file are:
> 0.0.7E7F3 20120303: impossible Read from proxy interface failed

Do let me know if anyone has any thoughts.

Thanks,

j

---

### Post by MorrisseyJ on 2012-03-11
And today everything decided to work. I haven't done anything, the only change is that i am now in an air-conditioned room, so the temperature is back down.

Is it possible that the temperature could have messed up these acpi things? Its a bit frustrating if hot weather breaks the fan...

---

### Post by MorrisseyJ on 2012-04-26
This played up again so eventually i took it back to the shop under warranty. 

There they cleaned the heat sync, and replaced the fan and keyboard.

Everything is working fine now.

---

### Post by treblekicking on 2012-07-16
I had these exact same symptoms two months ago (although it didn't seem to be related to updating but rather to closing the lid and unplugging the power cable simultaneously).  I couldn't find a solution and ended up sending it to Lenovo for repair.  It came back with a BIOS update from 1.12 to 1.15 and Windows installed.  The problem just occurred again (again it was some combination of closing the lid and unplugging the power cable) but this time instead of dealing with Lenovo and Windows I updated the BIOS from 1.15 to 1.16 and this immediately solved the problem.

Since this occurred with BIOS versions 1.12 and 1.15 I suspect the problem could be solved by simply re-flashing the same BIOS over itself if one needed to (although I haven't tried that).

Lenovo only releases an ISO and a .exe for the BIOS so make a bootable USB key.  That can be done using grub4dos: [http://www.thinkwiki.org/wiki/BIOS_Upgrade#Using_grub4dos_.28also_for_Linux.29](http://www.thinkwiki.org/wiki/BIOS_Upgrade#Using_grub4dos_.28also_for_Linux.29)

---

### Post by MorrisseyJ on 2012-07-17
Hi treblekicking, 

Thanks for the info. I have had the exact same problem recur after Lenovo did all the things you described - other than reinstalling windows as i was dual booting. 

I have now tried updating the BIOS from 1.15 to 1.16, from within Windows using the Lenovo utility. Unfortunately it doesn't seem to be working. After i follow the instructions , i check my system information to find that i am still on BIOS version 1.15.

So i am now trying your grub4dos solution (it would also be good to be able to do this without windows), but i am having a problem:

With my formated flash drive inserted,> sudo fdisk -l gives:

 ```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2         2459648   109043711    53292032    7  HPFS/NTFS/exFAT
/dev/sda3       109045758   625141759   258048001    5  Extended
/dev/sda5       109045760   608542719   249748480   83  Linux
/dev/sda6       608544768   625141759     8298496   82  Linux swap / Solaris

Disk /dev/sdc: 4011 MB, 4011851776 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7835648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004629e

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     7834071     3917005    c  W95 FAT32 (LBA)
```Trying to create grub4dos boot sector in MBR of the flash drive,> ~/grub4dos-0.4.4$sudo ./[bootlace.com]("http://bootlace.com") /dev/sdc1 gives the error:

 ```
Error: Invalid partition table. Must specify --floppy explicitly for floppy.
 BOOTLACE writes GRLDR BOOT RECORD to MBR or to the boot area of a file system.
 Usage:  [bootlace.com]("http://bootlace.com")  [OPTIONS]  DEVICE_OR_FILE
 Options: --read-only, --floppy[=N], --boot-prevmbr-first, --boot-prevmbr-last,
 --no-backup-mbr, --force-backup-mbr, --mbr-enable-floppy, --mbr-disable-floppy,
 --mbr-enable-osbr, --mbr-disable-osbr, --duce, --time-out=T, --hot-key=K,
 --preferred-drive=D, --preferred-partition=P, --sectors-per-track=S, --heads=H,
 --start-sector=B, --total-sectors=C, --install-partition=I, --lba, --chs,
 --fat12, --fat16, --fat32, --vfat, --ntfs, --ext2, --serial-number=SN,
 --restore-mbr, --mbr-no-bpb, --chs-no-tune
 DEVICE_OR_FILE: Filename of the device or image. For DOS, a BIOS drive number
 (in hex 0xHH or decimal DDD format)can be used to access the drive.
```GParted shows no partitions on the pen drive. 

If you know what i'm doing wrong it'd be great if you could let me know. 

Thanks, 

j

---

### Post by treblekicking on 2012-07-18
Perhaps if the drive is not partitioned you need to send it to the MBR of the USB key without specifying the partition number:

Try:

> ~/grub4dos-0.4.4$sudo ./bootlace.com /dev/sdc

---

### Post by MorrisseyJ on 2012-07-18
Thanks for getting back to me. 

That seemed to work. 

> ~/grub4dos-0.4.4$ sudo ./bootlace.com /dev/sdcGave:
```
Disk geometry calculated according to the partition table:

        Sectors per track = 62, Number of heads = 124

Success.
```However the USB drive just looks blank  i.e. there is no evident directory structure on it.  So where do i > Copy the files grldr and menu.lst to the root directory of your pendrive.? Do i simply stick them on the pendrive, or has something gone wrong and i am meant to be seeing some file structure?

Thanks for your help.

---

### Post by treblekicking on 2012-07-18
I just put them on the pen drive.

---

### Post by MorrisseyJ on 2012-07-18
Sorry,  just to be sure. You had something like the attached (also no hidden folders)?

---

### Post by treblekicking on 2012-07-18
I don't remember, but there is little risk in trying it as it is.  The worst case scenario is that the pendrive is not bootable, in which case it will tell you so.  If it is bootable then you will see the menu file you just edited and you will be able to choose to run the BIOS update iso file that you copied to the disk (the last menu selection).

---

### Post by MorrisseyJ on 2012-07-28
Hi, 

So i got this working.

From post #10 it seemed that all i had to do was drag the files onto the flash disk. As treblekicking pointed out, if you boot to the USB then you'll see the amendments you made to the file in the menu list. 

Since having done all this however, i lost my nerve, worried that i'd flash the BIOS and break my machine. 

After complaining to Lenovo about the lack of support for making a bootable flashdisk to update the BIOS, especially since the windows .exe file was not working on my windows partition, they have decided to give me a new machine. 

Sorry i didn't get to confirm this. If anyone else finds that updating the BIOS solves the problems described at the top of this thread i am sure that other people with an x121e and experiencing the same problems would appreciate the info. 

Thanks also to treblekicking, for looking into this.

j

---

