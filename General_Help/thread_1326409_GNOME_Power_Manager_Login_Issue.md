---
title: "GNOME Power Manager Login Issue"
date: 2009-11-14
forum: General Help
---

### Post by TyD on 2009-11-14
Hey guys, I recently upgraded to 9.10 (64 bit), and was mostly pleased with it.  However, this morning when I tried to log on, I received an error message that said, "Install Problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator." I cannot log on to my computer now, as every time I try, I am sent back to the login screen.

My computer had been working well before this (besides not having sound) so I don't know where this could have come from.  Any help would be greatly appreciated.  Thanks!

---

### Post by whitelight1 on 2009-11-15
> **TyD said:**
> Hey guys, I recently upgraded to 9.10 (64 bit), and was mostly pleased with it.  However, this morning when I tried to log on, I received an error message that said, "Install Problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator." I cannot log on to my computer now, as every time I try, I am sent back to the login screen.

My computer had been working well before this (besides not having sound) so I don't know where this could have come from.  Any help would be greatly appreciated.  Thanks!

Same here.
I am using Xubuntu Karmic.
Everything was working properly until yesterday when i installed some updates. After doing so and rebooting i could not start applications which require my password.

So now i can not log in anymore. I can log in as 'root' (i created that account due to SWAT..).

Also, Totem does not play sound anymore. And I can not seek trough some videofiles.
This is very annoying so please if there is any help ...

---

### Post by whitelight1 on 2009-11-15
This finally worked for me:
```
apt-get --reinstall install gnome-power-manager
```After loggin in again, some of my Desktop and Panelsettings were gone. I have no idea why.
Totem is now working with sound again.

Programs like Gparted are working again as usual.

But since i have not changed anything on the system besides installing the updates, I am not shure how to 'trust' Ubuntu in the future.

---

### Post by Ithiel on 2009-11-16
This may or may not be your issue. I have had the problem to occur twice and finally found the culprit in MY case. It was simplebackup. In using SimpleBackup to back up my files to an external hard drive, occasionally it fails to mount the drive correctly. In such cases, if not configured correctly it will simply add a back up folder to your home folder and begin backing up there. That can quickly result in using up so much of your free space that your computer cannot boot properly. 

Using a live CD, I went in and deleted the erroneous back ups and then everything booted fine. I also went back into SimpleBackUp Config and clicked the Destination tab and marked the Abort backup if destination directory does not exist box. Its all good now.

---

### Post by pigphish on 2009-11-17
I had the same issue with simple backup (simple backup). I couldnt find the confounded files until I did:

```
sudo find / -name '*' -size +1G

```

once i removed the backup files i was finally once again able to see available space using df command. 

mine where in var/backup of my ubuntu partition. I even had the option selected to fail if destination folder not found. Very frustrating simple backup. ](*,)

---

### Post by John RG on 2009-11-21
Thankyou. Saved me!

---

### Post by Kinnard on 2009-12-11
Ok, people have proffered a lot of solutions, but where do I type all that stuff in? Thanks.

---

### Post by rpaskudniak on 2009-12-23
Kinnard,  Mr. Concise (NOT) here.

If your problem is like mine, you don't have a desktop environment in which to click on the terminal application; merely an orange desktop with some abstract orange image.  So your question is quite reasonable - how do you enter all these cool commands folks are suggesting?

Since gdm and the Window manager *is* running, albeit messed up, you get out of Windowing mode with the three-finger salute, Ubuntu style:
Ctrl-Alt-F1.

(On my keyboard, I had to first press the F-Lock key and use only the Ctrl-Alt keys on the left of the keyboard.)

In any case, what worked for me was... Wait, first how I got into this mess:

