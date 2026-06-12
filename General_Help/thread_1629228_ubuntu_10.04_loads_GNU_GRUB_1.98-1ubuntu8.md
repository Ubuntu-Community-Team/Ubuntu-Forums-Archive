---
title: "ubuntu 10.04 loads GNU GRUB 1.98-1ubuntu8"
date: 2010-11-23
forum: General Help
---

### Post by ERJ on 2010-11-23
I tried looking for a problem like mine before posting, but couldn't find anything helpful.
 
My problem is that last night, when I was watching some .swf file in firefox, the computer slowed down to the point of my not being able to do anything about it. I shut the computer down and restarted to handle the problem. This worked the first few times, and proceeded to really turn out bad later on.
 
Now, I have windows and ubuntu on the same hard drive. Whenever I select ubuntu, I get a message saying "GNU GRUB version 1.98-1ubuntu8" and some stuff about how limited Bash-like commands are supported. I can also his tab to do stuff.
 
By using the help command for everything, I have determined that the command "linux" is supposed to load linux and "boot" is supposed to load an OS. Everytime time I pick a command that should load something, it says that I need to load a kernal.
 
I'm sorry if this question has been answered, but I kind of don't want to reinstall Ubuntu if I don't have to. Please help. How do I load a kernal? How do I *find* a kernal? Please help.

---

### Post by Quackers on 2010-11-23
Welcome to UF :-)
Please boot from the Ubuntu Live cd and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply).
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ERJ on 2010-11-23
Thank you! I will try this when I get home.

---

### Post by Quackers on 2010-11-23
You're welcome :-)
Let's hope we can solve it.

---

### Post by oldschoolgentoo on 2010-11-29
[I]Sorry for the Hijacking the post
But since it is on the same page as the OP, and i would rather not  start a simular post of the same nature.[/I]

Ok  I have been reading and searching the net as well as the UF here for fixes on the change from Grub to Grub2.   

So  it seems to me that instead of  my grub being pointed to sda1 like it should it is shooting to sda3 root.  how do you change it in  grub2?


Did an upgrade from 9.10 to 10.04 and first had the grub_puts_ not found error.  fixed that now have the one we are looking at now.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 129177 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

```

---

### Post by drs305 on 2010-11-29
@ oldschoolgentoo,

Since your sda1 Ubuntu boot files look intact, just get into your normal sda1 OS and then run:
```
sudo grub-install /dev/sda
sudo update-grub
```
That should transfer control to sda at boot, using your sda1 Grub2 files.

---

### Post by oldschoolgentoo on 2010-11-29
with the reboot of the system  i get 
```


                    GNU GRUB    version 1.98-1ubuntu8

Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists possible
devices or file completions .

grub>  _   



```this is what brought me to this post?   "scratches head"

if i type linux after grub i get the "error: no kernel specified" error


i was thinking of changing the  /dev/sda  to  /dev/sda1

```

grub-install /dev/sda && 
sudo update-grub

```
but get errors if i try  hmmm

---

### Post by drs305 on 2010-11-29
> **oldschoolgentoo said:**
> this is what brought me to this post?   "scratches head"

Since you have/had multiple Grubs but it doesn't like the current setup, the best option would be to boot a LiveCD, chroot into sda1, and purge grub2 and reinstall on sda1. During the reinstall, make sure you only install it on "sda" and not "sda1" when you get to the setup page where you have to designate where to put Grub with an asterisk.

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by oldschoolgentoo on 2010-11-29
What did i miss?  i followed the "RTFM"  pretty simple link that you sent me to .  
was able to chroot only issue was no host name for some reason.  but not important right now. no errors as i did the link suggestions as well as the asterisk area like it prompted me to.  went real smooth.

did the update to grub  before reboot. and i get



```


                    GNU GRUB    version 1.98-1ubuntu8

Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists possible
devices or file completions .

grub>  _   



