---
title: "Errors before grub2 screen"
date: 2010-11-29
forum: General Help
---

### Post by CyberMuz on 2010-11-29
When I start my computer I have some errors messages appearing on screen after bios screen and just before grub screen appears. They are shown for a fraction of a second so I can't read them. Grub then loads in 'recovery' mode (no countdown is shown). How can I read these error messages? Is there any log for them or anything similar?

---

### Post by Rubi1200 on 2010-11-29
Hi and welcome to the forums :)
Are you able to boot normally into Ubuntu afterwards?

Do you have other operating systems installed?

If you can boot into Ubuntu, please post the results of the boot info script linked at the bottom of my post.

Thanks.

---

### Post by CyberMuz on 2010-11-29
Tnx for the welcome! :)
Yes, everything works normal. I have Ubuntu/Win7 dual boot and it's working fine but I would like to know what these errors are.
Before the update I had customized grub (old version, not grub2) screen by adding background picture and adjusting fonts. I think this might be the cause of the problem.
Here are my results for bootinfo script.

---

### Post by Rubi1200 on 2010-11-29
Thanks for the results. From what I can tell, it seems fairly normal. Have you recently upgraded to 10.10?
If you run > sudo update-grub after making the custom changes in, I assume, 41_custom do you still have a problem?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   488,392,064   385,993,755   f W95 Ext d (LBA)
/dev/sda5         102,398,373   225,279,494   122,881,122   7 HPFS/NTFS
/dev/sda6         225,279,558   389,110,364   163,830,807   7 HPFS/NTFS
/dev/sda7         389,110,428   484,488,269    95,377,842  83 Linux
/dev/sda8         484,488,333   488,392,064     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0276258076257597                       ntfs       Prvi                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        08808F31808F2472                       ntfs       Drugi                         
/dev/sda6        B47C0E4D7C0E0B36                       ntfs       Treci                         
/dev/sda7        71f59f16-204a-4c91-a1cf-7f0ce1b69064   ext4                                     
/dev/sda8        212d3f35-b68c-4976-92c2-959a8bf2f1e4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/prvi              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/drugi             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/treci             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800
  set gfpayload=keep
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
insmod png
if background_image /usr/share/images/grub/ubuntu.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 71f59f16-204a-4c91-a1cf-7f0ce1b69064
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0276258076257597
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=71f59f16-204a-4c91-a1cf-7f0ce1b69064 /               ext4    errors=remount-ro 0       1

/dev/sda1   /media/prvi   ntfs   user,fmask=0111,dmask=0000   0   0
/dev/sda5   /media/drugi   ntfs   user,fmask=0111,dmask=0000   0   0
/dev/sda6   /media/treci   ntfs   user,fmask=0111,dmask=0000   0   0
# swap was on /dev/sda8 during installation
UUID=212d3f35-b68c-4976-92c2-959a8bf2f1e4 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 200.2GB: boot/grub/core.img
 201.9GB: boot/grub/grub.cfg
 222.9GB: boot/initrd.img-2.6.31-21-generic
 232.6GB: boot/initrd.img-2.6.32-26-generic
 236.6GB: boot/initrd.img-2.6.35-23-generic
 209.5GB: boot/vmlinuz-2.6.31-21-generic
 203.6GB: boot/vmlinuz-2.6.32-26-generic
 215.3GB: boot/vmlinuz-2.6.35-23-generic
 236.6GB: initrd.img
 232.6GB: initrd.img.old
 215.3GB: vmlinuz
 203.6GB: vmlinuz.old
