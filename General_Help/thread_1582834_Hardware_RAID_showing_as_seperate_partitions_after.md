---
title: "Hardware RAID showing as seperate partitions after Ubuntu 10.04 upgrade"
date: 2010-09-27
forum: General Help
---

### Post by lightsabersetc on 2010-09-27
Hey Everyone,

I have been trying to upgrade my server to Ubuntu 10.04 since it has come out, but I hit a roadblock with my hardware RAID I have two JBODs that work perfectly in Ubuntu 9.10 x64 - but show as seperate, unformatted partitions (one per hdd) in Ubuntu 10.04 x64. Here's the relevant portion of my fstab:

UUID="1fac4a2c-6a2e-4278-bab4-c7179c8720ee" /media/Motherload ext4 exec,auto,async,rw 0 2  #4TB-ext4-/dev/mapper/pdc_cabedbfaef1
UUID="31f1f023-e6a0-4b5e-b9d9-0a46011e7fa0" /media/Fry ext4 exec,auto,async,rw 0 2 #3TB-ext4-/dev/mapper/pdc_gejagjajf1

I have tried mounting the devices with all possible identifiers to no avail. Following is the output from mount -a:
root@ubuntu:/home/ubuntu# vi /etc/fstab #Changed to UUID
root@ubuntu:/home/ubuntu# mount -a
mount: special device UUID="1fac4a2c-6a2e-4278-bab4-c7179c8720ee" does not exist
mount: special device UUID="31f1f023-e6a0-4b5e-b9d9-0a46011e7fa0" does not exist
root@ubuntu:/home/ubuntu# vi /etc/fstab #Changed to device
root@ubuntu:/home/ubuntu# mount -a
mount: special device /dev/mapper/pdc_cabedbfaef1 does not exist
mount: special device /dev/mapper/pdc_gejagjajf1 does not exist

I even pondered with the idea that maybe my motherboard (ECS BLACK SERIES A780GM-A) was actually some sort of spoofed software array so I attempted to mount the partitions with dmraid. I got to the point where it was obvious I was about to reformat my drives and stopped. At one point in the t/s process, the system was telling me it saw the devices, but they weren't formatted. I have been literally trying to figure this out for months (since 10.04 launched) and have failed every time - backup ftw. Any help would be appreciated :D

Thanks!

---

### Post by ronparent on 2010-09-27
I see you are using a fakeraid MB (that term drives me nuts). When 10.04 was launched, a bug prevented gparted from seeing the fakeraid partitions, effectively blocking anyone from installing 10.04 to a raid unless they employed a work around. I haven't personally checked on it, but, I thought it was handled with the 10.04.1 release.

In any event, I have found that installing a program called kpartx to a live cd session, running the install from the same session and selecting the manual partitioning in step 4 of the install permitted a more or less normal install. You can test the solution before you try the install. Good luck. Post if you run into any more problems.

---

### Post by lightsabersetc on 2010-09-27
It worked, thank you so much!

---

### Post by lightsabersetc on 2010-09-29
So maybe I jumped the gun on it working. Everything worked fine with the live disk, so I went ahead and upgraded my system. After upgrading and installing kpartx, I am now receiving this error:

mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_cabedbfaef,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg yields:


[47832.813841] EXT4-fs (dm-1): VFS: Can't find ext4 filesystem
[47832.826710] EXT4-fs (dm-0): VFS: Can't find ext4 filesystem

From reading the errors, I had a feeling I did something to completely wreck my raid array *GASP*, so I booted back to live disk, installed kpartx, and mounted the filesystems without any problems. Any ideas?

---

### Post by ronparent on 2010-09-29
You might try, from a live cd, uninstalling and purging the grub 2 distributed with 9.10, and installing grub-pc (a later version of grub distributed with 10.04). Use this reference for working wit grub: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

I don't think the normal upgrade deals with grub. I do think that trying to boot 10.04 with the version of grub 2 distributed with 9.10 causes problems. I've had to deal with that same issue but don't remember the details. If the 10.04 live properly detects your raid partitions, then they are valid for the upgraded install also and we have to find what is preventing them from being detected.

