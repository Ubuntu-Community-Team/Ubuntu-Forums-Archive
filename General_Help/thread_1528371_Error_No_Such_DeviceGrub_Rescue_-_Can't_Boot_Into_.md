---
title: "Error: No Such Device/Grub Rescue - Can't Boot Into Anything!"
date: 2010-07-10
forum: General Help
---

### Post by iMessedUp on 2010-07-10
Hi everyone.

I decided I wanted to try out Linux for a while on my primary laptop - sort of. I chose to install it to my Samsung 640GB drive that is enclosed in a NexStar CX enclosure. Bad idea!

Everything went fine at first, I created a 10GB ext4 partition to install Ubuntu on, and a 4GB swap partition. Everything seemed to install find until it was time to restart. On restart I chose to boot from the external "USB Hard Disk" which triggers a screen showing "Windows is loading files..." and a progress bar that fills twice before directing back to the HP startup/POST screen and then not long after a black screen that shows the following message;

error: no such device: 59477a79-f8aa-44f2-9687-c17be4e944b4
grub rescue>

The worst part is that I can't even boot back into the Notebook hard drive, where XP is installed. I guess it's something to do with a bootloader problem?

Anyways, I'm now desperately searching for help on how to recover access back to XP, as well as successfully boot into Ubuntu from the external hard drive.

All help is very much appreciated, I eagerly await replies.

---

### Post by oldfred on 2010-07-10
Welcome to the forum.

Just to be sure what is where and with external plugged in.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by iMessedUp on 2010-07-10
> **oldfred said:**
> Welcome to the forum.

Just to be sure what is where and with external plugged in.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
For some reason I can't seem to boot into the LiveCD... It's not showing in the boot menu anymore. 

Is there nothing I can do from the "grub rescue" that is coming up? I'll keep trying with the liveCD.

---

### Post by iMessedUp on 2010-07-10
Alright, I got into the LiveCD.

Here are the results from running the Boot Info script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,225,359   117,225,297   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848 1,175,990,129 1,175,783,282   7 HPFS/NTFS
/dev/sdb3       1,175,990,272 1,195,739,135    19,748,864  83 Linux
/dev/sdb4       1,195,741,182 1,203,771,391     8,030,210   5 Extended
/dev/sdb5       1,195,741,184 1,203,771,391     8,030,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B870618870614E66                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        44D49766D497594E                       ntfs       System Reserved               
/dev/sdb2        E0ACA0C2ACA09516                       ntfs                                     
/dev/sdb3        59477a79-f8aa-44f2-9687-c17be4e944b4   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        19aca707-524b-4190-9929-a9b21be48b14   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 59477a79-f8aa-44f2-9687-c17be4e944b4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,3)'
search --no-floppy --fs-uuid --set 59477a79-f8aa-44f2-9687-c17be4e944b4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 59477a79-f8aa-44f2-9687-c17be4e944b4
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=59477a79-f8aa-44f2-9687-c17be4e944b4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 59477a79-f8aa-44f2-9687-c17be4e944b4
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=59477a79-f8aa-44f2-9687-c17be4e944b4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 59477a79-f8aa-44f2-9687-c17be4e944b4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set 59477a79-f8aa-44f2-9687-c17be4e944b4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b870618870614e66
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 44d49766d497594e
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=59477a79-f8aa-44f2-9687-c17be4e944b4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=19aca707-524b-4190-9929-a9b21be48b14 none            swap    sw              0       0

=================== sdb3: Location of files loaded by Grub: ===================


 604.8GB: boot/grub/core.img
 605.4GB: boot/grub/grub.cfg
 605.5GB: boot/initrd.img-2.6.32-21-generic
 605.4GB: boot/vmlinuz-2.6.32-21-generic
 605.5GB: initrd.img
 605.4GB: vmlinuz
