---
title: "Install issues"
date: 2010-10-29
forum: General Help
---

### Post by pinnicle329 on 2010-10-29
After installing ubuntu it prompts a restart, so i allow it, naturally. After coming back up it immediately restarts the install from the beginning after loading the virtual environment. That's if the dvd is in. If I take the disc out at boot, i get (initramfs) unable to find a medium containting a live file system. 

I've tried 3 different downloads, on 4 different dvds now, i'm a little lost as to what i'm doing terribly wrong. So, here' some info

i7 930
asus p6t mobo
8gb corsair 
1tb WD caviar (windows 7 boot works fine)
500gb WD (failed ubuntu drive) 

64 bit install by the way

Thanks in advance for any advice! 

Cheers

---

### Post by Rubi1200 on 2010-10-29
Is the 500GB drive internal or external?

Do you have the ability in BIOS to choose which drive to boot and what order did you set it to when trying to install Ubuntu?

---

### Post by pinnicle329 on 2010-10-29
It's an internal. This bios will recognize the 500g just fine, however under boot options, the bios will not allow me to use the 500 as a boot drive right now, it only shows the cd/floppy/1tb as options currently. However, i think a fresh new CD burned at a lower speed did the trick. 

But... because i think the install worked correctly this time, i have another problem, one that's apparently pretty well known.

Grub seems to hate me, it boots to the grub recovery menu, so, i went from a working windows drive and a sketchy/non funtional ubuntu drive, now to a big hunk of metal with a bios. So, i've tried booting to the CD we'll see what happens from here. 