For whatever reason, the monitor would not come out of "hibernate" mode after the screen saver had been running for a long time.  I pressed the Power button to get the attention of the host but it rebooted instead.  When it came up, it would not boot correctly; I had to boot into recovery mode and run fsck.  It "fixed" a lot of files, leaving me with this login problem everyone in this thread (and quite a few others) has described.  (Sorta like getting your cat "fixed", from the cat's viewpoint. :twisted: )  I observed that many files being diddled were related to gnome some way.

BTW, other logins had no problem; only my profile (using the term loosely) was messed up.

What finally got back my gnome desktop:
[LIST=1]
[*]Ctrl-Alt-F1 - This got me into console mode in my own login session, _in my own home directory_. (No, I was not nostalgic for the 24-line CRT session wherein I learned Unix. :rolleyes:  )
[*]sudo stop gdm.  (Alternatively, /etc/init.d/gdm stop)
[*]mv .gconfd .gconfd-save
[*]sudo start gdm (Alternatively, /etc/init.d/gdm start)
[/LIST]
This presented my login screen again.  I logged in and had a default gnome desktop.  I had to recall the way I liked it (background picture, number of desktops, etc) **_but I was able to do it_**!

BTW, looking at the .gconfd-saved directory, it looks a lot like my .gconf directory (which seems to have gotten recreated freshly as well), not at all like the new .gconfd directory.  So I see where something was messed up.  All the error messages were total red herrings, IMHO.

---

### Post by RCepeda on 2009-12-28
It was exactly the thing that Ithiel said. I just set up my simple backup last wed to the external HD and as soon as I found the folder using what pigphish said and removed it, everything was working like a charm.
Thanks guys....:)

---

### Post by KPDXHAM on 2009-12-28
> **Ithiel said:**
> This may or may not be your issue. I have had the problem to occur twice and finally found the culprit in MY case. It was simplebackup. In using SimpleBackup to back up my files to an external hard drive, occasionally it fails to mount the drive correctly. In such cases, if not configured correctly it will simply add a back up folder to your home folder and begin backing up there. That can quickly result in using up so much of your free space that your computer cannot boot properly. 

Using a live CD, I went in and deleted the erroneous back ups and then everything booted fine. I also went back into SimpleBackUp Config and clicked the Destination tab and marked the Abort backup if destination directory does not exist box. Its all good now.

Well now! I've been searching threads and find that someone else has had a problem using Sbackup.

Please look here:
[http://ubuntuforums.org/showthread.php?t=1355880](http://ubuntuforums.org/showthread.php?t=1355880)

In the mean time, while I wait for someone to help, I'll keep trying to figure out how to access the Karmac Koala via the live Ubuntu 9.10 cd.

Sorry for posting all over the place, but I really would like to be able to fix this system since it was all finely tuned to what I liked and there's files I would rather not loose. Instead of reinstalling again and again](*,) (newbie), It would be really great to be able to fix the problem and move on.

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4dc6038e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   320,159,384   320,159,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="1CA81EC9A81EA176" LABEL="Hard Drive" TYPE="ntfs" 
sdb1: UUID="25F6416015D78FD1" LABEL="Ubuntu" TYPE="ntfs" 
sdb1/Wubi: UUID="2f413912-9705-4610-9eb2-58e809293511" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/Hard Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\wubildr.mbr="Ubuntu" 

======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2c4c10654c102c58
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2c4c10654c102c58
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2c4c10654c102c58
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2c4c10654c102c58
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1ca81ec9a81ea176
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
_____________________________
Thanks for help in advance!

---

### Post by HViktor on 2010-01-01
> **KPDXHAM said:**
>  In the mean time, while I wait for someone to help, I'll keep trying to figure out how to access the Karmac Koala via the live Ubuntu 9.10 cd.

Sorry for posting all over the place, but I really would like to be able to fix this system since it was all finely tuned to what I liked and there's files I would rather not loose. Instead of reinstalling again and again](*,) (newbie), It would be really great to be able to fix the problem and move on.


Hi All!

I think the mystic "GNOME Power Manager not installed correctly. Please contact your system administrator." message is only a symptom in the most of the cases. I was hit by this issue two week ago and I had to investigate a lot to find out the solution.

In my case I run out of free disk space because of an tricky sbackup setting :) and because I am a beginner Linux guy.
Behind the surface xserver (gnome) try to write important configuration files like xauthorization which has to be part of the new gnome session. Without that files you cannot log in.
A few problem solving tips around the out of space and Gnome login problem things:

