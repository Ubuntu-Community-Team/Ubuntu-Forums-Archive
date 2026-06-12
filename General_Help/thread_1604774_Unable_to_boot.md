---
title: "Unable to boot"
date: 2010-10-24
forum: General Help
---

### Post by dem0s on 2010-10-24
I am using Ubuntu 10.04 and am having a major issue with it not booting. My PC worked fine yesterday but when I tried to boot this morning I get the error "error: unknown filesystem" and under that I get the "grub rescue>" prompt.

At first I thought this was just a problem with Grub that would be easy fixed so I put in my Ubuntu USB and loaded it up in live mode. But when I try to look at my file system from within the live environment I can't seem to see any of my files.

I have looked at the drive in GParted and my main file system (/dev/sda1) shows up as 'unknown', while the swap partition (/dev/sda5) shows up as it should. I have also looked at the drive with the Disk Utility and the SMART Status says the disk is healthy.

I am really concerned about this as currently the system is totally unable to load, not only that but I am also unable to recover my data from the drive which is my main concern as I havent done a backup for quite some time and I have a lot of python code that I have been working on that I really need to get back.

Has anyone got any idea of what to do and how I might be able to sort this out or at the very least recover all my data. I can't understand why this has happened I have not made any changes to the system recently other than installing the updates that came through yesterday. This is a really urgent issue for me and any help will be very appreciated.

Thank you.

---

### Post by Malac on 2010-10-24
Sounds like it might be the MBR or some sort of filetable corruption.
You could try testdisk it's in the repos.
Load this from your USB Ubuntu boot.
Testdisk can scan your disk and in some cases workout what was on there.

Hope this helps.

---

### Post by kittkatt on 2010-10-24
If you didn't do anything special yet it simply became unrecognisable after a day then it could be a sign of hardware failure.  

Try booting up in live disk, and performing a "check" operation on the boot partition through gparted.

Also run the boot-info script (google) and let us know the results, it would clarify how you've got your drives set up.

---

### Post by dem0s on 2010-10-24
Thanks for your replies. I have checked out the things you suggested. TestDisk looks interesting so I'll have to look at that a little more.

I tried to use the 'check' option of GParted but it is grayed out and I can't seem to figure out how to get that to work. I ran the boot-info script and the results are as follows;

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   613,826,559   613,824,512  83 Linux
/dev/sda2         613,828,606   625,141,759    11,313,154   5 Extended
/dev/sda5         613,828,608   625,141,759    11,313,152  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007624704 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,823,654     7,823,592   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        de855e2b-ed06-414f-9e72-53a3479fe2f6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        121D-704F                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/3Connect          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)

=======Devices which don't seem to have a corresponding hard drive==============

sdc 

The drive I am having problems with is sda, and the partition where all my data is is sda1. I really can't understand why this has happened, it could be a hardware problem but it is only that one partition that seems to have a problem and not the whole drive.

What options do I have to get the system back up and running or at least get some of my data back?

Thanks for your help so far.

---

### Post by dem0s on 2010-10-25
So I am to assume that my Ubuntu is now totally broken and all my data is lost? I really can't understand how this could just happen, even with windows I've never had something like this happen, if my system used to brake I could at least get all my files back. But in this case not only has the system just stopped working but I can't even access the partition from another computer. There must be a way to fix this, I know all the files are there, they have not been over-written, the drive seems to work fine and shows up as healthy. I have used photorec quickly and it recovers the files but without the file-structure or file-names most of them wont be any use to me.

Surely someone knows how to fix this?

---

### Post by mr clark25 on 2010-10-25
> **dem0s said:**
> So I am to assume that my Ubuntu is now totally broken and all my data is lost? I really can't understand how this could just happen, even with windows I've never had something like this happen, if my system used to brake I could at least get all my files back. But in this case not only has the system just stopped working but I can't even access the partition from another computer. There must be a way to fix this, I know all the files are there, they have not been over-written, the drive seems to work fine and shows up as healthy. I have used photorec quickly and it recovers the files but without the file-structure or file-names most of them wont be any use to me.

Surely someone knows how to fix this?

this is where testdisk should help. [this link]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/") should also help.

---

### Post by Malac on 2010-10-25
from your boot-script info it looks like the sda MBR is knackered.
Testdisk should be able to fix this if it is fixable.

Someone please feel free to correct me if I'm wrong here:
If the drive won't hold MBR info as it is too knackered the only other thing would be to dd the whole drive to another unit then run testdisk on that one. It would probably be best if both drives were the same type and size.
**WARNING:**
Quote {"dd copies data byte-exactly, meaning it won&#8217;t get stuck should it encounter corrupted or fragmented data.
dd is nicknamed &#8216;destroy disk&#8217; as mistyping one letter can wipe your hard disk, so caution must be used."}

With the power off first unplug your current /dev/sdb and replace it with a new drive and then
Boot into Live CD and issue this command in a terminal:
```
sudo dd if=/dev/sda of=/dev/sdb
```
When this has finished shutdown the machine.
Move the new disk to /dev/sda position and replace the original /dev/sdb disk.
Boot up to Live CD and try running testdisk on the new /dev/sda

Hope this helps.

---

### Post by dem0s on 2010-10-25
Thanks for everyones help on this. I have tried TestDisk and have read the tutorial that was posted but unfortunately I have so-far been unable to fix the problem. I don't have another drive large enough to copy my drive to so that is not really an option, but thanks for the advice.

I have now decided that I am willing to lose most of my data such as mp3's and movies.

Thanks for the link to TestDisk there is another program that comes with it called PhotoRec that has allowed me to get all my .py code back which has lessened the pain.

Now I just have two files that I really can't afford to lose, both are MySQL dumps with the .sql extension. I am trying to get them back with PhotoRec 6.12 that the release notes state has support for this file type. The problem is that I can't seem to find the option to recover that specific file type. Any advice on this would be great

Thanks again for all of your help.

---

