---
title: "Problem with raid 5 in ubuntu 10.10"
date: 2011-03-18
forum: General Help
---

### Post by branko.savic on 2011-03-18
I have installed ubuntu 10.10 from windows wubi, the problem is that ubuntu does not seem to recognize my raid 5 array!

It is raided from the motherboard, and the chipset is Intel matrix ICH10R, raid 5 with 3 1TB harddrives, formated with NTFS file system!

I am pretty new to ubuntu, so any help would be greatly appreciated!

Thanks!

---

### Post by Rubi1200 on 2011-03-18
Hi,

please do the following so we can get a better overview of the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by branko.savic on 2011-03-18
I am able to enter ubuntu, it resides on the C drive that is not raided, the raided drives are set in windows as D: and E:!

But ubuntu does not see it!

---

### Post by Rubi1200 on 2011-03-18
What happens if you do this?

Places > Computer > File System > Host

Can you see the drives there now?

---

### Post by branko.savic on 2011-03-18
> **Rubi1200 said:**
> What happens if you do this?

Places > Computer > File System > Host

Can you see the drives there now?

No, I see only the c: drive and all windows folders!

---

### Post by branko.savic on 2011-03-18
Any other suggestions?

---

### Post by Rubi1200 on 2011-03-19
> Any other suggestions? 	
Yes.

After consulting with another forum member, it seems that you may need dmraid installed, although I am not entirely sure this will work.

```
sudo apt-get install dmraid
```

Hopefully, after rebooting you should be able to see the RAID drives.

---

### Post by branko.savic on 2011-03-19
> **Rubi1200 said:**
> Yes.

After consulting with another forum member, it seems that you may need dmraid installed, although I am not entirely sure this will work.

```
sudo apt-get install dmraid
```

Hopefully, after rebooting you should be able to see the RAID drives.

I tried that, but got the message that I already have the latest version of dmraid installed!

After restarting there are still no raid drives to be found!

---

### Post by branko.savic on 2011-03-19
I was thinking... could the problem be that I have installed ubuntu trough wubi/windows 7 instead of a clean install!?

I was thinking about testing so everything works on my system before getting rid of windows and making a clean ubuntu install, but I really dont want to go trough all that trouble without knowing that everything works!

So what do you think, is wubi the problem, or could it be something else?

Thanks for all your help!

---

### Post by Rubi1200 on 2011-03-20
I don't know if this is a Wubi issue. Theoretically, if dmraid is installed you *should* be able to see those drives.

I am going to ask another forum member, ronparent, to take a look and offer some perspectives.

Meantime, please post the results of the boot info script I asked for previously as this will help us determine the current state of your setup.

Thanks.

---

### Post by Rubi1200 on 2011-03-20
> **branko.savic said:**
> Any other suggestions?
Hi, after consulting with ronparent, we would like you to try the following:

```
sudo apt-get install kpartx
```

After a reboot, see if the drives show up. If not, we will have to keep investigating and see if there are other possibilities.

Thanks.

---

### Post by branko.savic on 2011-03-20
> **Rubi1200 said:**
> Hi, after consulting with ronparent, we would like you to try the following:

```
sudo apt-get install kpartx
```

After a reboot, see if the drives show up. If not, we will have to keep investigating and see if there are other possibilities.

Thanks.

Installed kpartx rebooted and still nothing!

Anyway here are the results from the boot info script!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/mapper/isw_cjaaibabha_Raid10

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

isw_cjaaibabha_Raid101: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

isw_cjaaibabha_Raid102: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   293,044,223   292,837,376   7 HPFS/NTFS


Drive: isw_cjaaibabha_Raid10 ___________________ _____________________________________________________

Disk /dev/mapper/isw_cjaaibabha_Raid10: 2000.4 GB, 2000404348928 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cjaaibabha_Raid101                  1 4,294,967,295 4,294,967,295  ee GPT

