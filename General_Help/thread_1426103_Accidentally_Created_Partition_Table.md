---
title: "Accidentally Created Partition Table"
date: 2010-03-09
forum: General Help
---

### Post by chochy on 2010-03-09
Alright, so, I booted using linux live, and was poking around Gparted, and was going to test some things on my extra hdd (80gb, IDE) -I thought that extra hard drive was selected, what I clicked Create Partition Table. Apparently, it was my primary hdd, (250gb Sata, Windows Vista x64) that was selected.

I think I may have tried to cancel it after a few seconds, realizing what was happening, but yeah, it now shows the entire hdd as unallocated space.

I immediately shut down the computer, pulled out linux live and tried to boot to windows, but I immediately got an error saying the disk couldn't boot, asking for a system disk.


There was a thread with a guy who had a similar thing happen to him, but the thread dropped off... [http://ubuntuforums.org/showthread.php?p=7034672](http://ubuntuforums.org/showthread.php?p=7034672)


sudo ./testdisk_static

Opened testdisk for me, but now that testdisk is open, I'm not really sure what I need to do. 

I'm guessing that the boot sector on that hdd is gone..

Can anyone tell me the bottom line on this? Are my files gone forever? There are some files that I don't have backed up on there, that I'm hoping are not gone. I would love it even more if I could somehow just repair that boot sector, and not have to reinstall everything on my machine.


Any advice would be awesome!


Steve

---

### Post by srs5694 on 2010-03-09
I've never used testdisk, but I quickly found this guide, which may help:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you're lucky, you'll be able to recover your partitions. You may need to reinstall a boot loader in the disk's MBR to make the system bootable again. Depending on the options you selected in GParted, it's conceivable your filesystems are damaged, too, but if you *only* created a new partition table, they *should* be OK, just inaccessible because the system can't find them.

In the future, back up your partition tables. You can make a binary backup with dd ("dd if=/dev/sda of=sda-backup.mbr bs=512 count=1"), but that only backs up the primary partitions. To back up both primary and logical partitions, you can use sfdisk:

```
sfdisk -d /dev/sda > sda-backup.txt
```

This assumes you're using MBR, which seems likely given that you had Windows on the disk. If you're using GPT, I recommend you use my [GPT fdisk](http://www.rodsbooks.com/gdisk/) to back up the GPT data. It's the 'b' option on the main menu. Alternatively, you can do a dd copy of the first 34 blocks, assuming a standard partition table size. The dd copy will get the primary table, but not the backup, which is stored at the end of the disk. Still, restoring the primary will enable disk utilities to recreate the backup.

---

### Post by chochy on 2010-03-09
> **srs5694 said:**
> I've never used testdisk, but I quickly found this guide, which may help:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you're lucky, you'll be able to recover your partitions. You may need to reinstall a boot loader in the disk's MBR to make the system bootable again. Depending on the options you selected in GParted, it's conceivable your filesystems are damaged, too, but if you *only* created a new partition table, they *should* be OK, just inaccessible because the system can't find them.



Any thoughts on how to go about reinstalling the boot loader?

The attachment shows where I'm at with teskdisk... Should I be writing the partitions to disk?

Also... The backup your talking about... If I'm understanding you correctly... It won't help me in my current state, but would be life saver in the future?



Edit* - I used the MBR repair in testdisk, and tried rebooting to windows, and a prompt written 1234F: shows up, but does not boot to windows no matter what number I type :(

---

### Post by meierfra. on 2010-03-09
> Should I be writing the partitions to disk?
No. You seem to be missing the Windows System partition.  Did you do the "Deep search"?  Post  a screen shot of  deep search results.

---

### Post by chochy on 2010-03-10
Heres the results from the deepsearch...

---

### Post by chochy on 2010-03-10
Anyone know what to do now?

---

### Post by meierfra. on 2010-03-10
[QUOTE=meierfra.]You seem to be missing the Windows System partition.
[/QUOTE]

Actually I was wrong about the missing system partition, ( I was mislead since the Vista was listed as logical partition).

[QUOTE=chochy]Anyone know what to do now? [/QUOTE]
Select each of the two partitions found by the deep search and press "p". See which of them gives you a directory listing. (Pressing "esc" will get you back to screen with the deep search result)

Then, at the screen with the deep search result, select the partition which gave you a directory listing. Use the "left arrow" key to change to first entry in that row to a "*":

So the first two colums should look like 


*  HPFS-NTFS 
D  HPFS-NTFS


or

D HPFS-NTFS 
* HPFS-NTFS


depending on which of the two partition gave you a directory listing.

Then press "enter" to continue. Choose "write" at the next screen.  Confirm the changes if asked. 

 I don't think you will have to reinstall the boot loader. So just reboot and hope for the best.

---

### Post by chochy on 2010-03-10
Okay, I did the deep search, and listed the directories... I posted screenshots of both- They're pretty much identical other than in size...

Which should I edit?

Thanks so much for the help....

---

### Post by meierfra. on 2010-03-10
Probably either one will be fine. But I would pick the larger one:

D HPFS-NTFS
* HPFS-NTFS

---

### Post by chochy on 2010-03-11
Okay, so I made *some* progress:

After writing to disk, I rebooted- 


I got an error that I was missing winload.exe and that I need to insert the manufacturers disk (my Vista cd) to repair the installation.

Unfortunately, I don't have the disk on me right now, but I'll have it in a couple days to try that out. I'll let you guys know how it goes...

Any other things I might try in the mean time?


Thanks for all the help

---

### Post by meierfra. on 2010-03-11
> was missing winload.exe 
I'm not sure what caused this, maybe the disk signature got erased.

> don't have the disk on me right now,

You can download a  Vista Recovery CD from [ here]("http://www.pcworld.com/downloads/file/fid,71039/description.html") or [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

> to repair the installation.


I suggest to  run "Start-up repair:

Boot from the Vista CD.
At the first screen select your favorite language.
At the second screen choose "Repair your Computer".

If a pop windows appears, offering  to repair a problem with the "Startup options",   click on "Repair and restart".

Otherwise, on the  next screen select  your operating system under "Use recovery tools ..."  and click on "Next".

Choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

This link contains picture of the various screens:  [http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by tommynz1975 on 2010-03-11
posibly try hirens boot cd?
contains "partition find and mount and many disk utilities.

this used to contain super grub and still may?? the program would look for all installed OSs and try and boot the one you selected.

[http://www.hirensbootcd.net/details/10.2.html](http://www.hirensbootcd.net/details/10.2.html)

The link is at the bottom of the page

Best of luck.

---

### Post by chochy on 2010-03-12
Used Windows Vista repair disc-

It recognized "Startup Errors" and tried to repair them... and failed. However, there may have been some progress, because now the file that is missing upon startup is

"boot\bcd"

I tried several times, as you mentioned, but it doesnt get past this file- I'll take a crack at hirens boot disc next. Thanks for the help guys.

---

### Post by meierfra. on 2010-03-13
Lets check out your system. Follow these [instruction]("http://bootinfoscript.sourceforge.net") to run the boot info script and post the RESULTS.txt.

---

### Post by pbrane on 2010-03-13
I know this won't help you now, but when you get everything working again, print out a copy of your partition data. It's simple to re-create the partition by putting in the original values. I've done it several times. You just have to make sure you don't format or otherwise change the data on the disc. When you do that everything is as it was.

---

### Post by chochy on 2010-03-15
Here is Results.txt


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb has 
                       66055247 sectors, but according to the info from 
                       fdisk, it has 156368016 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92bb91a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 8005 MB, 8005787648 bytes
32 heads, 63 sectors/track, 7756 cylinders, total 15636304 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x675e0b23

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63    15,636,095    15,636,033   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        146046D36046BAEE                       ntfs                                     
/dev/sdb         34AE7C6EAE7C2B0E                       ntfs                                     
/dev/sdg1        5204-7E09                              vfat       KINGSTON                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```
And yes.. having a copy of my partition data would've been awesome... :(

---

### Post by meierfra. on 2010-03-15
>  Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

You are indeed missing the file "/Boot/bcd".  This is pretty strange for two reasons:
  [list=1]
[*]Changing the partitions table should not have deleted "/Boot/bcd".  
[*]  Runnning "Startup Repair" should have created a new "/Boot/bcd"
[/list]

Anyway, lets see whether "bootrect RebuildBCd" can restore the bcd: 

Boot from the Windows CD as before. But instead of choosing "Startup Repair" choose "Command Prompt". Then

```
bootrec /FixMbr
chkdsk /r
bootrec /FixBoot
bootrec /RebuildBcd
```

The first command will replace your current "testdisk" MBR by a Windows MBR. It's unlikely, that this will make any difference, but it won't hurt either.  
The second command runs a files system check and the third command's will rebuild the boot sector.  The Boot Info Script  did not detect any problems with filesystem and the boot sector, but  since the partition table was changes, I still recommend to   run those command as  a precaution. 
The last command  should find the  Vista operation system and give  you an option to add it to the bcd. This should recreate the missing "Boot/bcd".

Since StartUp Repair did not recreate the "bcd", I'm not sure whether "bootrect /RebuildBcd" will be successful. If it fails, one can try to manually recreate the BCD, but we'll worry about that later.

---

### Post by chochy on 2010-03-15
.

---

### Post by chochy on 2010-03-15
Okay...

So, "bootrect" was not a command, but "bootrec" was, and had all of the appropriate options you mentioned.

bootrec /FixMbr - Successful
Chkdsk /r - "Cannot lock current drive. Windows cannot run disk check on this volume because it is write protected."
bootrec /Fixboot - Successful
bootrec /RebuildBcd - Identified Windows installs: 1  Add Installation to boot list?  (I chose Yes, and when I did, I got the following message:)

"The requested system device cannot be found."


The chkdsk error is what puzzles me, but it also would explain why the automatic repairs have not been working... Any thoughts?

---

### Post by meierfra. on 2010-03-15
> bootrect" was not a command, but "bootrec"
Sorry for the typo.


> Chkdsk /r - "Cannot lock current drive. Windows cannot run disk check on this volume because it is write protected."


"The requested system device cannot be found."

I'm not sure what is going on, but lets see whether your Vista partition is detected correctly:

Boot from the Windows CD and go to the "Command Prompt" as before. Type

```
diskpart 
```
and at the "diskpart>" prompt:

```
list volume
```

Does that list your Vista partition? And does the Vista partition have a drive letter assigned?
 

Type

   ```
select volume [COLOR="Red"]3[/COLOR]  
```

(but  replace "3" by  the volume number for  your Vista partition according to the   "list volume" output)

If no drive letter was assigned to your Vista partition:

```
  assign letter [COLOR="Red"]K[/COLOR]
```
Here "K" needs to be some letter which is not used by any other volume.

Type 

```
exit
```
to exit "diskpart".  Next

```
chkdsk /r [COLOR="Red"]K:[/COLOR]
bootrec /RebuildBcd
```

but replace "K:"  by  the drive letter for your Vista partition.

---

### Post by chochy on 2010-03-16
Okay, so "list volume," showed my drives as NTFS, but said nothing about either of them having vista. I selected the correct volume (D) (I knew which was which based on the size), and ran a chkdsk /r d:

The chkdsk seemed to run without incident, and even made a few repairs, however, it did not change the results of the  "bootrec /RebuildBcd." 



At this point... I'm ready to look at some other options... There must be some sort of file recovery program that can help me rip my files off the hdd in its current state.. If I could do that, I'll just format the whole thing and re-install, unless you have any other thoughts or suggestion. I'm open to trying whatever if it keeps me from losing all of those files....


Thanks for all the help so far....

---

### Post by meierfra. on 2010-03-16
> There must be some sort of file recovery program that can help me rip my files off the hdd in its current state..

The boot info script was able to mount your Vista partition. So  you should be able to access all you Vista files from the Ubuntu Live CD: Just go to Places->Computer and double click the icon for the Vista partition. 


> I selected the correct volume (D) 
Maybe "bootrec" gets confused since Vista is the D: drive and not C: drive.

Before reinstalling  I suggest to try this: Go the the "Command Prompt" of the Vista CD as before.

```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
``` Determine the drive letter for your Vista partition. It should still be D:. If the drive letter of your Vista partition is different, you need to replace all "D:"  in the instructions below accordingly.  Also determine the drive letter for the CDrom drive, I'll  assume that is "E:".  Type

```
 exit
``` to exit the ``diskpart'' prompt.

Type

```

mkdir D:\BOOT

copy E:\BOOT D:\BOOT 

bcdedit /store D:\boot\bcd /set {default} osdevice boot

bcdedit /store D:\boot\bcd /set {default} device boot

bcdedit /store D:\boot\bcd /set {default} path \Windows\system32\winload.exe

bcdedit /store D:\boot\bcd /set {bootmgr} device boot

bcdedit /store D:\boot\bcd /set {memdiag} device boot

```

Reboot and see whether you can boot into Vista.

---

### Post by chochy on 2010-03-16
>  The boot info script was able to mount your Vista partition. So you should be able to access all you Vista files from the Ubuntu Live CD: Just go to Places->Computer and double click the icon for the Vista partition.You are quite right. At the very least, I'll be able to back those up.

> 
mkdir D:\BOOT

copy E:\BOOT D:\BOOT 

bcdedit /store D:\boot\bcd /set {default} osdevice boot

bcdedit /store D:\boot\bcd /set {default} device boot

bcdedit /store D:\boot\bcd /set {default} path \Windows\system32\winload.exe

bcdedit /store D:\boot\bcd /set {bootmgr} device boot

bcdedit /store D:\boot\bcd /set {memdiag} device boot Im guessing "/createstore" is the parameter you are meaning... "/store" was not an option.

Running the above commands with "/createstore," gave me the following error for every single command:

"The boot configuration data store could not be opened. The requested system device cannot be found." :(

---

### Post by meierfra. on 2010-03-16
> "/createstore" is the parameter you are meaning... "/store" was not an option.

I meant "/store"   and it has been an option for any version of "bcdedit" I have ever seen. 

I suggest to try again.  What Vista CD are you using?

---

### Post by chochy on 2010-03-16
> I meant "/store"   and it has been an option for any version of "bcdedit" I have ever seen. 
My mistake-- You're right about that, I had just misread the error it gave me- Using /store, I received this error for each command: "The element data type specified is not recognized, or does not apply to the specified entry. Run bcdedit /? for command line assistance.

I only saw the "command line assistance," line and assumed the syntax was wrong.


> I suggest to try again.  What Vista CD are you using?Windows Vista Home Premium SP1 OEL version.

---

### Post by meierfra. on 2010-03-16
I just did seem testing. I get the same error message if I misspell "osdevice",  "device" or "path".  Are you sure you typed the commands correctly?

---

### Post by chochy on 2010-03-16
> I just did seem testing. I get the same error message if I misspell "osdevice", "device" or "path". Are you sure you typed the commands correctly?I had the wrong brackets. I was using () instead {}, which apparently makes a difference.


Progress!!!

Windows actually booted vista correctly until just after selecting the user- It hangs on "Preparing the your Desktop," and finally gives an error entitled "rundll32.exe" - Windows cannot access the specified file. You may not have permission.


I was interested to see if using Repair on the Vista installation could take me the rest of the way, but actually, it harmed more than helped. After trying to do the startup repair, boot/bcd was missing again. 

I ran the bcdedit commands again, and now am back to hanging on "Preparing your Desktop," and the "rundll32.exe" error.


So close!!!!!


Thanks for all your help so far!

---

### Post by meierfra. on 2010-03-17
Testdisk "mbr"  erases the "disk signature"  and that can lead to problems with drive letters. So I suggest to erase the Mounted Devices registry. Go to the "Command Prompt on the Vista CD as before

Type 
```
 regedit 
```
to open the Registry Editor.

Select "HKey_Local_Maschine" in the left panel.
Select  "Load Hive" in the "File" menu.

In the Pop Up Box, navigate to the  \Window\System32\config folder in your Vista Partition. 
Select the file "SYSTEM" and click open. 
In the new box type "MyHive" and hit enter.
Click on the "+"  signs next the "HKey_Local_Maschine"". 
You should now have an entry  named "MyHive in the left panel.
Click on  the "+" sign next to "MyHive".
RightClick "MountedDevices"  and choose "Delete".
Select   "MyHive". 
Select "Unload Hive" in the "File" menu.

Reboot.  Vista  should automatically regenerate the "mounted device" registry.

---

### Post by chochy on 2010-03-17
I followed the steps, but was again stopped by the rundll32.exe error. I tried to repeat the steps in case I had done something wrong but could not complete them a second time.


After loading the hive a second time, Mounted Devices had not re-appeared. As an alternative, can I load the SYSTEM file off of the Vista install disc?



Thanks,

---

### Post by chochy on 2010-03-17
Update:


Okay, so upon receiving the "rundll32.exe" error, I started task manager, and found that there were 3 processes called rundll32.exe running. I killed all 3 of those processes, and then used task manager to start explorer.exe

Windows loaded me to a "temporary user," because my user settings could not be loaded. This is better than nothing, definitely.. Any thoughts about how to repair my user?



Thanks,

---

### Post by chochy on 2010-03-23
Any thoughts on this?

The "temporary user," does not allow for any applications to run. I tried to make a new user, but it appears those .dll files are missing as well. Nothing happens when I click to make a new user.

---