[LIST]
[*]try to get a living console (from one of the recovery menus or hit CTRL+ALT+F1)
[*]Log in as usual
[*]try to make free space (use rm command carefully, try to delete older sbackup catalogues (as root) or a few unimportant files like avi-s or iso-s, some flac-s or something "big" :). There are a nice tip from pigphis to to find them. Just follow with +50M at the end.
[*]After that you have a chance to solve the login issue. In my case I just deleted the /home/*myusername*/.gconf catalog (you can rename it also if you want).
[*]run startx
[*]I hope you will see a default gnome GUI and will feel more self-confidence to clean up your system and restore your settings manually or from backups.
[*]If not, you should continue with the other tips like install-reinstall gnome-power-manager or ubuntu-desktop...
[/LIST]
The message: be careful with your disk space. It can initialise a lot of tricky issues in your system. :neutral:

I hope you can use this ideas to fix your system. If I was wrong, sorry. If you request I can explain this process in more details (for instance with used commands). Sorry for my poor English too...

Best regards,
Viktor

---

### Post by KPDXHAM on 2010-01-01
> **HViktor said:**
> Hi All!

I think the mystic "GNOME Power Manager not installed correctly. Please contact your system administrator." message is only a symptom in the most of the cases. I was hit by this issue two week ago and I had to investigate a lot to find out the solution.

In my case I run out of free disk space because of an tricky sbackup setting :) and because I am a beginner Linux guy.
Behind the surface xserver (gnome) try to write important configuration files like xauthorization which has to be part of the new gnome session. Without that files you cannot log in.
A few problem solving tips around the out of space and Gnome login problem things:

[LIST]
[*]try to get a living console (from one of the recovery menus or hit CTRL+ALT+F1)
[*]Log in as usual
[*]try to make free space (use rm command carefully, try to delete older sbackup catalogues (as root) or a few unimportant files like avi-s or iso-s, some flac-s or something "big" :). There are a nice tip from pigphis to to find them. Just follow with +50M at the end.
[*]After that you have a chance to solve the login issue. In my case I just deleted the /home/*myusername*/.gconf catalog (you can rename it also if you want).
[*]run startx
[*]I hope you will see a default gnome GUI and will feel more self-confidence to clean up your system and restore your settings manually or from backups.
[*]If not, you should continue with the other tips like install-reinstall gnome-power-manager or ubuntu-desktop...
[/LIST]
The message: be careful with your disk space. It can initialise a lot of tricky issues in your system. :neutral:

I hope you can use this ideas to fix your system. If I was wrong, sorry. If you request I can explain this process in more details (for instance with used commands). Sorry for my poor English too...

Best regards,
Viktor

THANK YOU Viktor, for trying to help me! Happy New Year!
Yes, from what I've been reading in the forums I think I messed up by not knowing just how to use Sbackup and ran out of free space on my Ubuntu partition.
My problem is that I have not figured out just how to access my Ubuntu root.disk using either of these:

[LIST]
[*]sh:grub>
[*]Live Ubuntu 9.10 cd
[/LIST]
I've tried the super grub boot disk and the Ubuntu Rescue Remix disk also.

After waiting several days for someone to help me, I finally reformatted the Ubuntu HDD and made several partitions on it.
I still have the original Ubuntu folder with everything in it saved on my XP HDD.
If someone tells me precisely what to do to access my root.disk to make the repair or save my home folder from it, then I will do a fresh wubi install to the Ubuntu HDD.
After the fresh install I would replace the root and swap disks with the original (problem) Ubuntu disks. 

