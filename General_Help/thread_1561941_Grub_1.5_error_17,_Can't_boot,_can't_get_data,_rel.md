---
title: "Grub 1.5 error 17, Can't boot, can't get data, reluctant to re-install"
date: 2010-08-26
forum: General Help
---

### Post by dcsii on 2010-08-26
Well about a week ago my computer acted a bit funny and upon attempting a reboot I hit grub error 17, and really haven't been able to make it past it. The posts I find, haven't been that helpful, and all I want is to to get at my harddrive that had my original OS on it and get some files off and backed up at least.

Backing up, I've only used a single OS of Hardy Heron. I don't understand why I'm being affected by this error when all I have is two harddrives that are used as unbroken partitions. Best advice I've used is to use a live disk, however the one I've currently got is for Lucid Lynx. I'm not sure whether I need to go and get the old version of a live disc since all I want are my files, I'm content to update to the newer version (though part of me wants to wait for the next one since it's only a few weeks away.) If I could get my system running as it was that'd be great too.

I believe the harddrives are fine since both are recognized in bios, just when running the live disk it asks if it wanted to install it or try it first. When running in the trial of Lucid, I can see the second harddrive and access files as I could on Hardy, but I can't see the main one. 

I really don't know what to do and am considering just starting over and cursing the loss of the data I want to preserve.

---

### Post by oldfred on 2010-08-27
From the liveCD you can run this that will tell us all about your system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by dcsii on 2010-08-27
I don't understand but some of what I see I find troubling, especially input/output errors and that it doesn't seem to see any kind of boot OS by what I see. I could be mistaken though since it is a bit over my head

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,576,704   312,576,642   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sdb1     ?             0            -1                   Unknown
/dev/sdb2     ?             0            -1                   Unknown
/dev/sdb3     ?             0            -1                   Unknown
/dev/sdb4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A75-22FF                              vfat                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb3: No such file or directory
error: /dev/sdb4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: hpt37x: reading /dev/sdb[Input/output error]
ERROR: hpt45x: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: jmicron: reading /dev/sdb[Input/output error]
ERROR: lsi: reading /dev/sdb[Input/output error]
ERROR: nvidia: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: sil: reading /dev/sdb[Input/output error]
ERROR: via: reading /dev/sdb[Input/output error]
ERROR: asr: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: ddf1: reading /dev/sdb[Input/output error]
ERROR: hpt37x: reading /dev/sdb[Input/output error]
ERROR: hpt45x: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: isw: reading /dev/sdb[Input/output error]
ERROR: jmicron: reading /dev/sdb[Input/output error]
ERROR: lsi: reading /dev/sdb[Input/output error]
ERROR: nvidia: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: pdc: reading /dev/sdb[Input/output error]
ERROR: sil: reading /dev/sdb[Input/output error]
ERROR: via: reading /dev/sdb[Input/output error]
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb: Input/output error
hexdump: /dev/sdb1: Input/output error
hexdump: /dev/sdb2: Input/output error
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