``` 
                               holgerhom                                                             
                  [IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG]                 Re: HOWTO: Purge and Reinstall Grub 2 from the Live CD                                                                             For me, I have the boot partition on sda1 and the root partition on sda2.

In this case, I first had to mount the _root_ fs of sda2 and also /dev,  /dev/pts, /proc and /sys of the root fs as described here, and then,  before continuing, I _additionally_ had to mount the boot fs:

mount sda1 /mnt/temp/boot

Otherwise I got a grub prompt with no kernes found.

---

### Post by oldschoolgentoo on 2010-11-29
Could this be that i have  

/sda1       --- >   /boot
/sda2     ----->   /swap
/sda3   ------->  /

boot on a separate partition than root?

---

### Post by drs305 on 2010-11-29
> **oldschoolgentoo said:**
> Could this be that i have  

/sda1       --- >   /boot
/sda2     ----->   /swap
/sda3   ------->  /

boot on a separate partition than root?

Yes, that's it. Glad you brought that up because without complete the RESULTS.txt I probably wouldn't have figured it out.

You need to mount the boot partition as well. Mount it under */mnt/temp/boot* before you run the purge/install commands. 
```
sudo mount /dev/sda1 /mnt/temp/boot
```

I've updated the guide.

---

### Post by oldschoolgentoo on 2010-11-30
I am starting to not like  Grub2...   grrrr


ok  so i started over with the link you posted. ----->>[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


making sure i did

sudo mount /dev/sda1 /mnt/temp/boot
did the steps  on purging the grub2 from the system.

follwed by a reinstall of grub2

but get the 
                    GNU GRUB    version 1.98-1ubuntu8

Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists possible
devices or file completions .

grub>  _
......


thoughts?   possible  reboot system  after purge?  then  reinstall grub2?

---

### Post by oldschoolgentoo on 2010-11-30
Here is the full  Results.txt from  boot_infoscript055.sh

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 121061 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       240,974       240,912  83 Linux
/dev/sda2             240,975     6,104,699     5,863,725  82 Linux swap / Solaris
/dev/sda3           6,104,700   142,817,849   136,713,150  83 Linux
/dev/sda4         142,817,850   976,768,064   833,950,215   5 Extended
/dev/sda5         142,817,913   193,599,314    50,781,402  83 Linux
/dev/sda6         193,599,378   976,768,064   783,168,687  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   524,297,339   524,297,277  83 Linux
/dev/sdb2         524,297,340 1,048,594,679   524,297,340  83 Linux
/dev/sdb3       1,048,594,680 1,953,520,064   904,925,385  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e269934b-bfb8-467d-9092-e2bdff5819cb   ext3                                     
/dev/sda2        1b68ff4a-2128-46b1-8a36-228db04d1337   swap                                     
/dev/sda3        d2b3cedb-e4ca-48a5-964e-5b1795b20a7a   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d8b62099-bd72-4beb-b5ae-c674fe95b160   ext3                                     
/dev/sda6        62798956-9733-40e6-ad21-2f617f944d32   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        befc4e11-d535-4b6e-b9cb-e4e7f1e60998   ext3                                     
/dev/sdb2        ffbbe796-e418-40e7-b329-83474056bf7c   ext3                                     
/dev/sdb3        c083bcbc-e61b-43e4-9999-7236bcdb9d56   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d2b3cedb-e4ca-48a5-964e-5b1795b20a7a
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
    linux    /vmlinuz-2.6.32-26-generic-pae root=UUID=d2b3cedb-e4ca-48a5-964e-5b1795b20a7a ro   quiet splash
    initrd    /initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /vmlinuz-2.6.32-26-generic-pae root=UUID=d2b3cedb-e4ca-48a5-964e-5b1795b20a7a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
    linux    /vmlinuz-2.6.31-22-generic-pae root=UUID=d2b3cedb-e4ca-48a5-964e-5b1795b20a7a ro   quiet splash
    initrd    /initrd.img-2.6.31-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
    echo    'Loading Linux 2.6.31-22-generic-pae ...'
    linux    /vmlinuz-2.6.31-22-generic-pae root=UUID=d2b3cedb-e4ca-48a5-964e-5b1795b20a7a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e269934b-bfb8-467d-9092-e2bdff5819cb
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-22-generic-pae
    .0GB: initrd.img-2.6.32-26-generic-pae
    .0GB: vmlinuz-2.6.31-22-generic-pae
    .0GB: vmlinuz-2.6.32-26-generic-pae

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d2b3cedb-e4ca-48a5-964e-5b1795b20a7a
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d2b3cedb-e4ca-48a5-964e-5b1795b20a7a
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d2b3cedb-e4ca-48a5-964e-5b1795b20a7a /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e269934b-bfb8-467d-9092-e2bdff5819cb /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=d8b62099-bd72-4beb-b5ae-c674fe95b160 /home           ext3    defaults        0       2
# /storage was on /dev/sda6 during installation
UUID=62798956-9733-40e6-ad21-2f617f944d32 /storage        ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=1b68ff4a-2128-46b1-8a36-228db04d1337 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  65.0GB: boot/grub/core.img
  65.0GB: boot/grub/grub.cfg
  65.0GB: boot/initrd.img-2.6.32-26-generic-pae
  65.0GB: initrd.img



```