Any reccomendations on which boot to recover (grub, mbr) and how to do that would be appreciated :(

---

### Post by pinnicle329 on 2010-10-29
I should mention this is 10.10 too, i suppose.

---

### Post by Rubi1200 on 2010-10-29
Don't worry, we can fix this :)

Use the LiveCD and post the results from the boot-script linked at the bottom of my post.

The information will help us determine what is going on and make offering solutions easier.

Thanks.

---

### Post by pinnicle329 on 2010-10-29
Boy, this is fun!

Attached is a big wall of text! If you want me to repost in the body, let me know.

---

### Post by Rubi1200 on 2010-10-29
You have both a Wubi install on sda2 and on sdb1. Do you really need the Wubi install? I recommend booting into Windows and uninstalling it.
The next thing to do is reinstall GRUB, which is not installed: > No boot loader is installed in the MBR of /dev/sdbYou can do a simple reinstall using the first method here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

You need to mount the Ubuntu partition on sdb1 and install GRUB to the MBR of sdb.

Don't forget to run > sudo update-grub once you are back in Ubuntu.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
                       /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   937,164,799   937,162,752  83 Linux
/dev/sdb2         937,166,846   976,771,071    39,604,226   5 Extended
/dev/sdb5         937,166,848   976,771,071    39,604,224  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C8CCB57ACCB562FC                       ntfs       System Reserved               
/dev/sda2        72BCB748BCB7061F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        40a00b84-c92e-4625-83b4-9f22e20ac5e8   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        636911d3-3738-4a03-8b82-fc6056a6e8d0   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/40a00b84-c92e-4625-83b4-9f22e20ac5e8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/72BCB748BCB7061F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 40a00b84-c92e-4625-83b4-9f22e20ac5e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 40a00b84-c92e-4625-83b4-9f22e20ac5e8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 40a00b84-c92e-4625-83b4-9f22e20ac5e8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=40a00b84-c92e-4625-83b4-9f22e20ac5e8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 40a00b84-c92e-4625-83b4-9f22e20ac5e8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=40a00b84-c92e-4625-83b4-9f22e20ac5e8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 40a00b84-c92e-4625-83b4-9f22e20ac5e8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 40a00b84-c92e-4625-83b4-9f22e20ac5e8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c8ccb57accb562fc
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=40a00b84-c92e-4625-83b4-9f22e20ac5e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=636911d3-3738-4a03-8b82-fc6056a6e8d0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 124.6GB: boot/grub/core.img
 322.2GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 124.6GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
 124.6GB: vmlinuz
```

---

### Post by pinnicle329 on 2010-10-29
How does it look doc? 

Thanks again for helping out, I'll send you a small kitten doing something ridiculously cute as payment.

---

### Post by Rubi1200 on 2010-10-29
> **pinnicle329 said:**
> How does it look doc? 

Thanks again for helping out, I'll send you a small kitten doing something ridiculously cute as payment.
I just answered in the post above. 

No need for kittens, already have 2 cats. But thanks for the thought :)

Also, don't thank me yet, wait until everything is fixed!

---

### Post by pinnicle329 on 2010-10-29
How will i go about booting into windows?

---

### Post by Rubi1200 on 2010-10-29
> **pinnicle329 said:**
> How will i go about booting into windows?
I thought you could boot into Windows now?

Or do you mean once GRUB is installed?

If the latter, GRUB should pick up the Windows installation and offer you a choice between Ubuntu and Windows when the GRUB menu appears just after the BIOS/POST screen.

---

### Post by pinnicle329 on 2010-10-29
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script*.sh
bash: /home/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/ubuntu/downloads/boot_info_script*.sh
bash: /home/ubuntu/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/downloads/boot_info_script*.sh
bash: /home/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash _/Downloads/boot_info_script055*.sh
bash: _/Downloads/boot_info_script055*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Downloads/boot_info_script055.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Downloads
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4271327d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      121602   976657408    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e33c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       58336   468581376   83  Linux
/dev/sdb2           58336       60802    19802113    5  Extended
/dev/sdb5           58336       60802    19802112   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb1
mount: /dev/sdb1 already mounted or /media/40a00b84-c92e-4625-83b4-9f22e20ac5e8 busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/40a00b84-c92e-4625-83b4-9f22e20ac5e8
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ 


Already mounted... not mounted= confusion.

I leave the well being of my rig, in your hands my friend.

---

### Post by pinnicle329 on 2010-10-29
I cannot boot into windows.

---

### Post by Rubi1200 on 2010-10-29
Run the commands from the LiveCD like this (copy/paste):

```
sudo mount /dev/sdb1 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sdb
```If all goes well you should be able to boot into Ubuntu first (don't be surprised if you do not see Windows mentioned) and then run ```
sudo update-grub
``` in Ubuntu. This should pick up the Windows install. Reboot to see if it does.

EDIT: from what point in this whole story were you unable to boot Windows. If we need to reinstall the Windows bootloader, it needs to be done first, before installing GRUB. Please explain the current situation: can you boot anything?

---

### Post by pinnicle329 on 2010-10-29
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 


Installed, no update... /shrug

---

### Post by pinnicle329 on 2010-10-29
After i finally got ubuntu to finish the install to the secondary drive (maybe, this was after several attempts, on all previous attempts i was able to boot into windows)

After the last attempt, i got the grub error and was unable to boot to anything but the live cd.

I've been doing all of this posting from the live cd

---

### Post by Rubi1200 on 2010-10-29
Restart the computer with the LiveCD and then follow what I posted above UNLESS we need to fix the Windows booting issue first, in which case tell me and we will try and sort that out first.

From what I understand, the problem is GRUB related. Try the way I posted above (in post #14) and then we can reassess the situation.

---

### Post by pinnicle329 on 2010-10-29
I'm thinking we should try to work out windows first as this is my primary OS and I'd very much like to keep it healthy, and operable.

---

### Post by Rubi1200 on 2010-10-29
If you unplug the external drive, can you boot into anything?

---

### Post by pinnicle329 on 2010-10-29
It's an internal. But I can certainly try. 

To clarify, I've had a 1tb WD caviar since i built the rig. I run windows 7 on it.

I picked up a 500g WD for cheap yesterday, so i figured I'd give ubuntu a try on my desktop ( It runs flawlessly on my 8 year old laptop) 

So, no externals. The only bootables i have right now are the two internals and the live CD.

Would unplugging the drive really do anything? My limited knowledge and understanding is telling me Grub wrote over or otherwise killed the windows boot manager.

---

### Post by Rubi1200 on 2010-10-29
Sorry for the delayed response; having Internet issues here.

If you have made no changes since the last time we ran the script then yes, it seems that sda is the 1TB drive and sdb the second drive, correct?

And it looks like the Windows bootloader was wiped out. However, installing GRUB the way I suggested before should, theoretically, fix the problem as long as you set the 500GB drive as the first drive to boot from BIOS.

If you do not want that, then you need to reinstall the Windows bootloader on sda and find a solution for Ubuntu later. Do you have the Windows installation/recovery CD?

Instructions to restore here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by pinnicle329 on 2010-10-29
Well, I was afraid of that. I don't have the discs on me, they're actually at a different house, the bios doesn't show the 500g as a boot option, though it does recognize that it's there. I'm not sure why but i can play around with it a bit, perhaps ripping the 1tb out and setting the 500g in the primary sata port could fix that. I'll play around, and see what i can do there. Know of a way to get the windows boot repaired without the discs?

Edit: sda is the 1tb, sdb being the second 500g

---

### Post by Rubi1200 on 2010-10-29
Yes, there is a fix you can use from the LiveCD that installs a basic Windows-style bootloader.

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

it may show errors, but you can ignore them because we just want lilo on the MBR.

---

### Post by pinnicle329 on 2010-10-29
Fun new update, unplugged my primary hard drive, through the 500g into the primary sata port, and it boots to ubuntu in 2 seconds. Great boot time. So, now problems here now, but there's still the issue of my windows being dead. So at this point it's pretty much essential i get the repair disc?

Should i go ahead and run the script you posted? Or will that again, disable my 1 working os? haha... this is a fun process

---

### Post by Rubi1200 on 2010-10-29
> **pinnicle329 said:**
> Fun new update, unplugged my primary hard drive, through the 500g into the primary sata port, and it boots to ubuntu in 2 seconds. Great boot time. So, now problems here now, but there's still the issue of my windows being dead. So at this point it's pretty much essential i get the repair disc?

Should i go ahead and run the script you posted? Or will that again, disable my 1 working os? haha... this is a fun process

Hmm, on the one hand this is good news. Though how does Ubuntu boot when there was an issue (it seemed) with its bootloader?

As far as Windows is concerned, see my post above about installing lilo (but it assumes the 1TB is the first drive, which you just took out!)

But, from what I can tell, you need to sort out this issue (?) about BIOS recognizing the drives because that also seems to have caused some of these problems. Maybe update BIOS? Or change the master and slave jumpers?

In any event, the fix for lilo will get you back into Windows, but then what about Ubuntu?

There would be no harm running the boot-script again, and you can do it from within Ubuntu this time.

> haha... this is a fun processGlad you are having a good time :-)

---

### Post by pinnicle329 on 2010-10-29
> **Rubi1200 said:**
> Hmm, on the one hand this is good news. Though how does Ubuntu boot when there was an issue (it seemed) with its bootloader?

As far as Windows is concerned, see my post above about installing lilo (but it assumes the 1TB is the first drive, which you just took out!)

But, from what I can tell, you need to sort out this issue (?) about BIOS recognizing the drives because that also seems to have caused some of these problems. Maybe update BIOS? Or change the master and slave jumpers?

In any event, the fix for lilo will get you back into Windows, but then what about Ubuntu?

There would be no harm running the boot-script again, and you can do it from within Ubuntu this time.

Glad you are having a good time :-)

Not sure why or how it booted, but it certainly did, it's perfect. Which is peachy and all, just ran the grub update it was successful. 

No jumpers on the hard drives, the bios is updated to a point... the newest versions of this particular bios just added new intel chips, nothing else that i'm aware of, so i never bothered updating it, as my 930 works just fine.

Now, if i run the fix for lilo, without my 1tb in, will that only stop the ubuntu drive from working correctly? 

I'm just confused as to what the next step should be, are you finding this situation as goofy as i am?

---

### Post by Rubi1200 on 2010-10-29
Yes, this is a bit goofy, but take a deep breath.

If the 500GB drive now works with Ubuntu; great.

Let's try this:

Take it out and put the 1TB back in (but leave the 500GB out for the moment).

Then, assuming it won't boot because of the original problem with GRUB writing over the MBR there, use the LiveCD to install lilo as I posted.

This should give you Windows back.

Then, we need to find a solution that allows you to have BOTH drives in and boot from them both.

Or put the 1TB in where the 500 was and see if you can boot into either one. It may be that we can update-grub and it will pick the Windows install up?

What do you think?

---

### Post by pinnicle329 on 2010-10-29
Worth a shot! I'll try em both, see what happens.

---

### Post by pinnicle329 on 2010-10-29
m@m-System-Product-Name:~$ sudo apt-get install lilo
[sudo] password for m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 96 not upgraded.
Need to get 415kB of archives.
After this operation, 1,331kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main mbr amd64 1.1.10-2 [23.8kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main lilo amd64 1:22.8-8ubuntu1 [391kB]
Fetched 415kB in 1s (300kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 119608 files and directories currently installed.)
Unpacking mbr (from .../mbr_1.1.10-2_amd64.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

m@m-System-Product-Name:~$ liloconfig(8)
bash: syntax error near unexpected token `8'
m@m-System-Product-Name:~$ /sbin/lilo
Fatal: Cannot open: /etc/lilo.conf
m@m-System-Product-Name:~$ sudo lilo -M /dev/sda/mbr
Fatal: Cannot open /dev/sda/mbr: Not a directory
m@m-System-Product-Name:~$ 


That was the result of trying to run lilo

I get the grub error anytime the windows drive is set as disk0, as long ubuntu's hard drive is set at disk0, it will boot regardless of the windows disk being installed.

---

### Post by pinnicle329 on 2010-10-29
I can't read that well enough to decide if the install was a success or not... 

Should i throw the windows drive back into the disk0 spot and give it a try?

---

### Post by Rubi1200 on 2010-10-29
To be honest, I am not sure what you did here, but this looks wrong:
```
sudo lilo -M /dev/sda/mbr
```
It should have been this:
```
sudo lilo -M /dev/sda mbr
```

Also, you appear to have run this from within Ubuntu? I did say to do this from a LiveCD with the 1TB drive in and the Ubuntu drive out since it is Windows that won't boot not Ubuntu from what I understand.

In any event, it is late here and I need to get some sleep. I am not abandoning this and will ask someone else to take a look and offer advice.

---

### Post by pinnicle329 on 2010-10-29
Alright, i really appreciate all your help, you're a fantastic human being.  

Cheers

---

### Post by pinnicle329 on 2010-10-29
WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device aufs as the root          &#9474; 
 &#9474; filesystem device. This doesn't look to me like an "ordinary" block       &#9474; 
 &#9474; device. Either your fstab is broken and you should fix it, or you are     &#9474; 
 &#9474; using hardware (such as a RAID array) which this simple configuration     &#9474; 
 &#9474; program does not handle.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/. 

This is the nice message lilo config left me, not moving from here, because i'm totally and completely lost.
So, if anyone else sees this and has some insight, i'm all ears :guitar:

Thanks in advance, this community is amazing, by the way.

---

### Post by oldfred on 2010-10-29
You should not be fully installing lilo, just the MBR, but the error message seems to be that it is trying to install to the liveCD not sda?

The windows boot loader and the lilo boot loader in the MBR just look for the active partition (boot flag) and jump to additional boot code in the partition boot sector. If linux, then lilo would have code there, but since it is windows it just boots windows. (Grub does not use partition boot sector, normally).

So if lilo is installed to the MBR you should be able to boot windows on your windows drive.

More info on how windows works:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by pinnicle329 on 2010-10-30
I turned my pc on as i was going to take a shower, come back, and windows is booted...

I don't even know which way is up anymore, but thanks, and i don't really plan on screwing with this again for a while... today was enough troubleshooting to last me a few weeks.

Thanks to everyone who helped me.

---

### Post by Quackers on 2010-10-30
If your problem is solved will you please mark the thread as solved with the Thread Tools near the top of the page. It may help others. Thanks.

---

### Post by Rubi1200 on 2010-10-30
> **pinnicle329 said:**
> I turned my pc on as i was going to take a shower, come back, and windows is booted...

I don't even know which way is up anymore, but thanks, and i don't really plan on screwing with this again for a while... today was enough troubleshooting to last me a few weeks.

Thanks to everyone who helped me.
I am glad you got something sorted out, it seems.

It might be helpful if you could run the boot-script again and post the results as before.

---