---

### Post by lightsabersetc on 2010-09-29
Thank you for your quick response! I am actually not trying to install ubuntu on the RAIDs, they are just storages drives. 

I was just able to get a few steps closer by installing dmraid also. After installing dmraid, if I open up gparted, I can now see the drives in their entirety and they are showing as formatted. I went ahead and tried to mount -a. I received no output from the command, and the drives did not mount. I was able to mount the devices through gparted by right clicking, going to mount to, and choosing the mount point. I edited my fstab to mount the drives with all available identifiers and the same thing happened. I have actually been having this problem since day one (aside from not being able to mount with the mount command). Ever since setting this raid up, I had to add gparted to my bootscript before the mount command so that the drives can be identified as RAID, then mount -a would mount the drives (they have never been able to auto-mount due to this). At this point, I am happy to at least have my drives mounted in the new version, but I would like the drives to be able to mount on system boot w/o ubuntu-desktop installed so I really need to figure out what is causing this. The weirdest part is, other flavors of linux I've tried (fedora,suse,debian) identify drives w/o issue - I just don't want to use those distros lol

Thanks again for helping out! Let me know if you need any more info :D

---

### Post by ronparent on 2010-09-29
Sorry, I misunderstood your situation. You ought to check that you are booting on the latest grub 2 release anyway.

You definitely have to have dmraid installed. Once installed the equivalent of dmraid -ay is automatically executed on boot and all your raid partitions are automatically made mountable and should be seen in nautilus. You shouldn't need any special add-ons to the boot scripts to accomplish this - and they may be counter productive! That at least is what I would expect with my own setup. You might examine your boot up logs for some clue as to what is happening with the raids. I'll have to reboot into 10.04 myself to see what should be happening - playing with 10.10 too much leaves me fuzzy on 10.04 behavior with raids.

---

### Post by psusi on 2010-09-29
> **lightsabersetc said:**
> 
mount: wrong fs type, bad option, bad superblock on /dev/mapper/pdc_cabedbfaef,

You seem to be missing the partition number at the end of the name there.

---

### Post by ronparent on 2010-09-29
Sharp eyes psusi.  /dev/mapper/pdc_cabedbfaef is not mountable, it is the entire raid array and contains no file system! 

lightsabersetc: you might want to undo any scripts you may of added!

---

### Post by lightsabersetc on 2010-09-29
> **psusi said:**
> You seem to be missing the partition number at the end of the name there.

Good catch there, thank you. I'm not sure where in the troubleshooting process I dropped the partition #, but i certainly did. I went ahead and changed that, but the drives still did not mount. Just in case I may have messed something up along the way, here is the current relevant portion of the fstab, and output from mount command. As you see, I'm trying with the UUID of one drive, and the path of the other:
#######
/etc/fstab:
#######
UUID=1fac4a2c-6a2e-4278-bab4-c7179c8720ee /media/Motherload ext4 nouser,exec,auto,async,rw 0 2  #/dev/mapper/pdc_cabedbfaef1

/dev/mapper/pdc_gejagjajf1 /media/Fry ext4 nouser,exec,auto,async,rw 0 2  #UUID=31f1f023-e6a0-4b5e-b9d9-0a46011e7fa0
#######

mount -a
results in no output, no drives are mounted.

#######

sudo fdisk -l:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      267350  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      267350  2147483647+  ee  GPT

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c2f6cf9

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00074965

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19205   154264131   83  Linux
/dev/sdd2           19206       20023     6570585    5  Extended
/dev/sdd5           19206       20023     6570553+  82  Linux swap / Solaris

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6d61c3c4

   Device Boot      Start         End      Blocks   Id  System
############END##########


On a side note, I am updating GRUB right now :)

---

