---
title: "my grub has gone"
date: 2011-05-10
forum: General Help
---

### Post by aab001 on 2011-05-10
hello 
after I install windows the grub is gone
i tried to do some thing and i follow the steps listed in this link
[http://ubuntuforums.org/showthread.php?t=922678](http://ubuntuforums.org/showthread.php?t=922678)
because it was very similar to my problem, i did every thing up to step #10 which is
sudo mount -o bind /dev /mnt/dev sudo mount -t proc none /mnt/proc sudo chroot /mnt apt-get install grub update-grub exit know when i reboot i became to grub screen ( grub>               )
 with no option. even my windows is gone I don't know what to do
please help

---

### Post by ManualSparrow on 2011-05-11
[http://ubuntuforums.org/showthread.php?t=1736692](http://ubuntuforums.org/showthread.php?t=1736692)

Similar deal. You should be able to boot in the GRUB command line and then fix the GRUB once you get to Ubuntu.

---

### Post by Hedgehog1 on 2011-05-11
We need to get a look at what shape your partitions are in.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by aab001 on 2011-05-11
We need to get a look at what shape your partitions are in.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the ```
 & 
``` tags.

[I][B]The Hedge

# 

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   252,188,369   252,188,307   7 HPFS/NTFS
/dev/sda2         252,188,670   396,722,175   144,533,506   5 Extended
/dev/sda5         252,188,672   260,001,791     7,813,120  82 Linux swap / Solaris
/dev/sda6         260,003,840   328,361,983    68,358,144  83 Linux
/dev/sda7         328,364,032   396,722,175    68,358,144  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C82C6FE52C6FCCCE                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        792cbf23-5d78-4223-ad91-d29e0e27abaf   swap                                     
/dev/sda6        5f237478-fea7-4ed2-824c-3cbbe91d2daa   ext4                                     
/dev/sda7        8f7dc388-e19f-4209-973b-040ecca2300d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /mnt                     ext4       (rw)
/dev/sda7        /media/8f7dc388-e19f-4209-973b-040ecca2300d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/C82C6FE52C6FCCCE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5f237478-fea7-4ed2-824c-3cbbe91d2daa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5f237478-fea7-4ed2-824c-3cbbe91d2daa /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=8f7dc388-e19f-4209-973b-040ecca2300d /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=792cbf23-5d78-4223-ad91-d29e0e27abaf none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/core.img
 154.7GB: boot/grub/grub.cfg
 154.7GB: boot/grub/stage2
 134.1GB: boot/initrd.img-2.6.35-22-generic
 134.3GB: boot/initrd.img-2.6.35-25-generic
 134.7GB: boot/initrd.img-2.6.35-27-generic
 135.3GB: boot/initrd.img-2.6.35-28-generic
 154.7GB: boot/vmlinuz-2.6.35-22-generic
 154.7GB: boot/vmlinuz-2.6.35-25-generic
 154.7GB: boot/vmlinuz-2.6.35-27-generic
 155.2GB: boot/vmlinuz-2.6.35-28-generic
 135.3GB: initrd.img
 134.7GB: initrd.img.old
 155.2GB: vmlinuz
 154.7GB: vmlinuz.old
[/B][/I]

---

### Post by aab001 on 2011-05-11
still I need your help

---

### Post by Quackers on 2011-05-11
Please boot from the live cd/usb and select "try ubuntu" and when the desktop loads open up a terminal.
In the terminal copy/paste these commands one line at a time pressing enter after each line.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
``` and if no errors are reported please reboot. Ubuntu should now boot directly. Does It?

---

### Post by QLee on 2011-05-11
Quackers, 
It might be useful to confirm which version of the live CD the OP is using for installing to the MBR, it appears that somehow aab001 got the GRUB-legacy version installed, yet the rest of the script results look like a system that should use GRUB2, Ubuntu 10.10.

---

### Post by Quackers on 2011-05-11
Yes, you are right Qlee. It seems aab001 has used a guide written in 2008 to repair his system. Not a good idea.
At least all the grub2 boot files are there so the commands I posted may still work (but as Qlee says, only using a recent live cd).
If it proves necessary to purge/re-install grub we can do that :-)

---

### Post by QLee on 2011-05-11
[QUOTE=aab001]still I need your help[/QUOTE]

It can be easy to become confused following old documentation and it often happens to new users. Ubuntu is a rapidly evolving operating system with a new release every 6 months and things can change fairly drastically from one release to another. The change from the old style grub to the new version has caused confusion for many. Don't worry, what you have appears to be easily fixable and Quackers will stay with you to help, will even ask others to help if necessary.

---

### Post by aab001 on 2011-05-11
thank you for your cooperation
i tried the command that Quackers asked me to do but still is not working

---

### Post by QLee on 2011-05-11
[QUOTE=aab001]thank you for your cooperation
i tried the command that Quackers asked me to do but still is not working[/QUOTE]

Yes, but you did not tell us the error message you received when you tried those commands. In a reply post, it is often helpful to post exactly the commands you typed and any error message you receive exactly as it appears to you in the terminal.

If you re-read my posts you will see that it could be helpful for you to also tell us what version of the Ubuntu live CD you are using for this.

---

### Post by aab001 on 2011-05-11
I am using live cd ubuntu10.10
and know when I reboot without live cd I end up with grub screen ( grub>                )
I don't know what to do ?

---

### Post by aab001 on 2011-05-12
I am using live cd ubuntu10.10
and know when I reboot without live cd I end up with grub screen ( grub>                )
I don't know what to do ?

---

### Post by aab001 on 2011-05-12
> **Quackers said:**
> Yes, you are right Qlee. It seems aab001 has used a guide written in 2008 to repair his system. Not a good idea.
At least all the grub2 boot files are there so the commands I posted may still work (but as Qlee says, only using a recent live cd).
If it proves necessary to purge/re-install grub we can do that :-)

how can i reinstall grub

---

### Post by QLee on 2011-05-12
> **aab001 said:**
> how can i reinstall grub

Sorry, this must be frustrating for you aab001.

I have no idea what happened to Quackers (unlucky coincidence for you that both of us were gone at the same time), I did not expect you would be left with no help and I don't understand why no one else stepped up to help you, I've been gone since just a bit after making my previous post and I won't be here long today, just checked in to see things.

Here is the community guide for restoring GRUB to the MBR after an install of Windows:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and this post is detailed and helpful:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

However, you seem reluctant to participate in the fix, don't seem to want to give us much information, don't even tell us what you understand and what you don't understand, so you probably are looking for someone to tell you which keys to push in a step-by-step. In addition, legacy GRUB did not get into the MBR of your system when you installed Windows so there are things that you are not telling us about what you did and that makes it harder to troubleshoot. So, we'll just have to start with the assumption that the system was working correctly and you installed Windows which installed its own bootloader into the MBR as you described in your first post.

Boot up your system with your live 10.10 CD. 

We know from your results.txt that your Ubuntu 10.10 is on /dev/sda6. 
(There is also sda7 with an ext4 filesystem but it doesn't show as having an operating system on it so it is probably something you use for data.) 

Now, in a terminal window, try the commands that Quackers gave you in post 6:
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That should write the bootloader into the MBR (master boot record) of sda (your only physical drive) pointing to the partition sda6 as the place to look for the files it needs for the boot menu (and results.txt shows that they are there).

Since installing Windows did not do anything to your Ubuntu partition because Windows did not "see" it when you installed, your system should now boot and display the boot menu just as it did before Windows overwrote the MBR. When you have successfully booted into Ubuntu (this time, I mean the one on your system not the live CD), run sudo update-grub to have GRUB find the Windows install and add it to the boot menu so it will be available on the next boot.

I hope you were able to follow along with what we were doing with the commands as you were entering them.

If this did not work as expected, please tell what else you did before you posted your question, besides just installing Windows and please write the exact error message in your post if you receive one. The exact error message is not always important, but sometimes it is critical to finding a fix when we know what command dropped the error.

---

### Post by Quackers on 2011-05-12
Thanks Qlee :-)
Sorry I've been away.
If those commands don't do anything it may be an idea to purge then re-install grub. You can do this by looking at the CHROOT section of the guide below.
The partition you want to mount at first is /dev/sda6 and the place where grub is to be installed is /dev/sda (no number at the end)
Good luck
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by aab001 on 2011-05-14
p { margin-bottom: 0.21cm; }  Thank you for your help and sorry for my late replay which is due to may late work because my system was not working.
#
 Qlee wrote
However, you seem reluctant to participate in the fix, don't seem to  want to give us much information, don't even tell us what you understand  and what you don't understand, so you probably are looking for someone  to tell you which keys to push in a step-by-step. In addition, legacy  GRUB did not get into the MBR of your system when you installed Windows  so there are things that you are not telling us about what you did and  that makes it harder to troubleshoot. So, we'll just have to start with  the assumption that the system was working correctly and you installed  Windows which installed its own bootloader into the MBR as you described  in your first post.
 #
 In fact I taught I explained what I did by posting the link I used to write every command until I found the problem. I believed that is a short cut for listing all the commands I wrote. (sorry for inconvenience)  
 after your last post I used the commands  
 sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
 and my grub works
 also I used the command sudo update-grub  
 and every thing know is working very well
 many thanks for you and for all your team for your patient and I want to ask know how can I develop my knowledge to learn more about ubuntu and what is the command shows that my grub is updated to grub2

---

### Post by QLee on 2011-05-14
[QUOTE=aab001]...
 after your last post I used the commands  
 sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
 and my grub works
 also I used the command sudo update-grub  
 and every thing know is working very well
 many thanks for you and for all your team for your patient and I want to ask know how can I develop my knowledge to learn more about ubuntu and what is the command shows that my grub is updated to grub2[/QUOTE]

Great, I was worried you might not understand everything but you did and were successful. 

You've already started developing your knowledge and if you continue to read posts in the forum you will continue to learn about Ubuntu. You can use the forum search tool to investigate specific topics that interest you. You'll find many links to topics at,

[Edit] Oops, I gave you 11.04 1nd you use 10.10 here is the correct link
[https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)
and
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

and many links in the forum threads you read (each user has their own favorites).

You don't need a command for that, when your GRUB boot screen is presented you will see the version number at the top of the screen, it will be higher than 1.9 and that is what we refer to as GRUB2 (it is actually grub-pc), old (what we refer to as legacy) is Grub 0.97

---