---

### Post by CzR45 on 2010-11-30
I've got the same problem, but I installed Ubuntu in windows using wubi. How do I solve this problem if I don't have a LiveCD?

---

### Post by oldschoolgentoo on 2010-11-30
> **CzR45 said:**
> I've got the same problem, but I installed Ubuntu in windows using wubi. How do I solve this problem if I don't have a LiveCD?



CzR45,  what version of windows are you using?  windows XP  windows 7?  dual boot?

---

### Post by CzR45 on 2010-11-30
Windows 7 home premium

---

### Post by drs305 on 2010-12-01
> **oldschoolgentoo said:**
> I am starting to not like  Grub2...   grrrr

thoughts?   possible  reboot system  after purge?  then  reinstall grub2?

I am sure this is being caused by the separate boot. I haven't tried to interpret RESULTS.txt with a separate /boot, but the first line doesn't look correct since it says it's looking at partition 3 for /boot/grub. The boot files should be on sda1 - but I'm not sure the boot info script would report it that way. 

Assuming it is correct, and since the OS isn't booting anyway, let's go through it once more. I'll put the steps in this thread, modified slightly for your setup.

```

sudo mkdir /mnt/temp /mnt/temp/boot
sudo mount /dev/sda3 /mnt/temp
sudo mount /dev/sda1 /mnt/temp/boot
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp

```

In the chroot at the 'root' prompt:
```

apt-get update
apt-get install --reinstall grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
update-grub
exit
```
Unmount:
```

for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
sudo umount /mnt/temp/boot && sudo umount /mnt/temp

```
Reboot and see if it now works.

---

### Post by lintingy on 2010-12-20
Hi, I'm a new comer to ubuntu and UF.
 I install ubuntu on windows by wubi and I got the same problem this morning when I open my computer.
 
 I tried the boot_info_script with Live USB and get the result.txt as below:
 ```

                 Boot Info Script 0.55    dated February 15th, 2010                    
 
 ============================= Boot Info Summary: ==============================
 
  => Windows is installed in the MBR of /dev/sda
  => Syslinux is installed in the MBR of /dev/sdb
 
 sda1: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
     Boot files/dirs:   /bootmgr /boot/bcd
 
 sda2: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
     Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                        /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                        /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                        /ubuntu/disks/swap.disk
 
 sda2/Wubi: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Mounting failed:
 mount: wrong fs type, bad option, bad superblock on /dev/loop1,
        missing codepage or helper program, or other error
        In some cases useful info is found in syslog - try
        dmesg | tail  or so
 
 
 sda3: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
     Boot files/dirs:   
 
 sdb1: _________________________________________________________________________
 
     File system:       vfat
     Boot sector type:  Fat32
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
 
 /dev/sda1               2,048    10,979,327    10,977,280  27 Hidden HPFS/NTFS
 /dev/sda2    *     10,979,328   226,859,007   215,879,680   7 HPFS/NTFS
 /dev/sda3         226,859,008   312,578,047    85,719,040   7 HPFS/NTFS
 
 
 Drive: sdb ___________________ _____________________________________________________
 
 Disk /dev/sdb: 2048 MB, 2048901120 bytes
 64 heads, 63 sectors/track, 992 cylinders, total 4001760 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
 Partition  Boot         Start           End          Size  Id System
 
 /dev/sdb1    *            245     3,999,743     3,999,499   b W95 FAT32
 
 
 blkid -c /dev/null: ____________________________________________________________
 
 Device           UUID                                   TYPE       LABEL                         
 
 /dev/loop0                                              squashfs                                 
 /dev/loop1       1c8e90c8-7f05-4980-a7e2-bb5e884dd2ab   ext4                                     
 /dev/sda1        E69E1E149E1DDE3D                       ntfs       ServiceV002                   
 /dev/sda2        D446285946283E9C                       ntfs       C_Prim                        
 /dev/sda3        4692023592022A4F                       ntfs       D_Data                        
 /dev/sda: PTTYPE="dos" 
 /dev/sdb1        4ACD-B2AC                              vfat       PENDRIVE                      
 /dev/sdb: PTTYPE="dos" 
 
 ============================ "mount | grep ^/dev  output: ===========================
 
 Device           Mount_Point              Type       Options
 
 aufs             /                        aufs       (rw)
 /dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
 /dev/loop0       /rofs                    squashfs   (ro,noatime)
 
```It looks different to the one post by   [oldschoolgentoo]("http://www.uluga.ubuntuforums.org/member.php?u=1173173").
And I found a different answer here: 
[http://ubuntuforums.org/showthread.php?t=1391670](http://ubuntuforums.org/showthread.php?t=1391670)
But in the link, it said this is only a temporary fix.
I wondering what should I do to solve this for long?

Thanks!!

---

### Post by drs305 on 2010-12-21
lintingy,

Welcome to Ubuntu and the Ubuntu forums.  :-)

