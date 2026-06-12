---
title: "Boots into wrong OS when chosen from GRUB"
date: 2011-04-28
forum: General Help
---

### Post by one2fwee on 2011-04-28
My soundcard seems to have problems working with a certain game in windows xp so i decided to create a different installation of windows xp to use with onboard sound drivers instead.

I had a backup of my clean current install on a dvd, so thought i would use this to speed up the proceedure.

I have two hard drives - the sata has my normal windows boot on and my ext4 ubuntu installation. The id drive has only files on.
So i decided to shrink the partion on the ide drive using gparted and then create a new primary partition.

I then installed my backup to this newly created partition.

At first it did not appear in the boot manager. Then i did a sudo update-grub and it now does, however whichever windows installation i now select from the grub, it always seems to boot into the same (old) installation, rather than the new one i installed from a backup.

Does anyone have any ideas how i can actually get it to boot into this new installation?
It might be due to windows boot ini settings or disc / partition flags or whatever, as i tried fiddling with those to help but i don't really know what i'm doing, and it didn't.

I can provide any more info that may be of use - would screenshots of what gparted displays be helpful?

Thank you for your time.

---

### Post by oldfred on 2011-04-28
You might want to check boot.ini

---

### Post by LostFarmer on 2011-04-28
Boot into XP - get to Disk Management- Does it show C: as Boot and D: as System or visa versa ?   If so you will need to modify the registry or temporarily delete the installed XP partition  (save MBR with dd , delete partition with fdisk, boot into XP 2 times, restore MBR with dd 'very basic how to') .  

My guess is the cloned copy of XP has HKLM/System/MountedDevices wrong , so it will complete the boot into the first primary partition that has XP in it.

Is the cloned XP on a primary partition ?  post output of linux's  ' fdisk -lu' Note l=small L

---

### Post by one2fwee on 2011-04-29
fdisk -lu didn't appear to do anything - ran it and nothing happened. Tried fdisk -lu * and it started to work on files in my home directory?? and fdisk /mount/partition_id/ just got it saying that it couldn't work with that kind of file.