```

---

### Post by drs305 on 2010-11-29
I don't fully understand your original post where you say it boots to recovery mode but then later state everything is working normally. Does the system boot to the normal Desktop without any intervention?

If I had to guess, I would expect the error messages have something to do with the "gfxpayload", "gfxmode" settings or the blank "insmod". 

You can experiment with a one-time boot by booting to your normal install, then editing /boot/grub/grub.cfg (which isn't normally done, but it won't hurt anything). 
```
gksu gedit /boot/grub/grub.cfg
```

If I had to guess, I would suspect this section. The gfxmode seems reasonable but I don't know what your BIOS supports, so I've changed it to the default 640x480.

There is also an empty "insmod", which could generate an error. Finally, there have been problems from time to time with the "gfxpayload" command, so I've commented that as well.

Make the changes and save the file but do NOT run update-grub since that would wipe out the changes. Reboot and see if you still get the errors. 
> 
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=**[COLOR="DarkRed"]640x480[/COLOR]**
**[COLOR="DarkRed"]#[/COLOR]**   set gfpayload=keep
  insmod gfxterm
**[COLOR="DarkRed"]#[/COLOR]**  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi


If you don't get them, we can make the changes in the appropriate scripts.

If they still appear, you can return to your original state by running "sudo update-grub".

 I would purge/reinstall G2. It's very simple if you can boot to your normal install. But try the above first.

---

### Post by CyberMuz on 2010-11-29
I solved the problem by purging and reinstalling grub. (tnx for making tutorial drs305)
What i meant in my original post is that grub starts in mode where there's no countdown so I have to select OS by hitting enter.

---

### Post by harlequin_ on 2010-12-30
Hi!
I have the same problem, getting error messages (that appear and disappear very fast so I cant read them) just before Grub 2 kicks in when I boot. I also use Ubuntu/Win7 on this machine. The problem started today after I upgraded to 10.10 from 10.04. When I was using 10.04 I had some customizations on *[COLOR=blue]05_debian_theme [/COLOR]*[COLOR=blue][COLOR=Black]file, and I was able to use the background image I desired. Now I upgraded to 10.10 and the background image which used to appear in 10.04 does not in 10.10, I get no countdown on Grub 2 screen when I boot and I get the errors mentioned in the OP. I tried to purge Grub 2 by 

[/COLOR][/COLOR]```
sudo apt-get remove --purge grub-pc
```

and then reinstalled it, but it didn't work.  still no countdown and still errors before Grub 2 screen :confused:. Any advice is appreciated..

Thanks!

---

### Post by drs305 on 2010-12-31
alimay,

Welcome to the Ubuntu forums.

First, regarding the background image. Grub2 has changed the way wallpapers are designated at least three times since it was introduced. It's possible your old convention for designating the wallpaper has changed with the newer version.  

As good as the boot info script is, one thing it doesn't display is the version of Grub2 you are using. You can get this information from the top of the G2 menu screen during boot, from Synaptic, or by running:
```
grub-install -v
```
If you tell me the version I can tell you how to include the wallpaper.

The command you posted wasn't the correct format for purging/reinstalling Grub 2. If you want a completely fresh install you should remove both grub-pc (Grub2) and grub-common.

I have posted the instructions in another guide. While the guide details how to 'chroot' into your installation, this is not necessary if you can still boot normally (without the LiveCD) into Ubuntu. If you can boot without the CD, go to the link and complete *only* steps 2-5. That should reinstall G2 for you.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

If you have to boot from a LiveCD, complete all the steps in the 'chroot' section.

---

### Post by harlequin_ on 2010-12-31
dear [[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")

after I followed steps from 2 to 5 in the [link]("http://ubuntuforums.org/showthread.php?t=1581099") you mentioned, the error messages that used to appear when I boot just before grub 2 screen disappeared and I was able to set my background image & reconfigure resolution etc. many thanks for your help.

---

### Post by drs305 on 2010-12-31
> **alimay said:**
> dear [[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")

after I followed steps from 2 to 5 in the [link]("http://ubuntuforums.org/showthread.php?t=1581099") you mentioned, the error messages that used to appear when I boot just before grub 2 screen disappeared and I was able to set my background image & reconfigure resolution etc. many thanks for your help.

That's 2 for 2 in this thread, so this solution seems to be at least one way to solve the problem.

Happy Ubuntu-ing (and New Year)!  :-)

---