If you compare your RESULTS.txt entry for your Wubi installation (sda2/Wubi) with a normal one (below) you can see that you have a mounting problem.
> 
 sda2/Wubi: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System: Ubuntu 10.10
     Boot files/dirs: /boot/grub/grub.cfg /etc/fstab


It's possible you just need to reinstall Grub2, or you may have a larger problem. 

Here are your options:
1. Boot a LiveCD, mount your Wubi installation, reinstall Grub2 and see if that fixes the problem. Here is a guide to help do this. Make sure you use the mount instructions for Wubi in the "Chroot" section. 
[_HOWTO: Purge and Reinstall Grub 2 from the Live CD_]("http://ubuntuforums.org/showthread.php?t=1581099")

2. Reinstall Wubi. Remove Wubi from the Windows Control Panel Add/Remove section and reinstall it. If you haven't made any customizations and don't have any data stored there, this may be the easiest/fastest solution. Note that you can recover and save any data files first (we can tell you how if that is what you decide to do). Once you remove Wubi you lose whatever is still inside your Wubi folders.

3. There is a thread devoted specifically to Wubi boot problems. It explains the symptoms and how to repair Wubi:
[*Wubi Megathread*]("http://http://ubuntuforums.org/showthread.php?t=1639198")
I am not sure if your situation is described in this guide but you can read each section and decide if it applies to you.

---

### Post by lintingy on 2010-12-21
drs305,

Thanks for your help!!!

I had tried the first link, but something went wrong.
I can't even open my win7 now.
when I open my laptop, it goes directly to: 
error: nosuch device: xxxxxx-oooxx-...
grub rescue >

I tried several command in grub rescue:
grub rescue > ls
(hd0)
grub rescue > set
prefix=(hd0)/boot/grub
root=hd0
grub rescue > insmod normal
error: unknown filesystem.

there's only (hd0) now?

I tried live USB again, and here's the new boot info script:
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1               2,048    10,979,327    10,977,280  27 Hidden HPFS/NTFS
/dev/sda2    *     10,979,328   226,859,007   215,879,680   7 HPFS/NTFS
/dev/sda3         226,859,008   312,578,047    85,719,040   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2048 MB, 2048901120 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            245     3,999,743     3,999,499   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1c8e90c8-7f05-4980-a7e2-bb5e884dd2ab   ext4                                     
/dev/sda1        E69E1E149E1DDE3D                       ntfs       ServiceV002                   
/dev/sda2        D446285946283E9C                       ntfs       C_Prim                        
/dev/sda3        4692023592022A4F                       ntfs       D_Data                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0DFD-1516                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/D_Data            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set d446285946283e9c
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set d446285946283e9c
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=zh
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e69e1e149e1dde3d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d446285946283e9c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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


   4.7GB: boot/grub/core.img
   4.9GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.32-24-generic
   3.6GB: boot/initrd.img-2.6.32-25-generic
   5.5GB: boot/initrd.img-2.6.32-26-generic
   5.0GB: boot/vmlinuz-2.6.32-24-generic
   5.0GB: boot/vmlinuz-2.6.32-25-generic
   5.5GB: boot/vmlinuz-2.6.32-26-generic
   5.5GB: initrd.img
   3.6GB: initrd.img.old
   5.5GB: vmlinuz
   5.0GB: vmlinuz.old

```

I found someone met similar problem here:
[http://ubuntuforums.org/showthread.php?t=1490715]("http://ubuntuforums.org/showthread.php?t=1490715")

But there's still something different...
I'm not sure if I could just follow the instruction in that post??

thanks for your help again!! thanks!!

---

### Post by oldfred on 2010-12-21
With wubi you boot thru windows, so you do not install grub to the MBR, but keep the windows boot loader in the MBR.

To install a windows like boot loader. 

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

This was posted about and has most of the wubi solutions:

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by lintingy on 2010-12-22
Thanks oldfred and drs305!!
You're suggestion solved my quesiotn!!
Everything so far is fine now!!
Thanks a lot!!

---