(Mind you i am having problems with ubuntu do to getting the beta - quickly afterwards i realised that probably wasn't the best idea. Also apparently the release is out yet i cannot update to it. I guess it might be easier to do a fresh install.)

Here is what gparted shows, if that is any help:

First hard drive contains my current windows install and linux - i think the unallocated in that extended partition may be swap or whatever it is called. Not sure why it doesn't say so: [http://img839.imageshack.us/img839/5845/hd1n.png](http://img839.imageshack.us/img839/5845/hd1n.png)

Second hard drive contains general file storage for windows / linux (firefox profile etc).
Also contains my new windows partition, sda2 (named old_games) that i am trying to get into: [http://img815.imageshack.us/img815/5189/hd2v.png](http://img815.imageshack.us/img815/5189/hd2v.png)

boot.ini for windows that i'm trying to get into:
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft WinXP (on Volume 2)" /noexecute=optin /fastdetect
```boot.ini for normal windows that it goes into no matter what:
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
 
[spybotsd] 
timeout.old=30 
```I tried changing rdisk in the first boot ini to 1, since it's on a seperate hard drive but it didn't seem to help. Maybe that wasn't quite the change needed.

Loaded the registry hive of the windows i was trying to get in and altered the C: mounted device partition key so that it referred to the partition that had the correct installation on (copying the key from my G: partition on the other windows install).
Didn't help.

I guess it's not even getting that far so i would assume boot ini? Don't know what it should be though?

Thanks

---

### Post by LostFarmer on 2011-04-29
To run 'fdisk -lu' , you must have root privileges.  So it will be su fdisk -lu.  

Please post the 'su fdisk -lu' , and from XP the values in regedit values under /hklm/system/mounteddevices/  --all entries titled 'dosx'  ('DosC:,ect' there should be about 6 double digit values for each).  

Will have to get back later when I have time to boot into XP and not guess.

Need to see also the /boot/grub/grub.cfg entries for both XP's, that could be the problem.

---

### Post by oldfred on 2011-04-29
You mention hive. Do you also have Vista or 7? Windows always installs to one version and normally moves all the boot files to that first install. Then that first version lets you boot the other installed windows.

Drive would have to be 1. But partition boot sector also has to have correct info inside it. Usually moving boot flag and running fixboot fixes the boot sector.

---

### Post by one2fwee on 2011-04-29
Ah, hahah normally it tells me when something requires permissions. Here you go:
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x47334732

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   299665407   149832672+   7  HPFS/NTFS
/dev/sda2       299676510   320170485    10246988    7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb71eb71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   366587234   183293586    7  HPFS/NTFS
/dev/sdb2       366587902   488396799    60904449    5  Extended
/dev/sdb5       366587904   482537471    57974784   83  Linux

Disk /dev/sdc: 1049 MB, 1049624576 bytes
29 heads, 28 sectors/track, 2524 cylinders, total 2050048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x61c817b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          64     2050047     1024992    b  W95 FAT32

```Grub.cfg entries:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft WinXP (on Volume 2) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 07EB6511100430C2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 07EB6511100430C2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```
Is there any easy way to copy/paste from regedt32? I'm guessing not. Will try when i boot into windows xp.

Oldfred, no i just have windows xp home - reason i am trying to have it twice is i want one installation to use different sound hardware (and therefore drivers).

Are you suggesting moving the boot flag on the second hard drive to the windows partition i just "restored"? To be honest i am not even sure why the file storage partition is listed as boot? I guess one partition has to be then, and considering that was there first, it was previously (even though of course it cannot boot).
Thing is i did try changing the boot to be the new windows and then booting from that hard disk but it didn't help - and anyway i would want to really boot from the other disk and then just select the os i want, no matter what disk it is on.

---

### Post by oldfred on 2011-04-29
Your grub entry has the same UUID in the search which overides the set root.

07EB6511100430C2

---

### Post by LostFarmer on 2011-04-29
There may be a problem with the grub.cfg entries, will let 'oldfred' comment on this:```
search --no-floppy --fs-uuid --set=root 07EB6511100430C2
``` both entries have the same uuid # at this point.  But I do not know if grub uses that entire for 
drivemap -s (hd0) ${root}
or ```
set root='(/dev/sdb,msdos1)
``` , which is correct.

If it is only a XP registry problem , will post some pointers where you may know enough to check and fix.  

EDIT: see 'oldfred' as also seen above possible problem, you could just  manualy edit boot.cfg and ## 'comment' out that line.  You will have to  have root permissions to do so.

{From my comp}

```
sudo fdisk -lu
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   [COLOR=Red]204860880[/COLOR]   235593224    15366172+   c  W95 FAT32 (LBA)


sudo dd if=/dev/sda count=1 bs=512 |hexdump
00001b0 0000 0000 0000 0000 [COLOR=Blue]aa3f ef0b[/COLOR] 0000 0080

HKLM/system/Mounteddevices\DosDevices\C: REG_Binary  [COLOR=Blue]3f aa 0b ef[/COLOR] 00[COLOR=Red] a0 db 6b 18[/COLOR]  
```The part in [COLOR=Red]RED[/COLOR] is the Start Sector # *2 and converted to HEX in little engin format. 
204860880*2=409721760=0x186bdba0=a0db6b18
The part in [COLOR=Blue]BLUE[/COLOR] is the hdd ID stored in the MBR in little engin format.[COLOR=Black]

When you are booted in the working XP, run regedit.
1) hilight hklm/ File (top right of window) select  'load hive'
2)in the new 'Load Hive' search window go to non working XP\windows\system32\config\system 'double click'
3) Load Hive 'Key Name' pop up type in  TEST 
4)There will be a new key "TEST" under /hklm/system/TEST
5)  open the new TEST key and and open/MountedDevices
6)modify data in "TEST\MountedDevices \DosDevice\C: to be the same as shown in the hklm/system/DosDevice\XX:   ---XX is the drive letter of non working XP as seen by the working XP. 
7) hilight the hklm/TEST and select in FILE upload hive.
 8 )  close regedit and reboot.

I do know that my writing is very poor so hopefully you can figure out what I'm saying.

It would be a good idea before any editing you make a backup copy of both /window/system32/config folders. You will need to do so from linux. XP will not let you copy the config folder that is in use.

From your fdisk, the hklm\system\TEST\Moundeddevices /DosDevice/C: in non working XP , when it's 'system' key is uploaded. The second set of digits in 'red above example' will be [/COLOR]299676510*2=599353020---0x23b966bc --[COLOR=Red]bc 66 b9 23[/COLOR]
[COLOR=Black]
[/COLOR]

---

### Post by one2fwee on 2011-04-29
Normal windows:
[IMG]http://img146.imageshack.us/img146/2312/currentw.png[/IMG]

C - old windows install
F - file storage drive
G - windows install i am trying to access


