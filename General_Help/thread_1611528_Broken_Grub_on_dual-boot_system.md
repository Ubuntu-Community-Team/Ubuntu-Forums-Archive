---
title: "Broken Grub on dual-boot system"
date: 2010-11-02
forum: General Help
---

### Post by Maggar on 2010-11-02
I installed Win7 after Ubuntu (10.10). I attempted to reload grub so that I would be able to run them dual boot and now I can't load anything. I followed the guide here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and went threw it a couple of times now to make sure it wasn't user error. 

I am using a live cd from 10.04 because it's the only one I have. Any chance that's why it isn't working properly? I wouldn't think so, but I assume that it's possible. 

If that is the case; Any way to solve it without using the live cd? I cannot burn a new disk because I have to boot from disk to use my computer right now.

If that isn't the problem; Any other ideas on how to fix this? I just get a flashing cursor on a blank screen when I try to load.

---

### Post by stinkeye on 2010-11-02
Try this guide...[**_[COLOR="DarkRed"]How to restore the Ubuntu/XP/Vista/7 bootloader[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1014708")

**Note the last command when reinstalling grub if windows 
is on /dev/sda1 you only use /dev/sda to install to the drive not a partition.

And you must substitue for what you find with 
```
sudo fdisk -l
```

This might explain it better
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9702777&postcount=5[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9702777&postcount=5")

---

### Post by rhoparkour on 2010-11-02
Hey man, I know your pain! Don't worry we just might get through this, could you post the exact output that you see when you reinstall grub? Just copy and paste the output of what you do, please post ALL of it. I would like to see if grub is actually installed.

It is a good time to back up any data you have in the computer, if you haven't already done so.

Edit: Totally forgot about that thread stinkeye, I was actually going to tell him to follow the same procedure, just easier and more complete to point straight to the source!

---

### Post by Maggar on 2010-11-02
Yep, still not doing anything for me. Let me walk step by step threw this and maybe I'm reading something wrong. 

I do ...
```
 sudo fdisk -l 
```And get the output:

```

/dev/sda1               1       50993   409600248+  83  Linux
/dev/sda2   *       50994       60144    73505407+   7  HPFS/NTFS
/dev/sda3           60145       60802     5278721    5  Extended
/dev/sda5           60145       60802     5278720   82  Linux swap / Solaris

```So I type:

```

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1

```Followed up by 
```

sudo grub-install --root-directory=/media/sda1 /dev/sda

```And I get the output 

```

Installation finished. No error reported.

```
Yet I still cannot boot correctly. Am I doing something obviously wrong that I'm not seeing?

---

### Post by garvinrick4 on 2010-11-02
Just so you tried this before going on. replace this in code;
```
sudo grub-install --recheck --root-directory=/media/sda1 /dev/sda
```run all the commands replacing this with other and this at end.
```
sudo umount /media/sda1
``` not a typo
If this works for you once you get into Ubuntu you have to.
```
sudo update-grub
```
will probe for other operating systems and put your windows in boot menu.

---

### Post by garvinrick4 on 2010-11-02
Boot flag still in Windows sda2 if you noticed. *

If that does not work run this in Live cd: download this script to Desktop
and then run code and will put a file on desktop post here.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by Maggar on 2010-11-02
I tried the advice you gave in your first post and received the exact same results as before.

I don't know what you want me to do with the output from the script, it seems like it may be too long to post on here.

---

### Post by garvinrick4 on 2010-11-02
copy and paste in this thread and then highlight whole thing and hit the # sign (code tags)
and will put in nice little box to scrowl thru. # sign in upper right of the message box.
Need to see it to fix problem.

---

### Post by Maggar on 2010-11-02
Nevermind, just attached it as a file.

EDIT: You replied while I was attaching hehe, I put it in code tags.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   819,202,544   819,200,497  83 Linux
/dev/sda2    *    819,202,545   966,213,359   147,010,815   7 HPFS/NTFS
/dev/sda3         966,215,678   976,773,119    10,557,442   5 Extended
/dev/sda5         966,215,680   976,773,119    10,557,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f4ff121f-d9c1-4702-8756-ab842991b349   ext4                                     
/dev/sda2        3F36933D74F15E62                       ntfs       Win7                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e599213f-ec7c-4460-a6c6-065a79342e56   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f4ff121f-d9c1-4702-8756-ab842991b349 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f4ff121f-d9c1-4702-8756-ab842991b349 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f4ff121f-d9c1-4702-8756-ab842991b349 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f4ff121f-d9c1-4702-8756-ab842991b349 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f4ff121f-d9c1-4702-8756-ab842991b349 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f4ff121f-d9c1-4702-8756-ab842991b349 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set f4ff121f-d9c1-4702-8756-ab842991b349
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f4ff121f-d9c1-4702-8756-ab842991b349 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e599213f-ec7c-4460-a6c6-065a79342e56 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
   2.1GB: boot/grub/grub.cfg
 116.1GB: boot/initrd.img-2.6.32-21-generic
  78.4GB: boot/initrd.img-2.6.32-25-generic
 116.0GB: boot/initrd.img-2.6.35-22-generic
 116.1GB: boot/vmlinuz-2.6.32-21-generic
 116.1GB: boot/vmlinuz-2.6.32-25-generic
 116.2GB: boot/vmlinuz-2.6.35-22-generic
 116.0GB: initrd.img
 116.0GB: initrd.img.old
 116.2GB: vmlinuz
 116.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by garvinrick4 on 2010-11-02
I do not see Windows in your config files at all. Let us get Windows to boot and then get Ubuntu to overwrite that. In your ubuntu live cd 

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Will give a few errors never mind we only need mbr

That should make you boot into Windows.
Let me know.
Your Ubuntu seems fine it is the Windows that seems to have the problem.

---

### Post by garvinrick4 on 2010-11-02
Without being able to boot into ubuntu you have not been able to update-grub to get
Windows in the config files. Might have to get into root of sda1 and run update-grub in
Live Cd.

---

### Post by Maggar on 2010-11-02
That worked, booted right up into windows without a problem. 
 
You mean something like doing a sudo update-grub after mounting and nav-ing into sda1? I can try that, it's starting to get late here though. I may just call it for the night in a little bit and try again after a nap. Just hate to walk away without getting it figured out first.

---

### Post by garvinrick4 on 2010-11-02
I think we have a handle on it now. Will have to chroot into Ubuntu and update-grub which means we will be in root of sda1 install and mount a few things and update the grub.
Just did it on my machine to make sure all is right. We can do tomorrow but at least we
know both installs are cool now it is just getting grub to install and update. Installing Windows after Ubuntu can be a pain but is OK. Let me know when you want commands.

---

### Post by Maggar on 2010-11-02
If you think you've got it figured out lets do it. I'd love to get this taken care of.

---

### Post by garvinrick4 on 2010-11-02
ok. put your grub back
in live cd
```
sudo mkdir /media/sda1
```
```
sudo mount /dev/sda1 /media/sda1
```
```
sudo grub-install --recheck --root-directory=/media/sda1 /dev/sda
```
```
sudo umount /media/sda1
```
Why you do that I will be writing the chroot commands

---

### Post by garvinrick4 on 2010-11-02
Copy and paste these one at a time will not take long.
```

Ok start from scratch nothing mounted; If already has the directory will say so.
[CODE]sudo mkdir /media/sda1
``````
sudo mkdir /media/sda1/proc
``````
sudo mkdir /media/sda1/dev
``````
sudo mkdir /media/sda1/etc
```                  ```
sudo mount /dev/sda1 /media/sda1
``````
sudo mount -o bind /proc /media/sda1/proc
```                      ```
sudo mount -o bind /dev /media/sda1/dev
```                    ```
sudo mount -o bind /dev/pts /media/sda1/dev/pts
```                      ```
sudo chroot /media/sda1
``````
update-grub
```[COLOR=#3465a4]after updates hit ctrl and d[/COLOR]
```
sudo umount /media/sda1/dev
``````
sudo umount /media/sda1/proc
``````
sudo umount /media/sda1/etc
``````
sudo umount /media/sda1
```Now boot back into harddrive into Ubuntu and for good measure.
```
sudo update-grub
```[/code][COLOR=#3465a4]
[/COLOR]

---

### Post by Maggar on 2010-11-02
When I tried to do 
```

sudo mount -o bind /pts/media/sda1/dev/pts

```I ended up with
```

mount: can't find /pts/media/sda1/dev/pts in /etc/fstab or /etc/mtab

```

---

### Post by garvinrick4 on 2010-11-02
ok go to next one: we want to get to the update-grub and get it to update it.
sudo chroot /media/sda1
then to next.

---

### Post by garvinrick4 on 2010-11-02
> **Maggar said:**
> When I tried to do 
```

sudo mount -o bind /pts/media/sda1/dev/pts

```I ended up with
```

mount: can't find /pts/media/sda1/dev/pts in /etc/fstab or /etc/mtab

```
That was my fault I have fixed the code.
```
sudo mount -o bind /dev/pts /media/sda1/dev/pts
```

---

### Post by Maggar on 2010-11-02
You did it! Got into Ubuntu, did a manual update and restarted quick. Everything is showing up now. Thank you very much. You put in waaaaaay more time than I ever could have asked for.

---

### Post by garvinrick4 on 2010-11-02
You are welcome. Now save the code for chrooting into a system given earlier; (under normal circumstances the commands your did at beginning would put grub in sda fine and could boot Ubuntu)
if you do this: before chroot command
```
sudo cp /etc/resolv.conf /media/sda1/ect/resolv.conf
```you will have internet; and this after chroot (chroot puts you in root do not need sudo)
```
apt-get -f install
``````
dpkg --configure -a
```will fix broken packages and this: to update system.
```
apt-get update
``````
apt-get upgrade
```Now you have most all commands to fix a broken install that you cannot boot into.

Have fun with Ubuntu and mark as Solved please in opening post under thread tools.

---

### Post by Maggar on 2010-11-02
Yep already ahead of you on the solved thing. Thank you again and have a great night. Time for some much needed sleep.

---