### Post by lightsabersetc on 2010-09-29
I finished the GRUB upgrade, and there was no change :( . It turns out if I open gparted, then run the mount command; the drives do mount. The system still hangs @ boot with this message:

"The disk drive for /media/Motherload is not ready yet or not present."

I press S to skip, then get the same message for the other drive. After the system boots, I ran:

dave@server:~$ sudo mount -a
mount: special device /dev/mapper/pdc_cabedbfaef1 does not exist
mount: special device /dev/mapper/pdc_gejagjajf1 does not exist

dave@server:~$ sudo dmraid -ay
RAID set "pdc_gejagjajf" already active
RAID set "pdc_cabedbfaef" already active


Then I open gparted, run mount-a, and disks are mounted successfully. The good part is, I am back to where I was with Ubuntu 9 with just having to open gparted before mounting. Bad part is, I still have to have ubuntu-desktop installed. Thanks for your help everyone, any other ideas are greatly appreciated! :D

---

### Post by ronparent on 2010-09-29
Just a simple question: why do you feel you have to pre-mount your raid partitions.

Prior to 9.04 I had to pre-mount on boot with fstab to see or act on any file within a raid partition.. With the initial release of 9.04 a fundamental change in behavior occurred witch blocked the raid partitions from premounting during boot and my fstab raid mounting notations became useless. I skipped 9.10 which actually improved raid behavior. Now with 10.04, if you can get past the installation blockade, the raid partitions are actually very accessible with no fiddling with fstab. No partitions, raid or otherwise are actually mounted on boot except for the partition you are booting. They are actually mountable with all of the file functions I have observed. I have not needed to explicitly mount any of my raid data partitions since this is automatically accomplished when files on the partition are accessed. I suspect what you are trying to do is unnecessary and that the mount points in the filesystem for the partitions already have been established. Am I missing something?

---

### Post by lightsabersetc on 2010-09-29
> **ronparent said:**
> Just a simple question: why do you feel you have to pre-mount your raid partitions.

Prior to 9.04 I had to pre-mount on boot with fstab to see or act on any file within a raid partition.. With the initial release of 9.04 a fundamental change in behavior occurred witch blocked the raid partitions from premounting during boot and my fstab raid mounting notations became useless. I skipped 9.10 which actually improved raid behavior. Now with 10.04, if you can get past the installation blockade, the raid partitions are actually very accessible with no fiddling with fstab. No partitions, raid or otherwise are actually mounted on boot except for the partition you are booting. They are actually mountable with all of the file functions I have observed. I have not needed to explicitly mount any of my raid data partitions since this is automatically accomplished when files on the partition are accessed. I suspect what you are trying to do is unnecessary and that the mount points in the filesystem for the partitions already have been established. Am I missing something?

It's not necessarily that I want the drives to mount on boot, I just want them to mount at some point. It is my understanding that I can't mount a device in terminal w/o first having declared it in my fstab. As it is now, I have to open gparted for the system to recognize the disks are actually a RAID, then run the mount command, then everything is accessible in the directory I mount it in. Is there something I'm missing?

---

### Post by ronparent on 2010-09-29
I don't know that this meets your needs,but, you can open nautius (ie places>computer) and all of your partitions should be listed. Any one of them can be mounted by right clicking on it - or a group by selecting several and right clicking. Less cumbersome then opening gparted. I see that could be cumbersome if you are operating completely in a command line environment. I can't immediately think how to get around that since the mount points within the file system are not established until the partitions are actually mounted?

edit: Does the location /media/Fry exist? Test with a simple mount command.

---

### Post by ronparent on 2010-09-29
For what it is worth, this was a typical fstab entry I previously used:

#/dev/sdb  nvidia_aebhdfib7  f:\PICTURES
/dev/mapper/nvidia_aebhdfib7	/WinXP/PICTURES	auto	relatime	0	1

I had to pre-create the /WinXP/PICTURES location. Little else was needed to make it operational.

---

### Post by psusi on 2010-09-29
Ahh, you appear to be using a GPT partition table, and dmraid does not understand that.

---

