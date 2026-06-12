---
title: "suddenly lost ntfs partition"
date: 2006-05-11
forum: General Help
---

### Post by tehscott on 2006-05-11
earlier today i used the rescue option when booting ubuntu in order to repair my grub file.  i tried this a few times before with no luck (i've done this many times because i've reinstalled windows more than once), but it worked this time.  after rebooting i tried to re-enter windows and couldn't.  it appears that my c drive (part of a partitioned drive) is no longer in the ntfs format.  if i do dmesg | tail it confirms that linux doesn't see that partition as ntfs, although fstab says it's still ntfs (which may not matter, i don't really know.)  i'm unable to mount the drive because of this.

this wouldn't be such a big deal if i didn't have lots to lose on that drive.

i hope i've been clear enough..if not i'm sorry.

some additional information:

i'm using the lastest distro of ubuntu on an 80gb, partitioned drive. i have 2 ntfs (maybe one now.. :() partitions, one of which still works fine, with windows xp pro sp2 on the c drive (the drive that doesn't work).  a third partition which is for linux (and the swap partition, of course).

i'm starting to think i've lost the partition :( thanks for any help you can give!

---

### Post by tehscott on 2006-05-11
oh yes, here's this:

skoobz@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/hda1 /media/hda1 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hda5 /media/hda5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 ntfs ro,user,fmask=0111,dmask=0000 0 0

and

skoobz@ubuntu:~$ dmesg | tail
NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume

and grub (the relevant part at least)

title		Ubuntu, kernel 2.6.10-6-386 
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.10-6-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.10-6-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,6)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by jtibau on 2006-05-11
ok for starters, fstab is supposed to be user generated, when you do partitioning while installing Linux, you do two things: Partition and format your drives of course, and help your OS know what to do with your partitions (build fstab from a GUI usually).
So, what I can get from fstab is that you used to have a NTFS formated partition in /dev/hda1 which you later point out that used to have a working WXP.
Thus, answering your doubt, it really doesn't matter what fstab says now.
What you can do is type "sudo cfdisk /dev/hda" that should show you what partitions do exist in your hda drive.
My guess is it got formatted somehow. I've done it unintencionally a couple of times :(
Best of lucks

---

### Post by tehscott on 2006-05-11
this is what i get from cfdisk:

cfdisk 2.12p

                              Disk Drive: /dev/hda
                        Size: 80026361856 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9729

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1        Boot        Primary   NTFS             []              29364.25
    hda5                    Logical   NTFS             []              41940.71
    hda6                    Logical   Linux swap / Solaris              1077.52
    hda7        Boot        Logical   Linux ext3       [/]              7641

hda1 is NTFS here...how odd.  what do you think?

i was thinking i might be able to install windows on hda5, which works at the moment, and possibly recover data from hda1 that way.  i just need a blasted windows disc that actually works...

---

### Post by RavenOfOdin on 2006-05-11
Have you tried BartPE?

If this happens to you again, that might help solve a few problems.

---

### Post by tehscott on 2006-05-11
ok, i'm fairly certain i know what happened.  i think i accidentally installed grub on the wrong partition (had1) and that messed up the MBR.  i looked around and it seems like i should be able to boot from my winxp disc and do a repair on the mbr.  the only problem is that both of my windows discs don't appear to like my computer and neither will boot :(

i'd download a new install disc, but my new ISP doesn't like torrents for some reason and they limit the bandwidth..or something.. 10mb up and down and i still get 5k/s on a torrent with 2000 seeds... :(

---

### Post by jtibau on 2006-05-11
You can try using the Knoppix live cd, it's supposed to be the best linux distro for recovering data.
I think you can reinstall grub with it, I don't really know howto though. That should get  your second winXP installation to work. Maybe it will be able to read the NTFS partition.

---

### Post by tehscott on 2006-05-11
well, it appears that in trying to fix my computer i screwed it up beyond repair.  i tried something that i didn't know much about and now it seems that i've messed up the partition table..so i think i've given up on fixing it.  i'm fairly certain all is lost, but if i can manage to install linux on a seperate harddrive i'll see if i can recover my data. thanks for your help..

remind me to not fix things by myself any more..that never seems to work..

---

### Post by jtibau on 2006-05-11
Well it sucks that you lost your stuff. However you should try to learn from the experience. Don't give up...

---

### Post by MJN on 2006-05-12
As jtibau says, breaking things is all part of the learning experience. Indeed I think it's safe to say I've learnt far more from breaking things than doing things right first time.
 
Rather than installing Linux on another HDD, just download yourself a LiveCD - Knoppix (as mentioned), (K)Ubuntu or even [www.sysresccd.org]("http://www.sysresccd.org") (only 120MB).
 
If your ISP doesn't support/endorse torrents then just download it over http - on a 10Mb connection it'll be done in no time!
 
Then, with the LiveCD of your choice, boot it and see if whatever GUI you get automatically mounts your NTFS partition (as read only most likely). If so, great - capture the data you need, if not then post back and we can look at mounting it manually.
 
Even if you've written off getting your data back you may as well attempt to get it back - if nothing else you'll learn how to do it for the time when it *really *matters that you get the stuff back!
 
Mathew

---

