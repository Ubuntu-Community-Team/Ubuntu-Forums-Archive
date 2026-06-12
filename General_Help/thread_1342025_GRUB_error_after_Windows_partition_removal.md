---
title: "GRUB error after Windows partition removal"
date: 2009-11-30
forum: General Help
---

### Post by lmerrill on 2009-11-30
Hello everyone,
 
I am new to Ubuntu and to the Ubuntu community forums as well. Therefore, if this topic is in the wrong location, please let me know in your reply so I am aware for future reference. 
 
I am a visuallly impaired computer user who installed Ubuntu 9.10 last week. Because I already had Windows XP Media Center Edition 2005 on my machine, I chose to use the "largest amount of continuous free space" during Ubuntu installation. 
 
Installation of Ubuntu was successful, and I experienced no problems until I tried to do some partition editing. As I said above, I had installed Ubuntu on the same hard drive as my Windows XP machine. The capacity of this had drive is 500 GB, with Ubuntu taking up about 192 GB, give or take a few. 
 
I wanted to get rid of my Windows XP installation entirely so that Ubuntu could use the entire hard drive, as I want to run a Web server on the machine and so will need as much free space as possible for the server and my clients' Web sites.
 
I booted from the Ubuntu 9.04 Live CD (as my 9.10 Live CD is not working correctly) and loaded up the GPartEd partition management utility. I then deleted the partition that contained mfy Windows XP installation and resized the Linux partitions so they took up the entirety of the drive. The operations were applied successfully, however after rebooting my machine I received the error:
 
[FONT=Courier New]NTLDR is missing.[/FONT]
[FONT=Courier New]Press Ctrl+Alt+Del to reboot.[/FONT]
[FONT=Courier New][/FONT] 
I realized then that the partition I removed contained the information needed to boot up my Ubuntu machine - I believe it's the "GRUB boot loader", but please correct me if I'm wrong.
 
Booting again from the Live CD, I ran the following commands at the Terminal to re-install GRUB based on instructions I had read in a post on these forums:
[FONT=Courier New]sudo grub[/FONT]
[FONT=Courier New]grub> find /boot/grub/stage1[/FONT]
[FONT=Courier New][/FONT] 
And received the following error:
 
[FONT=Courier New]Error 15: File /boot/grub/stage1 not found.[/FONT]
[FONT=Courier New][/FONT] 
Apparently GRUB seems to be broken on my machine. I looked on my hard drive and found the /boot/grub directory, but it seems to be missing some files.
 
So basically the bottom line is I can't boot into my Ubuntu installation, but I can't restore / re-install GRUB either because required files are missing. 
 
I have searched all across the Internet for resolutions to this isue, but am unable to find anything which is why I am posting here. I apologize if this issue has already been posted, as after doing a thorough search of these forums I am unable to find a resolution. 
 
Here are some of the specifications of my machine (not sure if this is required for new posts or not):
[LIST]
[*]**Processor: **Intel Celeron CPU 2.40 GHz
[*]**RAM: **1 GB
[*]**Primary hard disk size: **500 GB (where Ubuntu installation is installed)
[*]**Secondary hard disk size: **250 GB
[*]**Installed version of Ubuntu: **9.10 (32-bit)
[*]**Live CD version: **9.04 (32-bit)
[/LIST]I would like to thank the Ubuntu community in advance for reading this post and for possibly replying with assistance on this issue. I appreciate all of the hard work, time, rsources, and effort that goes into the Ubuntu project. I extremely enjoy the Ubuntu operating system and think that it is so much better than Windows.
 
Thanks again for your assistance,
-Logan Merrill

---

### Post by oldfred on 2009-11-30
To understand where everything is installed, please download and run this script. You can download and run from the liveCD:

Boot Info Script 0.37 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
louieb's 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
[http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
caljohnsmith
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script037.sh 
sudo ./boot_info_script037.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by lmerrill on 2009-11-30
Thanks for your quick response! I have downloaded and ran the boot info script. Below is the information in the RESULTS.txt file. Let me know if there is any other information you need to assist me in resolving this issue.

Thanks.

============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaa9d7a7f

Partition  Boot         Start           End          Size  Id System

/dev/sda2                  63   976,768,064   976,768,002   5 Extended
/dev/sda5                 126   970,807,949   970,807,824  83 Linux
/dev/sda6         970,808,013   976,768,064     5,960,052  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="20023254-8592-4fc5-bbe4-a6362f392f39" TYPE="ext4" 
/dev/sda6: UUID="db4149c8-8387-4a71-ac35-979b5f8544fe" TYPE="swap" 
/dev/sdb1: UUID="BA14FFB414FF71AD" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 20023254-8592-4fc5-bbe4-a6362f392f39
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
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 20023254-8592-4fc5-bbe4-a6362f392f39
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=20023254-8592-4fc5-bbe4-a6362f392f39 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 20023254-8592-4fc5-bbe4-a6362f392f39
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=20023254-8592-4fc5-bbe4-a6362f392f39 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 20023254-8592-4fc5-bbe4-a6362f392f39
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=20023254-8592-4fc5-bbe4-a6362f392f39 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 20023254-8592-4fc5-bbe4-a6362f392f39
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=20023254-8592-4fc5-bbe4-a6362f392f39 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 923cca503cca2f53
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=20023254-8592-4fc5-bbe4-a6362f392f39 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=db4149c8-8387-4a71-ac35-979b5f8544fe none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
  16.0GB: boot/initrd.img-2.6.31-15-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .9GB: boot/vmlinuz-2.6.31-15-generic
  16.0GB: initrd.img
    .5GB: initrd.img.old
    .9GB: vmlinuz
    .5GB: vmlinuz.old

---

### Post by oldfred on 2009-11-30
If you were getting a grub stage1 error I think you tried to install grub legacy to the MBR but now it shows grub2 (1.97).

If you switch drives in BIOS do you boot ok into windows? If so the os prober as part of update-grub should find it. If not fix it now before the next step. 

Switch back and reinstall grub2 per the instructions for grub2. The windows entry in grub.cfg is still for your old install in sda1 which is gone. After any change to your system you should run update-grub. IF that does not erase the sda1 entry and put in an entry for sdb1 with mapping come back for a manual entry to try.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Other grub2 info:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by lmerrill on 2009-11-30
Please correct me if I'm wrong, but I think you may have misunderstood a portion of my first post. In it, I mentioned that I had completely removed Windows XP by erasing the partition it was on, which also contained boot information. Therefore even if I were to switch the hard drives I would be unable to boot to Windows as it doesn't exist on any partition of any of my two drives.
 
I followed the instructions at the Ubuntu Help Site using the link you gave me regarding the re-installation of GRUB 2. However, I used the Ubuntu 9.04 Live CD instead of the 9.10 Live CD recommended on the help page, as my 9.10 Live CD is not starting properly. This is what may have contributed to the failure of the re-installation of GRUB 2. Everything worked fine -- I received no error messages -- until I rebooted my machine. I still got the same "NTLDR is missing" error message as before. I am trying to reinstall GRUB 2 on another partition, thinking that I may have installed it on the wrong partition the first time, and will post the results when finished. 
 
Note that because I am running the 9.04 Live CD, I don't know if what I install using the steps provided on the Ubuntu help page will actually be GRUB 2 or the legacy GRUB.

---

### Post by oldfred on 2009-11-30
The script says you still have windows in the MBR of sdb adn windows in sdb1 but missing the boot files. If you do not want windows that is fine.:D

If you are getting the ntldr missing that is from windows boot and no windows. Your BIOS must be booting sdb. Try switching it to see if sda will boot ok with ubuntu.

Edit:

Is one drive Sata and the Other Pata? BIOS, Grub, Windows, and Ubuntu do not always order the drives the same. The first drive in BIOS will be the boot drive, but grub may think that is the second and Ubuntu calls it sdb.

---

### Post by lmerrill on 2009-12-01
There's nothing on my second (250 GB) hard drive, "sdb", except some important files for re-installing drivers on Windows - files I've downloaded from the Internet, not files provided by my computer manufacturer. In other words, Windows was installed on my first (500 GB) hard drive, "sda", and has been removed, or so I thought. I don't know why the script results say Windows is installed in "sdb".
 
Is there any way I can use GRUB as my MBR instead of Windows? According to your reply, if I use GRUB I won't get the "NTLDR missing" error, right?
 
Thanks again for your posts. Remember that I am unable to boot from the 9.10 Live CD and have to use the 9.04 CD.

---

### Post by ranch hand on 2009-12-01
You are going to need a 9.10 (or 10.04 testing) Live CD to correct this problem.  You have changed the entire partition table and your grub does not in any way know this.

You need to use these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You know where to get the 9.10 CD.  The "testing" CD (only if you can't get the 9.10 to work) is at;

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The reason that you need 9.10 is you are using commands for grub2 and this will not work with the 9.04 CD.  9.04 uses grub-legacy.

---

### Post by oldfred on 2009-12-01
Ranch Hand is correct that you need a 9.10 CD to repair Grub2 but you have not yet booted with the grub2 in sda. The ntldr error can only be if your BIOS says to boot from sdb. Switch drives in BIOS before trying to reinstall to see if the grub2 works. The script says grub1.97 in sda links to partition 5 which is correct.

---

### Post by lmerrill on 2009-12-02
I fixed the machine, finally!
 
I figured out, thanks to the help of everyone who replied to this thread, that I was receiving the ```
NTLDR is missing.
Press Ctrl+Alt+Del to restart.
```
 
error message because my BIOS was trying to boot to my "/dev/sdb" hard drive, which apparently contained my machine's master boot record. I went into my BIOS settings and temprarily disabled the second drive, then restarted my computer, only to be presented with a GRUB prompt. 
 
I typed the following commands into the prompt to try and re-install GRUB:
 
```
grub> root (hd0,4)
grub> setup (hd0)
```
 
The installation completed without any errors, but after restarting again I was still returned to the GRUB prompt. After re-reading one of the replies made to this thread, I figured out why - I still had the legacy version of GRUB insstalled rather than GRUB 2. 
 
Since I couldn't get the 9.10 Live CD or the 10.04 (Testing) Live CD to boot, I had to install Windows to my "/dev/sdb" hard drive and run the Ubuntu Windows Installer to make a "live" version of Ubuntu inside Windows. I was then able to re-install GRUB 2 following the directions at the Ubuntu Wiki page given to me in a previous reply. 
 
So now GRUB works perfectly and my Ubuntu machine boots up without a problem!
 
I would like to say a huge thank-you to everyone who has helped me resolve this issue. I am beginning to feel that I will definitely enjoy using Ubuntu Linux over Windows, even if I have to deal with issues like this--because after all that's how you learn and become a better techie!
 
Thanks again everyone!

---

