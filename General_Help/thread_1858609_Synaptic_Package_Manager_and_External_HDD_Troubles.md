---
title: "Synaptic Package Manager and External HDD Troubles"
date: 2011-10-12
forum: General Help
---

### Post by jjbernacki on 2011-10-12
Greetings,

I'm a Ubuntu newbie, running 9.10 - the Karmic Koala.  I have a problem, and will be succinct.

- Wanted to upgrade to 11.04
- Needed to backup data on external Ultra HDD
- Not enough space on drive, began deleting old content.
- Eventually decided to format.  Formatted external HDD
- External HDD no longer automatically detects.
- Attempt to mount using [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) manual directions.  

[B]sudo fdisk -l
sudo mkdir /media/external
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
[/B]
- Attempts failed with following error

[B]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

- Re-run    sudo fdisk -l [FONT=monospace]with following results.  Realize it is an NTFS HDD

[/FONT][B]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9358    75168103+  83  Linux
/dev/sda2            9359        9729     2980057+   5  Extended
/dev/sda5            9359        9729     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 82.0 GB, 81964301824 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e5a331

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS
bernacki@bernacki-laptop:~$ 
[/B]
- Attempt to mount using NTFS directions on same page  [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB).  Following message appears

[B]bernacki@bernacki-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
bernacki@bernacki-laptop:~$ [/B]

- Attempt to download ntfs-3g driver as indicatedhere, [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions), as a troubleshooting solution   using   sudo apt-get install ntfs-config
- Following error appears

[B](Reading database ... 10%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer0.10-plugins-bad-multiverse' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/B]
- Run terminal instruction for same process on same page.  Read out as such.

[B]bernacki@bernacki-laptop:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  menu
The following NEW packages will be installed:
  menu ntfs-config
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/480kB of archives.
After this operation, 2,429kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package menu.
(Reading database ... 10%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer0.10-plugins-bad-multiverse' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
bernacki@bernacki-laptop:~$ [/B]


I've attempted many many solutions as listed on various ubuntu manuals and forums.  Am out of ideas.  Want my HDD back so I can back up my stuff, so I can get new Ubuntu.  Would rather not have to back up on DVD.

Please help, any advise is greatly appreciated.

Thanks in advance

Jack

---

### Post by cryptotheslow on 2011-10-12
What did you use to format the external drive to NTFS? It sounds like it didn't make a particularly good job of it.

If you are simply using it to backup files for safe keeping while you upgrade / clean install a new Ubuntu version, then you could format it to a natively supported filesystem such as ext3 or ext4 which would avoid any "potential" problems with NTFS support. Personally I'd use GParted to do this - plenty of other choices of course.

---

### Post by jjbernacki on 2011-10-12
Used right click, format, to format external drive.  Attempt to get GParted from Synaptic results in partial installation and following error

[B]Selecting previously deselected program libdmraid 1.0.0.rc15
(Reading database ... 10%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer0.10-plugins-bad-multiverse' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

Ideas?

Jack

---

### Post by cryptotheslow on 2011-10-12
Isn't GParted installed by default on 9.10? Been a while since I moved on from it so can't rightly remember.

If not do you have "Partition Manager" on the Administration menu? That does essentially the same job as GParted. Alternatively use the same "right-click" method to re-format to ext3 (I don't think ext4 made it into 9.10).

That error message you are getting from dpkg indicates there is corruption in the package database or sources list. It's fixable, but if you are reinstalling imminently it's probably not worth fixing unless necessary to get your files backed up.

---

### Post by cryptotheslow on 2011-10-12
Just a quick aside. You may want to consider waiting for the 11.10 release that is due imminently to benefit from a slightly longer support cycle.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Both 10.04.3 LTS and 11.10 will be supported until April 2013 (11.04 only until October 2012). Just gives an extra six months before having to upgrade to keep receiving security updates.

---

### Post by jjbernacki on 2011-10-12
Thanks for the advice on the new release.  I will do it anyways, as I am having ongoing problems I want to be done with.

As to the Partition managers, no GParted, and no Partition Manager.  Nothing that even looks like one.  I don't think I can even to the right click format, as the external drive icon has disappeared, and I can't locate the drive anywhere.  And I am having no luck remounting.  

The question remains, how do I reformat an invisible/unmounted drive, or how do I mount this stupid drive?  It seems to me Synaptic Package Manger not working is my major problem, as it is preventing me from installing the things I need to do either.

Ideas?  Or am I stuck with a busted 80 gig drive?

Jack

---

### Post by cryptotheslow on 2011-10-12
No you are not stuck. Just a little hurdle in the way :D

I think the way forward is to use parted from the command line.

Have a read of this before going any further:
[http://manpages.ubuntu.com/manpages/natty/man8/parted.8.html](http://manpages.ubuntu.com/manpages/natty/man8/parted.8.html)

Do you happen to know the block device of the external drive? e.g. /dev/sbd or /dev/sbc

Be very wary of wading into using parted until you are familiar with its options and are **sure** of what block device relates to your external drive.

This command entered in a Terminal will list all partitions on all block devices:
```
sudo parted -l
```

That is a lowercase letter L as an option. But read the man page first before diving in and ask if you are unsire about anything.

Post back the output of that command between code tags.

---

### Post by jjbernacki on 2011-10-12
Problem Solved

Like a total noob I didn't even notice the "Disk Utility" in the Admin menu.  The external was there, I set up the file system and it is up and running.  My system is backed up, and I am ready to install the latest Ubuntu.

Thanks for everything.  

Jack(***)

---

### Post by cryptotheslow on 2011-10-12
:D Good stuff! I really should get round to setting up some alternative versions in virtual boxes so I can use the relevant terminology for each!

Glad you got it sorted and good luck with the new install. Have a forum search for "oldfred's list of things to backup" for ideas on other application settings etc. you might want to consider saving before blitzing your drive.

And use the Thread Tools at the top to mark the thread as solved.

---

