---
title: "Endless boot cycle with xp in grub2"
date: 2010-03-23
forum: General Help
---

### Post by donc786 on 2010-03-23
I have recently been unable to boot into windows xp, which is on a drive separate from my linux installation.  When I select the windows installation, the computer starts back at the bios screen and returns to grub endlessly.  I am running an updated 9.10.  The linux will boot fine; however the most recent kernel does not show up on the list of available options, which may indicate something.  I have searched the forum and found nothing that helps.  There are plenty of posts asking if you have stopped using windows altogether and other non tech related posts though.  The results of sudo fdisk -l are below.  I'm sure the answer is right in front of me.  I just don't know enough to realise it.  All assistance is appreciated.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef73ade4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         461     3702951    b  W95 FAT32
/dev/sda2   *         462        9728    74437177+   7  HPFS/NTFS

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1082da5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9553    76734441   83  Linux
/dev/sdb2            9554        9964     3301357+   5  Extended
/dev/sdb5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31d65645

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       13971   112222026    7  HPFS/NTFS
/dev/sdc2           13972       14530     4490167+  83  Linux
/dev/sdc3           14531       14593      506047+   5  Extended
/dev/sdc5           14531       14593      506016   82  Linux swap / Solaris

sda contains the windows partitions.  There is also more info concerning the boot info available [URL="http://ddizzle.webs.com/linux.htm"]http://ddizzle.webs.com/linux.htm
[/URL]

---

### Post by prodigy_ on 2010-03-23
I haven't read the full output of bootinfo yet, but you seem to have Grub2 installed on /dev/sda MBR (80GB HDD with Windows partitions) and classic Grub on /dev/sdb MBR (80GB HDD with Linux partitions). Therefore a question: from which of those **physical** drives are you trying to boot? If you're unsure you can check this in BIOS.

[Edit]: I suppose you need to boot from /dev/sdb. This is where old Grub is installed (and in its menu.lst the newer kernel is listed).

---

### Post by donc786 on 2010-03-24
> **prodigy_ said:**
> I haven't read the full output of bootinfo yet, but you seem to have Grub2 installed on /dev/sda MBR (80GB HDD with Windows partitions) and classic Grub on /dev/sdb MBR (80GB HDD with Linux partitions). Therefore a question: from which of those **physical** drives are you trying to boot? If you're unsure you can check this in BIOS.

[Edit]: I suppose you need to boot from /dev/sdb. This is where old Grub is installed (and in its menu.lst the newer kernel is listed).



The bios starts with the drive windows is on.  The other 80 gb drive has had ubuntu on it for about a year.  The 115gb drive is used as a backup drive and also has xubuntu installed on it.  It is connected via usb and is not listed in the bios boot list.  I have tried booting without the 115gb drive connected, but it doesn't seem to make a difference.  I have also tried restoring the windows from a drive image I created as a back up thinking a boot.ini file had a problem.
  I changed the boot order, and the linux boots up and skips the grub list.  When I boot from the drive with windows, the grub list is displayed.

Thanks for your help.

---

### Post by oldfred on 2010-03-24
So  we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.


Did you by any chance install grub to the windows partition?

---

### Post by |{urse on 2010-03-24
boot to your xp disk (cd), select 'r' for repair console. type FIXBOOT at prompt.

---

### Post by donc786 on 2010-03-24
> **oldfred said:**
> So  we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.


Did you by any chance install grub to the windows partition?

The boot info is listed if you follow the link in my original post.  I didn't include it in the post to keep it from taking up a lot of space.  I'm not sure if the grub is on the windows drive.  When I originally installed Ubuntu, I had no experience with Linux.  I could have installed it in some strange manner.  I tried to keep the windows drive unchanged as much as possible.  The linux was on the drive that I believe is listed as sdb.  When I try to boot with the windows drive alone, I get an error message.  SDA and sdb have to be connected together to get grub to come up, and boot linux.

Thanks for your help.  I really need my windows for my autocad class.
Thanks,
Don

---

### Post by donc786 on 2010-03-24
> **|{urse said:**
> boot to your xp disk (cd), select 'r' for repair console. type FIXBOOT at prompt.

I just tried the fixboot command.  Everything seemed to install fine.  The boot problem still persists though.  Maybe I did something weird to my grub config.  Is there a file I could post that would show my grub config?

---

### Post by oldfred on 2010-03-24
Your sda2 has the boot flag so it should be the main winXP. The sda2 partition does not have a ntdect.com file that sda1 does have. You may have to do the full XP repair.

It also looks like the UUID's are reversed?
/dev/sda1        423B-2BDF                          vfat                                    
/dev/sda2        B0DC5F47DC5F06CE                       ntfs  

but your boot from the grub2 entry is 
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 423b-2bdf

You also have installed grub to a lot of partition boot sectors. It does not add anything nor cause problems unless you overwrite the windows partition boot. But should not be in all those partitions, except the one you were  chainbooting.

---