/dev/mapper/isw_cjaaibabha_Raid101 ends after the last sector of /dev/mapper/isw_cjaaibabha_Raid10

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/isw_cjaaibabha_Raid101          2,048 1,953,519,615 1,953,517,568 Linux or Data
/dev/mapper/isw_cjaaibabha_Raid102  1,953,519,616 3,907,035,135 1,953,515,520 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bf272d68-020f-443d-9c5b-d1bd4ff3d869   ext4                                     
/dev/mapper/isw_cjaaibabha_Raid10: PTTYPE="gpt" 
/dev/sda1        AE06B59E06B5684B                       ntfs       System Reserved               
/dev/sda2        405ABA445ABA370E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd                                                isw_raid_member                               
error: and: No such file or directory
error: /dev/mapper//dev/sdb:: No such file or directory
error: /dev/mapper//dev/sdc:: No such file or directory
error: /dev/mapper//dev/sdd:: No such file or directory
error: /dev/mapper/isw_cjaaibabha_Raid101: No such file or directory
error: /dev/mapper/isw_cjaaibabha_Raid102: No such file or directory
error: discovered: No such file or directory
error: formats: No such file or directory
error: "isw": No such file or directory
error: isw)!: No such file or directory
error: "pdc": No such file or directory
error: "sil": No such file or directory
error: (using: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cjaaibabha_Raid10

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 405aba445aba370e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 405aba445aba370e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 405aba445aba370e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 405aba445aba370e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set ae06b59e06b5684b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   9.1GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/initrd.img-2.6.35-28-generic
  13.2GB: boot/vmlinuz-2.6.35-22-generic
  13.2GB: boot/vmlinuz-2.6.35-28-generic
   1.4GB: initrd.img
   1.0GB: initrd.img.old
  13.2GB: vmlinuz
  13.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on isw_cjaaibabha_Raid101


Unknown BootLoader  on isw_cjaaibabha_Raid102



=======Devices which don't seem to have a corresponding hard drive==============

sdd: "pdc" and "isw" formats discovered (using isw)! sdd: "sil" and "isw" formats discovered (using isw)! sdc: "pdc" and "isw" formats discovered (using isw)! sdb: "pdc" and "isw" formats discovered (using isw)! sdb: "sil" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: only one argument allowed for this option
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
hexdump: /dev/mapper/isw_cjaaibabha_Raid101: No such file or directory
hexdump: /dev/mapper/isw_cjaaibabha_Raid101: No such file or directory
hexdump: /dev/mapper/isw_cjaaibabha_Raid102: No such file or directory
hexdump: /dev/mapper/isw_cjaaibabha_Raid102: No such file or directory
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: only one argument allowed for this option
```

Thank you for helping me out, I really appreciate it!

---

### Post by ronparent on 2011-03-20
Have you run the 10.10 live cd? If so, are the paid partitions visible? There is definitely a problem showing up from wherever you ran the boot script. Dmraid does support level 5 for isw. 

In your installed system, what are the results when you type **sudo dmraid -ay**.

---

### Post by branko.savic on 2011-03-20
> **ronparent said:**
> Have you run the 10.10 live cd? If so, are the paid partitions visible? There is definitely a problem showing up from wherever you ran the boot script. Dmraid does support level 5 for isw. 

In your installed system, what are the results when you type **sudo dmraid -ay**.

I run the scrips from the live cd, and I could not find the raid from there!

the results from "sudo dmraid -ay" :


```
/dev/sdd: "pdc" and "isw" formats discovered (using isw)!
/dev/sdd: "sil" and "isw" formats discovered (using isw)!
/dev/sdc: "pdc" and "isw" formats discovered (using isw)!
/dev/sdb: "pdc" and "isw" formats discovered (using isw)!
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
RAID set "isw_cjaaibabha_Raid10" already active

```

---

### Post by ronparent on 2011-03-20
Sorry I couldn't get right back to you. If "isw_cjaaibabha_Raid10" is already active, you should be able to find the raid symbolic links in /dev/mapper. Do you find anything there? You should also have links /dev/dm-0 and dm-1. These all are the handles by which the raid file systems are accessed. Your output with the sudo dmraid -ay paremeters is pretty much what would be expected. So we go from there.

---

### Post by branko.savic on 2011-03-20
> **ronparent said:**
> Sorry I couldn't get right back to you. If "isw_cjaaibabha_Raid10" is already active, you should be able to find the raid symbolic links in /dev/mapper. Do you find anything there? You should also have links /dev/dm-0 and dm-1. These all are the handles by which the raid file systems are accessed. Your output with the sudo dmraid -ay paremeters is pretty much what would be expected. So we go from there.

In /dev/mapper I can find the following two files:
Control and isw_cjaaibabha_Raid10

The files have a big red X sign on the top left!

I am able to find /dev/dm-0 (Also has a big red x) but I can not find the dm-1!

---

### Post by ronparent on 2011-03-20
I don't know what the red x symbology stands for but mine display the same way and all the partitions are readable. More worrisome is that the symbolic links for your partitions don't show. Although dmraid supposedly support raid5 for some reason it is not reading yours? If it were, the symbolic partition links would show and be mountable and thus readable once the raid was activated. It doesn't at all look promising but what do the commands **sudo dmraid -r** and **sudo dmraid -s** produce?

Something I just noted: the partitions were not noted when dmraid was used to activate the raid. If not acted on they are not readable. What also is the output of s**udo blkid**?

---

### Post by ronparent on 2011-03-21
A google search indicates that at one time (in the recent past) dmraid did not support level 5 RAIDs but needed a kernel patch labeled dm-raid45 to do so. It is unclear what the current status is. Your system doesn't seem to support raid 5 but dmraid appears to claim raid 5 support?

Since this is the case for the 10.10 live cd it is a distribution problem not unique to wubi. I would suggest submitting a bug report against dmraid and the current kernel to see what falls out. At the least it should get the attention of someone more directly connected to the technical details. I would do it myself but I cannot observe the problem first hand and it would not be credible. Post if you need help.

edit: Ive found 8 bug reports on the launchpad search **dmraid + raid 5 + maveric + isw**. You might check them out and see if you can add commments to any of them.

---

### Post by branko.savic on 2011-03-21
> **ronparent said:**
> I don't know what the red x symbology stands for but mine display the same way and all the partitions are readable. More worrisome is that the symbolic links for your partitions don't show. Although dmraid supposedly support raid5 for some reason it is not reading yours? If it were, the symbolic partition links would show and be mountable and thus readable once the raid was activated. It doesn't at all look promising but what do the commands **sudo dmraid -r** and **sudo dmraid -s** produce?

Something I just noted: the partitions were not noted when dmraid was used to activate the raid. If not acted on they are not readable. What also is the output of s**udo blkid**?

Sorry I could not get back to you sooner, here are the results from the commands you asked about!

sudo dmraid -r

```
/dev/sdd: "pdc" and "isw" formats discovered (using isw)!
/dev/sdd: "sil" and "isw" formats discovered (using isw)!
/dev/sdc: "pdc" and "isw" formats discovered (using isw)!
/dev/sdb: "pdc" and "isw" formats discovered (using isw)!
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
/dev/sdd: isw, "isw_cjaaibabha", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdc: isw, "isw_cjaaibabha", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_cjaaibabha", GROUP, ok, 1953525166 sectors, data@ 0
```

sudo dmraid -s

```
/dev/sdd: "pdc" and "isw" formats discovered (using isw)!
/dev/sdd: "sil" and "isw" formats discovered (using isw)!
/dev/sdc: "pdc" and "isw" formats discovered (using isw)!
/dev/sdb: "pdc" and "isw" formats discovered (using isw)!
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
/dev/sdb: "sil" and "isw" formats discovered (using isw)!
*** Group superset isw_cjaaibabha
--> Active Subset
name   : isw_cjaaibabha_Raid10
size   : 3907039744
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 3
spares : 0
```

sudo blkid

```
/dev/loop0: UUID="bf272d68-020f-443d-9c5b-d1bd4ff3d869" TYPE="ext4" 
/dev/sda1: LABEL="System Reserved" UUID="AE06B59E06B5684B" TYPE="ntfs" 
/dev/sda2: UUID="405ABA445ABA370E" TYPE="ntfs" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd: TYPE="isw_raid_member" 
```

I also went into windows 7 just to verify that the raid is indeed working, and it does! However I noticed that the partition type for the raid 5 is GPT, if I remember correctly I had to set it to GPT in order for windows to handle partitions/disks larger then 2TB! Could that be the problem? Can linux read GPT partitions?

Thanks!

---

### Post by branko.savic on 2011-03-21
> **ronparent said:**
> A google search indicates that at one time (in the recent past) dmraid did not support level 5 RAIDs but needed a kernel patch labeled dm-raid45 to do so. It is unclear what the current status is. Your system doesn't seem to support raid 5 but dmraid appears to claim raid 5 support?

Since this is the case for the 10.10 live cd it is a distribution problem not unique to wubi. I would suggest submitting a bug report against dmraid and the current kernel to see what falls out. At the least it should get the attention of someone more directly connected to the technical details. I would do it myself but I cannot observe the problem first hand and it would not be credible. Post if you need help.

edit: Ive found 8 bug reports on the launchpad search **dmraid + raid 5 + maveric + isw**. You might check them out and see if you can add commments to any of them.

If you think that this is strictly a wubi problem, I have no problem making a clean ubuntu install!

However I wanted to be certain that everything works as it should before I completly wiped my system!

Thanks!

---

### Post by Rubi1200 on 2011-03-21
I don't think this is a Wubi issue at all. Could it be related to GPT? Perhaps. Wait until ronparent responds though.

---

### Post by srs5694 on 2011-03-21
> **branko.savic said:**
> I also went into windows 7 just to verify that the raid is indeed working, and it does! However I noticed that the partition type for the raid 5 is GPT, if I remember correctly I had to set it to GPT in order for windows to handle partitions/disks larger then 2TB! Could that be the problem? Can linux read GPT partitions?

Yes, Linux can handle GPT just fine -- better than Windows, in fact. There are some issues with the combination of RAID and GPT under Linux, but my impression is that these relate to building a Linux software RAID array from GPT disks, not in using GPT on a RAID array. My knowledge of RAID, and particularly of motherboard-based software RAID, is limited, though, so I can't rule out the possibility of some sort of RAID/GPT interaction in your case.

---

### Post by ronparent on 2011-03-21
To restate the problem: It appears that GPT partitions created by Window are not discoverable by dmraid! Because the problem is present with the live cd it in not likely a wubi problem. Further, the routines in the BootScript find the partitions but cannot identify their file systems. This probably should be brought to the attention of the developers because it requires resources out of reach to most of the users to investigate and fully define. It is also is a regression of sorts and will likely become more prevalent as the 'large' drives come more in use, especially in raid5 large partitions. 

Among us we have probably taken this as far as we can go without their help. Again I suggest the OP submit a bug report. We can support him with suggestions but I don't think it would be useful for us to join in without independent verification. What do you all think?

---

### Post by branko.savic on 2011-03-21
> **ronparent said:**
> To restate the problem: It appears that GPT partitions created by Window are not discoverable by dmraid! Because the problem is present with the live cd it in not likely a wubi problem. Further, the routines in the BootScript find the partitions but cannot identify their file systems. This probably should be brought to the attention of the developers because it requires resources out of reach to most of the users to investigate and fully define. It is also is a regression of sorts and will likely become more prevalent as the 'large' drives come more in use, especially in raid5 large partitions. 

Among us we have probably taken this as far as we can go without their help. Again I suggest the OP submit a bug report. We can support him with suggestions but I don't think it would be useful for us to join in without independent verification. What do you all think?

I want to thank you all for the assistance you have provided, and I see no option then to do as you say and submit a bug report!

Where would be the best place to submit the bug report so it will be investigated and hopefully solved as soon as possible?

Also, with the information provided so far, how do you think that a proper bug report should look like?

Once again, thank you all for your help!

---

### Post by Rubi1200 on 2011-03-21
I agree with ronparent that this is likely not a Wubi specific issue and that it may have to do with the large drive you are using.

I also suggest filing a bug report:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Provide as much information as possible about your setup, specifications etc., including linking to this thread.

---

### Post by BBUCommander on 2011-03-31
You are right that dmraid does not by handle GPT by itself.  However, if you install kpartx and use the command

```
sudo kpartx -a /dev/mapper/**xxx**
```

where **xxx** is your RAID device, then the GPT table will be mapped for you.

Of course, this assumes that you activated the RAID array using dmraid -ay and that the drive was successfully mapped to /dev/mapper.

You should then be able to manually mount the partitions produced in /dev/mapper via the following:

```
sudo mount /dev/mapper/xxx**1** /media/**mountpoint**
```

where **mountpoint** is a folder you created in /media and the **1** at the end of xxx**1** can be replaced with whatever the order of your partition is amongst other partitions on the same disk (see /dev/mapper for available partitions).

As an example, I do the following for my Intel RAID 5 partition named 'Fire': 

```
 
sudo dmraid -ay
ls /dev/mapper
 [I]control
 isw_dfgcebfjia_RAID5Fire
 ...[/I]
sudo kpartx -a /dev/mapper/isw_dfgcebfjia_RAID5Fire
ls /dev/mapper
 [I]control
 isw_dfgcebfjia_RAID5Fire
 isw_dfgcebfjia_RAID5Fire1
 isw_dfgcebfjia_RAID5Fire2[/I]
sudo mount /dev/mapper/isw_dfgcebfjia_RAID5Fire2 /media/Fire

``` 

Now my drive contents are mounted to /media/Fire and all is well.  The only bad news is that you will have to run this every time you reboot.  You could get around this by create a shell script and calling it every time the computer reboots.  Attached is such a script.  If you add a line calling it from your /etc/rc.local file (before the exit 0 line) you will have your mapping done automatically at boot.  I also left a couple examples of how I mount my partitions as a reference.

BTW, an alternative approach that is good for ease of testing is to launch gparted (available in general repository, sudo apt-get install gparted) and then run 'ls /dev/mapper' to see if the maps ending in a number appear.  Gparted should map all your RAID partitions and you should now be able to mount them using the above method.

Hope this helps.

---