```

EDIT: Not sure if it effects anything, but I'm not running Windows 7. I used to be running Windows 7, but since retired the hard drive to being a storage solution by making it external.

---

### Post by oldfred on 2010-07-10
You cannot boot the external as grub2 installed to the internal. It does that unless you use the advanced button on the last install screen where it says ready to install.

Are you still using XP on the internal? Either grub or the script often reports the drive incorrectly but it should work. On my system the  grub install in sda says partition 7 but sda only has 3 partitions but it does correctly boot sdc7.

I would install grub2 to the external sdb and if still using XP install a windows boot loader to sda. If you boot from sda the 60GB drive does it boot ok?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

or
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR boot loader.

---

### Post by iMessedUp on 2010-07-10
> **oldfred said:**
> You cannot boot the external as grub2 installed to the internal. It does that unless you use the advanced button on the last install screen where it says ready to install.

Are you still using XP on the internal? Either grub or the script often reports the drive incorrectly but it should work. On my system the  grub install in sda says partition 7 but sda only has 3 partitions but it does correctly boot sdc7.

I would install grub2 to the external sdb and if still using XP install a windows boot loader to sda. If you boot from sda the 60GB drive does it boot ok?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

or
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR boot loader.
The worst part is I clicked that Advanced button, just to look, my mistake...

Yes, I am using XP on the internal, but I do not have access to it because of this problem. I assume the internal (60GB) drive is "SDA"? If so, then no I can not boot from it without getting that error right now. I will try and install Grub2 to the external drive, and re-install the XP bootloader to the internal drive. 

Thanks for the link for installing the XP bootloader, do you have one for installing GRUB2 to the external drive?

I very much appreciate your help.

---

### Post by iMessedUp on 2010-07-10
Just tried to install the XP bootloader from the CD and got this...

"Setup did not didn't any hard disk drives installed in your compuer.. blah blah make sure they're connected, etc."

That's not good. The information on the XP partition is very important. I figure this is a MBR/Boot issue, but I'm pretty nervous right now. 

As for installing Grub onto the external drive, the guide at SourceForge begins the guide with "Boot into Linux". Can't do that. I'll try on the LiveCD.

---

### Post by oldfred on 2010-07-10
The link on restoring all boot loaders will work. You just want to install to sdb , but sometimes externals mount as another drive (sdf or sdd) so you still should check with fdisk.

Install from LiveCD install on sdb3 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb3 if not correct, and/or even sdb :
```
sudo fdisk -l
sudo mkdir /mnt/sdb3
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

```

Do not install to sdb3 the partition, but sdb the drive's MBR.

---

### Post by iMessedUp on 2010-07-10
> **oldfred said:**
> The link on restoring all boot loaders will work. You just want to install to sdb , but sometimes externals mount as another drive (sdf or sdd) so you still should check with fdisk.

Install from LiveCD install on sdb3 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb3 if not correct, and/or even sdb :
```
sudo fdisk -l
sudo mkdir /mnt/sdb3
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

```Do not install to sdb3 the partition, but sdb the drive's MBR.
I apologize for being so ignorant, but could you clarify the names of the drives, like what exactly sdb3 is? Is it the partition I previously tried to install to?

Also, you are telling me to install Ubuntu again, but this time correcting my mistake of installing GRUB2 in the wrong place? 

Again, I apologize.

---

### Post by iMessedUp on 2010-07-10
Alright, I re-installed Ubuntu to sdb3, and installed the boot loader to sdb1. It didn't work. Writing this I am thinking, was I suppose to install the boot loader the same place I installed Ubuntu, in sdb3? 

When I get Ubuntu working externally, do I only need to install the XP bootloader to get everything back to working condition? 

I'm freaking out!..

---

### Post by oldfred on 2010-07-10
No, you do not need to install again. 

Just install the part of grub that goes into the MBR to allow the system to boot. Some, by mistake install to the partition, sdb3 not the MBR sdb. 

The MBR is the first sector of a hard drive reserved for boot info - sda, sdb etc. It is not part of any partition.

Partitions always have numbers at the end sda1, sda2, sdb1 etc. The start of every partition (PBR or boot sector) is also reserved for boot info and is used by windows, but not normally used by grub.

If on boot with the liveCD the drives are the same as reported in the boot info script, the sda is your internal 60GB drive and sdb is the 640GB drive.

If you installed lilo boot loader to sda, it does give error messages because it does not see the rest of lilo. But lilo works just like windows in finding a active (boot flag) partition and jumping to the boot sector of that partition. So it will boot windows just like windows does. We just wanted the boot loader in the MBR of the windows drive sda to boot windows. And we want grub2 in the MBR of sdb to boot the 640GB drive.

Then in your BIOS change boot order to boot the external first, so it boots grub if the external is connected. If not it will default to the internal drive and boot windows.

---

### Post by iMessedUp on 2010-07-10
OK, let's simplify this down to a short guide that I will try in about half an hour.

1. Install lilo

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR boot loader.

**After installing lilo I should be able to boot into Windows?**

2. install the part of grub that goes into the MBR to allow the system to boot

**How do I do this?**

3. I am now able to boot into both OSs, correct? Adjust BIOS settings to boot into Ubuntu if external is connected, if not boot windows.

---

### Post by iMessedUp on 2010-07-10
Alright, I am now in my XP!

I used the lilo commands through terminal, on the Live CD. 

Now all I need to to do what I had been trying to do when I caused this whole mess - run Ubuntu from my external drive. Now that I have it installed on there, from what oldfred has told me I need to install GRUB2 boot loader on to it. 

How? I don't know :)!

---

### Post by oldfred on 2010-07-11
See post #8 on reinstalling grub2 to sdb. Do not install to sdb3. You have to tell grub that the install is in sdb3 with the mount commands and then you install to sdb (no number at the end).

---

### Post by iMessedUp on 2010-07-11
Alright, I booted into the LiveCD, and did these commands;

```
sudo fdisk -l
sudo mkdir /mnt/sdb3
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