Thanks again,
Cliff

---

### Post by HViktor on 2010-01-02
> **KPDXHAM said:**
> 
If someone tells me precisely what to do to access my root.disk to make the repair or save my home folder from it, then I will do a fresh wubi install to the Ubuntu HDD.
After the fresh install I would replace the root and swap disks with the original (problem) Ubuntu disks. 

Welcome!
I am sorry because I am not a WUBI expert. I use native Ubuntu and I have not experience on it.

Did you try the virtual disk extraction to be a real partition (see WubiGuide Wiki)? (after that you can mount it as an ext2 or ext3 file system and you can save your data..)
> Existing Wubi/Lubi installations can be upgraded to an installation on a dedicated partition via LVPM. The main site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).
or
simple attach them to be a virtual filesystem on your xp...after that you can move your data to your fresh install too...
> How can I access the Wubi files from Windows? There are a few Windows applications that can mount ext2-based file systems. See for instance: 

[LIST]
[*][http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) 
[*][http://www.fs-driver.org/](http://www.fs-driver.org/) 
[/LIST]
The relevant Wubi files you need to access are located under C:\ubuntu\disks\

When you get a solution on the WUBI virtual disk issue just share your experience with us. Thank you!

Regards,
Viktor

---

### Post by KPDXHAM on 2010-01-04
> **HViktor said:**
> Welcome!
I am sorry because I am not a WUBI expert. I use native Ubuntu and I have not experience on it.

Did you try the virtual disk extraction to be a real partition (see WubiGuide Wiki)? (after that you can mount it as an ext2 or ext3 file system and you can save your data..)

or
simple attach them to be a virtual filesystem on your xp...after that you can move your data to your fresh install too...


When you get a solution on the WUBI virtual disk issue just share your experience with us. Thank you!

Regards,
Viktor

Thanks Viktor,
I'm certainly no WUBI expert either, but I am finding out more about it as I continue to try to recover my Ubuntu installation.
I see that both explore2fs and Ext2 Installable File System can access the Linux ext2 and 3 according to their info, but what if WUBI only installs on ntfs?

I did a clean install of Ubuntu onto ext3 partition on the second HDD. I used Ubuntu live cd and Gparted to make an ext3 partiton.
Then booted into xp and started wubi, but wubi could not see the ext3 partition! Probably because xp can not see it either.
So, now I uninstalled wubi / ubuntu from that drive via XP, then used Gparted again and this time made it ntfs like I had been using for a couple months or so with no problem (except the ones I caused..)
Now did fresh install of Ubuntu onto that HDD, did updates to 2.6.31.16 generic, then rebooted and made sure all is working right.
Then booted XP and tried explore2fs again with same results. Unless I choose "All Files" it shows nothing. When I do choose All Files I can see the Ubuntu disks on that drive, but it will not open them just like when it was formatted ext3.

For now I think I'll just start over with this fresh install and then find a safer way to do a backup other than Sbackup.

Thanks for the help!:P

Cliff

---

### Post by felipebarroeta on 2010-05-18
Re: GNOME Power Manager Login Issue
This may or may not be your issue. I have had the problem to occur twice and finally found the culprit in MY case. It was simplebackup. In using SimpleBackup to back up my files to an external hard drive, occasionally it fails to mount the drive correctly. In such cases, if not configured correctly it will simply add a back up folder to your home folder and begin backing up there. That can quickly result in using up so much of your free space that your computer cannot boot properly.

Using a live CD, I went in and deleted the erroneous back ups and then everything booted fine. I also went back into SimpleBackUp Config and clicked the Destination tab and marked the Abort backup if destination directory does not exist box. Its all good now.

Hey man, thanks for that response, that's exactly the problem i'm having now. I could enter with the live Cd, but when I try to delete, it says I don't have the permission. How did you do it?

Cheers!

---

