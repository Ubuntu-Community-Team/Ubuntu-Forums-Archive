---
title: "Partition Recovery"
date: 2011-01-03
forum: General Help
---

### Post by DManX04 on 2011-01-03
I had my Windows partition disappear a few months ago, and at the time some posters here had me post a boot info script and felt that it was gone. I was pretty busy and decided not to worry about it right away, but today I tried to recover using testdisk, and everything was there. Is there anyway to just restore the partition, or am I going to have to backup from testdisk and then reformat and reinstall Windows?

---

### Post by DManX04 on 2011-01-04
So I got impatient, and I'm not sure if I'm better or worse for it.

I went ahead with the testdisk recovery. It recognized a swap, a linux partition, a windows partition, the mediadirect partition, and an extended partition. I wrote the new partition table. Now when I boot, it says "Error: no partition" and goes to the Grub Rescue prompt.

I've booted to a LiveCD and now the Windows partition can mount and shows everything there, the mediadirect partiton can mount, but the Ubuntu partition will not mount. The error box says: 

"Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Any ideas what I should do next? Much thanks for any help.

---

### Post by rpaskudniak on 2011-01-04
You DMan, and I feel your pain, having posted similarly anguished cries for help more than once in these forums.

First: Since you can boot something, download the System Rescue CD from [here]("http://www.sysresccd.org/Main_Page").  Burn this to a cd and then boot from that CD.

You will have to answer a few simple prompts but it can fix your partition table once it's live.  It fixed my Windows partition merely by trying to poke around and mount it, without my having to deliberately tell it to fix anything.

I can't guarantee your results but it's worth a try.

Another option is to search for recent posts with the word Partition in the subject.  You will surely find a similar post because it happens to many people who get too clever (as I did) with their partition tables.  At lease one will have advice to boot the Ubuntu Live CD and run grub commands from there.

Sorry I can't be more specific right now.

Good luck!

---

### Post by DManX04 on 2011-01-04
Thanks for the advice. I don't have any way to burn a CD right now, but I'm trying to find one.

Anyone else have any suggestions?

---

### Post by DManX04 on 2011-01-04
Sorry to keep bumping this, but I'm really trying to avoid reformatting and then reinstalling windows and ubuntu.

---

### Post by dino99 on 2011-01-04
use these tools:

[http://www.cgsecurity.org/wiki/Main_Page](http://www.cgsecurity.org/wiki/Main_Page)

---

### Post by searchfgold6789 on 2011-01-04
This problem is easy to solve using testdisk, and you're halfway there. Fixboot and fixmbr from the windows CD, or bootrec if you're a Windows 7/Vista, and then install GRUB again using a Live CD. I did exactly the same thing on my friend's computer with the same problem and it worked. However you might want to try to force mount and check the data on the Ubuntu partition first.
Do not try to recover the data again because it is probably not as trustworthy, since the partitions might have overwitten parts of it.
I wish you luck with this issue.

---

### Post by oldfred on 2011-01-04
You should run chkdsk on all NTFS partitions with a windows repair CD.

And you should run e2fsck on all ext type partitions.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by DManX04 on 2011-01-04
Thanks for all the advice, guys. So far, I haven't really been able to get any of this stuff to work though. Maybe if explain the history of the problem a little more it will help.

I have a 160GB HD on a Dell Inspiron 1720 that originally came with Windows Vista. I partitioned it to install Ubuntu a few years ago (I think 8.10 was the first version I put on), and except for a clean install of 10.04 it's been fine. Back in September - after installing 10.04 but before upgrading to 10.10 - my Windows partition stopped coming up in Grub and I couldnt' mount it. Disk analyser showed the space as unallocated. I posted the boot info script on here, and everyone said it looked like the data was gone. 

That brings us to the present. I went ahead and tried testdisk. It showed everything as still there, so I wrote the new boot record. Then nothing came up. I've still got the boot info script and the testdisk log. Also, fdisk -l shows the original partition structure, but the Ubuntu partition won't mount. When I attempted to use my Dell Windows re-installation CD, it recognised five partitions, but said there was no space on the Ubuntu partition. Also, when I go to system repair and it asks me to select an operating system, it shows no operating systems. The partition manager on the LiveCD showed the entire HD as unallocated.

I'm really lost here. How do I use the bootrec for Windows? Is there anything else I should be doing from the Ubuntu side of this? What else do you guys need to know about the system and what's been going on?

---

### Post by DManX04 on 2011-01-04
Bump.

---

### Post by oldfred on 2011-01-04
Post boot info script. Be sure to run a new copy with whatever changes you have done so far.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Windows will not see Linux partitions, so that is normal. Use windows tools on windows, and Linux tools on windows, but sometimes it is better to use Linux tools to fix windows.

---

### Post by DManX04 on 2011-01-04
Here's the boot script. Also, I tried to use the Windows recovery tools in bootrec.exe, but nothing worked. Here's what I got, in case it might help.

1) FixMbr said it was successful
2) FixBoot said that the volume had no recognized file system
3) ScanOs said it identified 1 Windows installation
4) RebuildBCD said both that it identified 1 Windows installation and that the volume had no recognized file system

```
       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: Stale NFS file handle

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     4,321,484     4,321,422  82 Linux swap / Solaris
/dev/sda2           4,321,485    62,910,539    58,589,055  83 Linux
/dev/sda3          62,910,540   306,279,224   243,368,685   7 HPFS/NTFS
/dev/sda4         306,279,225   312,592,769     6,313,545   f W95 Ext d (LBA)
/dev/sda5         306,279,288   312,576,704     6,297,417   c W95 FAT32 (LBA)

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4103 MB, 4103937024 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8015502 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  34     7,984,304     7,984,271   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        686fc6a5-4234-4a18-a9cb-ee28b3dbaefd   swap                                     
/dev/sda2        d28eb7a5-3bc5-499d-b234-99837f6e16ba   ext2                                     
/dev/sda3        D4F24E0FF24DF670                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        07D9-0916                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1007-A232                              vfat       ¿-7&#132;5YÉ]§ÿ                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by oldfred on 2011-01-04
Linux does not use the boot flag but windows has to have it to know what partition to boot. Move the boot flag to sda3 with gparted or command line. there also is a makeactive command in the windows repair but I do not know exact syntax.

Then rerun the fixBoot commands, you are missing the BCD. This is what you should have:
  Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If more info needed:
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by DManX04 on 2011-01-04
Thanks a lot for all your help. Do you think you could explain how to move the boot flag? I'm not really sure how to do that with gparted or the command line.

---

### Post by oldfred on 2011-01-05
With gparted, you click on the partition then click (or right click?) on manage flags, boot flag is one of the options. Be sure not to have more than one boot flag per drive. And boot flags must only be on primary partitions (for windows, lilo does not care).

set boot flag on for sda3 (off on others), from command line
sudo sfdisk -A3 /dev/sda

---

### Post by DManX04 on 2011-01-05
Thanks for all your help. Unfortunately, this didn't seem to work either. I continue to get the same messages that an installation of Windows has been found, but that there is no recognized file system on the volume. I think at this point I'm just going to do a clean install of Windows and Ubuntu. I'd keep going, but I've got to have Windows funtional in a few days so I can download some exam software.

Thanks, though, for all your time and effort. It's been much appreciated.

---