```

---

### Post by dcsii on 2010-08-27
It especially troubles me that my larger drive doesn't appear as it's a 750 GB drive and as far as I can tell is attached correctly

EDIT: Just for the record I had disassembled and reassembled all the components, so what may have once been sda and sdb might have switched. I reassembled and reconnected the components because for some reason it wasn't manually turning on, and being that I'm doing this via a Live CD whatever I did solved the problem of manually coming on. However, I'm not very positive that my files on my main harddrive are gone. I'm worried that perhaps some bad blocks or something occurred but I don't know, cause I'm still quite the noob at dealing with this.

---

### Post by oldfred on 2010-08-27
It seems to see the partitions in sdb but not much else. 

You might try on every sdb partition from the liveCD.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Or try testdisk, but I am concerned that you may have major hard drive issues.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by dcsii on 2010-08-27
> **oldfred said:**
> It seems to see the partitions in sdb but not much else. 

You might try on every sdb partition from the liveCD.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1
[]("http://www.cgsecurity.org/wiki/Menu_Analyse")

Trying that I get the following response with respective numbers to each one I try and the same when I try without a number
> 
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then then the superblock is corrupt and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>


Testdisk I started to do, but it ran out of space when I tried to redirect it to another drive it ran out of space and everything locked up when I tried to do something about it. Considering the drive I'm trying to access is significantly bigger than the freespace of anything I have available. I debate whether I need something larger. Overall the drive was 750 GB free and from what I could tell it had 698 GB of files via testdisk to grab from. I have about 180 GB free on an external HD, and 29 GB free on sda1. So do I have to get another harddrive to get the 20GB or so of files I'm trying to salvage from the 750 GB drive?

When using testdisk, I made it about halfway down this link:
[http://www.psychocats.net/ubuntucat/...rdeletedfiles/]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/")

---

### Post by oldfred on 2010-08-27
Did you try any of the alternate superblocks?

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

### Post by dcsii on 2010-08-27
Haven't tried partmagic yet, but that's what I'm going to try next, this is all very frustrating. Especially since I can't seem to access it in any way, I hope I can access it this way. 

If not, then I guess I'm hoping my other machine has some of the data on it. But the other machine has issues that I just didn't want to deal with because of the video card seemed to be causing errors. Other parts of the data I know people that have copies I should be able to get at in two weeks. Just been trying to avoid the rest of this elaborate way to get everything that matters back.

---

### Post by dcsii on 2010-08-27
So, going around Parted Magic I'm not sure but I think I may have made things worse, I managed to find 3 numbers for bad sectors but I can't access anything for the drive at all anymore. Not sure what to do
 
The numbers of the sectors I'd found:(though they seem a bit high for numbers)
-29302983
-98340918
-189704358
 
It was from a mechanical scan of the drive and those three had warnings on them that two of them pinged between 150 and 500 ms, while the first one was over 500 ms, and the overall scan was of 1,465,000,000 sectors.
 
Other than getting that I'm lost, unsure wth to do, frustrated, think that the harddrive is dead, I don't know. Think I'm done for the night, and will go back to it with a cooler head, and looking at it with fresh eyes. I appreciate all the help that oldfred has given me, and maybe I could use a bit more. Right now, I'm going to give it some time and see what you all advise me to do.

---

### Post by oldfred on 2010-08-27
I am pretty much out of ideas. But note the script says you have 
312581808 sectors, so your numbers may be valid.

---

### Post by dcsii on 2010-08-28
Ok massive progress or maybe I'm just optimistic. I used a third harddrive and did a full install of Lucid Lynx, and I was able to see both of my other harddrives in the places tab. However, when trying to open the larger harddrive, , the 747 I got the following error message in a window:
 
[quote="error"]
Unable to mount 747 GB
Error mounting mount: wrong fs type, bad option, bad superblock on /dev/sb1
 
missing codepage or helper program or other error in some cases useful info is found in syslog dmesg | tail or so
[/quote]
 
I'm not sure if it _*really is*_ progress but it gave me a glimmer of hope to see a message like that coming from the GUI instead of doing something far more elaborate with testdisk. I probably should run through some of the same steps prior to doing this, and see if any changes have been made. However, given my setup it's hard to do at the moment, but I'll be sure to do it in a few hours. 
 
Would like confirmation on whether I need to re-run the last couple of processes, or if that error message has shown a clearer way to solve the problem. 
 
Thank you again oldfred for all the help thus far and hope that you'll read this post and have an idea of what to do. I think I need to run things again but I may not, I'm not sure enough to know.

---

### Post by oldfred on 2010-08-28
Using your new install of Ubuntu or the Parted Magic from the link have you tried reloading with alternate superblocks. Sometimes it takes more than one alternative. And possibly reruning the sudo e2fsck -f -y -v /dev/sdb1.

---

### Post by dcsii on 2010-08-29
Ok prior to this I had added a fresh harddrive and installed Lucid Lynx  on it. Now, I could "see" the 747 GB and 160 GB harddrives in the places  menu. However, when trying to access it output the following error:



I then input the code as follows:
```
sudo mke2fs -n /dev/sdb1
```It output the following list:
32768
98304
163840
229376
294912
819200
884736
1605632
2654208
4096000
7962624
11239424
20480000
23887872
71663616
78675968
102400000

I then put in the code for each of the _**17 number codes**_ as instructed with this code:
```
sudo e2fsck -b 32768 -p /dev/sdb1 
```Then each number code output the following:



I'm also going to note that the 747 GB harddrive is no longer listed in  the places menu. Not really sure what's going on, I'm kinda lost and  over my head

---