```

Terminal said installation was successful.

I rebooted and set the external drive as the boot drive, booted and got this error:

error: unknown filesystem
grub rescue>

:frown:

---

### Post by oldfred on 2010-07-11
Will this let you boot? Is it seeing the external as sdb or something else?

#show you the available partitions
ls
#look for boot files on the partitions
ls (hd1,3)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition s/b 1,3
insmod ext2
set root=(hd1,3)
# in the next command sdb3 represents (hd1,3), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sdb3 ro 
initrd /initrd.img
boot
Install grub to MBR:
sudo grub-install /dev/sdb
sudo update-grub

---

### Post by iMessedUp on 2010-07-11
Thanks oldfred,

I'm going to try that in about 20 minutes, have to step away for a minute.

Just to make sure, none of those commands will effect any of the other partitions on the external drive? Everything else will be safe?

---

### Post by oldfred on 2010-07-11
All those commands to boot are just from a grub rescue command to try to get it to boot. The only command that writes anything is the grub install to sdb which you already have done but we want  to try again after you boot to see it that works better.

---

### Post by iMessedUp on 2010-07-11
Partition (hd1,3) wasn't listed after the ls command. I tried each of the listed partitions for step 2, but of course none of them booted. 

Would it be easier for me to delete the linux partition and delete what parts of GRUB2 I do have, then just re-install? If so then how would I cleanly remove Ubuntu and GRUB? And what do I have to make sure I do to avoid the mess up this has caused?

---

### Post by oldfred on 2010-07-11
I am surprised it does not show 1,3 as one of the partitions.

We like to spend days even weeks fixing things, sometimes just for the satisfaction of fixing it.:smile:

I installed from a USB drive in 9 minutes to partitions I had already set up. It took longer to download all the updates. Sometimes reinstalling is the better choice. Just be sure to use the advanced button to install grub to the MBR of sdb or whatever the external is seen as.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by iMessedUp on 2010-07-12
> **oldfred said:**
> I am surprised it does not show 1,3 as one of the partitions.

We like to spend days even weeks fixing things, sometimes just for the satisfaction of fixing it.:smile:

I installed from a USB drive in 9 minutes to partitions I had already set up. It took longer to download all the updates. Sometimes reinstalling is the better choice. Just be sure to use the advanced button to install grub to the MBR of sdb or whatever the external is seen as.

[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")
Alright, I made sure I did that. 

:confused:

Still got the unknown filesystem error! I did the ls command, still no 1,3. Could it be that my NTFS partitions is in front of the ext4 and swap partition? If so, how could I move them?

This is taking  a lot more than 9 minutes!

---

### Post by oldfred on 2010-07-12
Lets rerun the boot script, but frankly I do not expect to see anything. I am running out of ideas.

---

### Post by iMessedUp on 2010-07-12
I'm knee deep in gParted. 

Deleted the 100MB "System Reserved" partition left over from Win 7, split the 560GB partition in half, I'm going to copy the data from the half with the data, to the half without, them reformat it to NTFS, and then try and make the linux partition at the start of the drive.

gParted has been working away at shrinking the partition in half for a good hour and a half, hope it's almost done...

EDIT: It's been 3 hours, now it says 4.5 hours left. :'(

---

### Post by iMessedUp on 2010-07-12
gParted will be finished in half an hour. It's been over 10 hours...

I've got a friends external drive that I am going to use to back up all my important stuff of the external I'm trying to boot Ubuntu on, format my entire drive in NTFS, then try this whole thing again.

I think the problem was I had a Win 7 installation on the drive in my external previously, I completely forgot about this and just deleted the Windows system files rather than format the drive. Could this have  caused this mess? 

Anyways, the first partition I create will be the linux partition, then I will try installing Ubuntu again. Hopefully, it's successful and then I copy all my info back to a NTFS partition, and all is good.

Question : Does the Ubuntu partition have to be the first partition?

---

### Post by oldfred on 2010-07-13
No Ubuntu does not have to have its root on any specific partition. Of the four primary or three primary and one extended with many logical partitions, windows has to boot from a primary partition. 

If you ever want to install windows then it would be best to make a NTFS partition first. Some BIOS will not let you boot unless you have a boot flag on a primary partition (sda1-4) as it checks before it lets windows boot. Of course grub does not need the boot flag but it is good practice to have a boot flag on a primary partition.

---

### Post by iMessedUp on 2010-07-13
So....

I'm posting this from my Ubuntu install, on my external hard drive! :p:D

My guess on what created this monster, that caused probably close to a full 24 hours of cleanup, is I never reformatted after I sold my Windows 7 PC, but kept the hard drive, I only deleted the system files. This means that pieces of the boot loader remained, and weren't cleaned out until I formatted the entire drive. I guess the Win 7 bootloader out muscled GRUB? 

Anyways, I'm posting from Ubuntu now. All that's left is to copy my files back onto the external drive. I have already made an extended partition (with NTFS) for my files, so that both Linux, and Windows PCs can read the files.

Now, I'm going to have great pleasure in pressing the solve button!

Thank you very much for all of your help oldfred!

---

### Post by agentfortyseven on 2010-11-01
I had a similiar problem too..

---