Loaded heap from windows i am traing to access:
[IMG]http://img847.imageshack.us/img847/8931/newpw.png[/IMG]

However i already modified the C drive on here to be the same as the G drive in the other registry - as that is the location the installation is on. It didn't help though. Cannot remember what it was previously, but it was wrong / different.

---

### Post by LostFarmer on 2011-04-29
The mounted devices are now correct.  The problem now I would say is that both partitions have the same UUID # ( it would do to cloning) .  In XP's volume boot record 'Volume Serial Number' is used for grubs UUID, I do not think that XP uses that infor for anything.
 [http://www.ntfs.com/ntfs-partition-boot-sector.htm](http://www.ntfs.com/ntfs-partition-boot-sector.htm)

From my system: (just parts from XP on sdb5)
dd if=/dev/sdb5 count=1 bs=512 |hexdump
0000040 00f6 0000 0001 0000 [COLOR=Red]3f11 d85c 5c76 6ed8[/COLOR]

grub.cfg
search --no-floppy --fs-uuid --set[COLOR=Red] 6ed8 5c76 d85c 3f11[/COLOR]

The # are the same.  You could edit XP's volume boot record, (make your own #), then rerun update-grub . 

You could edit via XP and run a MS's 'diskprob' (on the MS XP cd or find at microsoft) or use linux. First you would need to use dd to save XP's volume boot record to a file, edit file with a hex editor "Bless Hex Editor" then write the edited file to XP's volume boot record.  Volume Boot Record is the first sector of XP partition.

The easiest would be to edit grub.cfg and comment out the floppy search line. You would have to do it each time update-grub is ran by you or some updates.

Just to let you know, I never do things the correct way.

---

### Post by one2fwee on 2011-04-29
No luck in commenting out that search for floppy line with #
When i did that and dtried to boot, it said:

```
error: device format "/dev/sda, msdos2" invalid: must be (f|h)dN with 0 <= N , 128
error: No such disk
```Definately grub that is having the problem though.

I modified the boot ini of the windows that works to add the line ```
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft WinXP (on Volume 2)" /noexecute=optin /fastdetect
```This means that after grub, windows' own boot loader lets me choose os and that works. However i would like to get it working via grub if that is possible.

I guess diskprob would be easiest? Or i can try hexediting. Thing is, if i make something up, what if windows uses the uid for some kind of activation thing and has a panic attack because i changed it. Or does it use another id for things like that?

What is dd? i did a man dd on it and it seemed to be something about copying files or something, which seemed a bit confusing.

---

### Post by LostFarmer on 2011-04-29
[QUOTEset root='(/dev/sdb,msdos1)'][/QUOTE] that line is wrong if not using the UUID. (?)

should be  set root="(hd1,msdos2)'  NOTE: can not say for sure but the hd1 may need to be hd0.

>  Or does it use another id for things like that?
 can not say for sure , I have never change the volume #, but have coped XP to a different partition using a third copy of XP with no problems, click and paste.

For linux using 'dd if=/dev/sdb of=sdbvbr count=1 bs=512'   where if=inputfile/device and of=output file/device.  You would use say Bliss Hex Editor on file sdbvbr , then use
'dd if=sdbvbr of=/dev/sdb count=1 bs=512' .  Note: the use of 'dd' can destory the file system if a mistake is made.

When using any hex editor be SURE that it is not in the insert mode, make sure it is in the replace mode.

---

### Post by one2fwee on 2011-04-30
Okay, changing it to hd1,msdos2 and commenting out the floppy disc check worked.
Not a permanent solution as every time grub is updated i will have to do it again but at least i shall not break anything that way.

Wouldn't really know what exactly i was doing with dd, or even what the command means itself so probably better not to try something if i don't have a vague understanding of it, less it goes wrong and then would be even more confused.

Thank you for your help.

---

### Post by LostFarmer on 2011-04-30
> Not a permanent solution as every time grub is updated i will have to do  it again but at least i shall not break anything that way. I think there is a way to change that ,READ the links below.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
I did not reread the links so could be wrong.  Go to /etc/grub.d/  and put the correct menuentry for XP into 40_custom. Make 40_custom executable and remove 30_os-prober executable bit.

---

### Post by one2fwee on 2011-04-30
Okay thanks, i'll have a look. Are those links supposed to be the same by the way?

---

### Post by LostFarmer on 2011-04-30
[]("https://help.ubuntu.com/community/Grub2")My error.
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

