---
title: "Moving from Vista to Ubuntu 9.10, can't boot"
date: 2010-04-04
forum: General Help
---

### Post by agar_agar on 2010-04-04
Hi everyone.
I'm an absolute beginner though I'm pretty good with PCs. Recently I decided to remove Vista from my Pc and put Karmic Koala in its place. Instead, I formatted C: then created a new partition and put Ubuntu there but now it won't even boot!. All it does is stay on the logo screen and flash the Caps LED. Booting on 'safe mode' only works until the message:  gave up waiting for root device. 

I'm sure there are a lot of guides to correct this error but I'm a Terminal newbie and can't grasp them easily. Could anyone direct me to a very basic guide to boot problems in Ubuntu?

Thanks.

---

### Post by scrooge_74 on 2010-04-04
not sure, but maybe you could try reinstalling again, if Ubuntu is going to be the only system there, just tell it to use the entire drive.

---

### Post by duckleet on 2010-04-04
try to reinstall the os that should help

---

### Post by Nisal on 2010-04-04
what the method u used ? i mean when partitioning ? manual configuring o ?

---

### Post by ngronewold on 2010-04-04
Good advice, just reinstall and let Ubuntu take over your entire drive.  I did exactly what you did -- put the Ubuntu CD in a Windows Vista pre-installed laptop.  Opted to wipe Vista completely out and let the new OS stretch its legs.  Works beautifully, minus the occasional quirk that I can usually find a fix for in the Forum.

---

### Post by gzarkadas on 2010-04-04
Try [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions); it may be of help.

---

### Post by agar_agar on 2010-04-04
> **ngronewold said:**
> Good advice, just reinstall and let Ubuntu take over your entire drive. I did exactly what you did -- put the Ubuntu CD in a Windows Vista pre-installed laptop. Opted to wipe Vista completely out and let the new OS stretch its legs. Works beautifully, minus the occasional quirk that I can usually find a fix for in the Forum.
> **Nisal said:**
> what the method u used ? i mean when partitioning ? manual configuring o ?
 
Thanks guys, I wasn't expecting such a fast response. In most other forums I wait a day or two for answers. 
Ok so, I reinstall and that should do the trick? That easy? 
 
The method I used is this: I formatted C: but installed Karmic on another partition, let's call it D: I did so because from time to time I need to use VisualStudio on Windows so I thought I wouldn't be getting rid of it just yet. I originally installed Win7 on top of Vista but didn't keep the windows.old folder. That ruined my boot sector because Seven wouldn't boot anymore. That's when I decided to try Ubuntu and this is where I am now. 
 
I remember something about Vista's bootmgr and Grub not being compatible. Any thoughts? Thanks!

---

### Post by itiswhatitis on 2010-04-04
I do remember a while back that Vista and Grub had some issues working together.  I did not run Ubuntu as a dual boot with Vista...

I did a quick google, which confirmed that the NT Boot Loader for Vista interracting with Grub did cause problems.  They typical solution was to first let the Vista Boot Menu come up, and create an item in that boot menu to point to the Grub Boot.

It seems like a messy solution to me...  

If your boot sector is hosed, here is the Windows fix.  (yeah, I'm a windows system admin too *sigh*)

Put your Windows 7 CD in, and reboot into the installer.
Pick "Repair Your Computer__" to access the System Recovery window. 
Choose "Command Prompt" 
Type BootRec.exe /FixMBR

That should put Windows Boot back as your only option.  You can then reinstall Ubuntu into your other partition and hopefully get up and running.

Of course - make sure you research the command and process before you do - so that you understand what you are doing.  :-)

---

### Post by agar_agar on 2010-04-04
> **itiswhatitis said:**
> 

Put your Windows 7 CD in, and reboot into the installer.
Pick "Repair Your Computer" to access the System Recovery window. 
Choose "Command Prompt" 
Type BootRec.exe /FixMBR

That should put Windows Boot back as your only option.  You can then reinstall Ubuntu into your other partition and hopefully get up and running.

So, it is a complete reinstall, then. I was thinking I could simply edit the menu.lst so it included my Vista loader too (right now it only sees Ubuntu and the ACER recovery boot). 
Please, before I do it, could you tell me how to completely wipe the Vista boot sector and install Ubuntu's on top? As if Vista had never been there? Also, do you know if MS SQL server Express will run fine on something like Wine or even, a Virtual Environment?
Thanks a lot!

---

### Post by itiswhatitis on 2010-04-04
I don't imagine it has to be a complete reinstall. :-/  

What I suggested would get your Windows up and running again.  (basically putting the windows boot loader back)

I would suspect there is a way to use the live CD to put grub back and set it all up, without a reinstall... but that certainly is out of the realm of my experience.

You may have some luck with those applications and wine, as an alternative, check out crossover @ [http://www.codeweavers.com](http://www.codeweavers.com).  It's based on wine, but not free.  They have a compatibility database that will tell you if the applications you want will work, and roughly how well they *can* work in their emulator.

You could also look at setting up a Windows install in VirtualBox or VMWare (and run Windows inside Ubuntu).  Then you get the best of both worlds, the apps you need in Windows and the joy of Ubuntu.  :-)

---

### Post by agar_agar on 2010-04-04
> **itiswhatitis said:**
> I don't imagine it has to be a complete reinstall. :-/  

What I suggested would get your Windows up and running again.  (basically putting the windows boot loader back)

Thanks, I've tried that already.
I'm afraid nothing I've tried is working. Maybe what I want to hear is not possible without a working Windows. So I'm letting ubuntu take over the whole drive this time. 
It would have made me much happier if some obscure lil' app could fix this for me. Alas, there's none.

---

### Post by oldfred on 2010-04-04
What version of Ubuntu did you install. Separate partition or wubi in the windows NTFS partition?

wubi has a problem that is easy to fix. Loading the correct boot loader requires knowing which version of windows or grub you have.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want us to review your install configuration, run this script from a liveCD:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by agar_agar on 2010-04-04
> **oldfred said:**
> 
If you want us to review your install configuration, run this script from a liveCD:
Boot Info Script courtesy of forum member meierfra

Sure! I'll do exactly that.

I must comment that performing the last step provided in 
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)](http://ubuntuforums.org/showthread.php?t=1014708) 
returned an error. Whether it was 'device not found' or something else I don't remember, I had to turn off the pc.

Here's the troublesome step:
> And then, to reinstall the grub:
Code:
sudo grub-install --root-directory=/media/sda5 /dev/sda
Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

I'll be updating.

/EDIT: And here's the RESULTS.txt
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfaca1d1f

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2    *     25,167,872   189,020,789   163,852,918   7 HPFS/NTFS
/dev/sda3         189,020,790   488,392,064   299,371,275   f W95 Ext d (LBA)
/dev/sda5         189,020,853   218,066,309    29,045,457   7 HPFS/NTFS
/dev/sda6    *    218,066,373   259,015,994    40,949,622   7 HPFS/NTFS
/dev/sda7         259,016,058   415,087,469   156,071,412   7 HPFS/NTFS
/dev/sda8         415,087,533   485,291,519    70,203,987  83 Linux
/dev/sda9         485,291,583   488,392,064     3,100,482  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 3965 MB, 3965714432 bytes
255 heads, 63 sectors/track, 482 cylinders, total 7745536 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2733f666

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            128     7,745,535     7,745,408   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8008D1E008CE54A                       ntfs       PQSERVICE                     
/dev/sda2        6080CDBF80CD9BC2                       ntfs       ACER                          
/dev/sda5        01CACBB709F3B260                       ntfs       Jolicloud                     
/dev/sda6        394567796BDF1EE1                       ntfs       Akenathon                     
/dev/sda7        01CACBB70B8AA610                       ntfs       Robby                         
/dev/sda8        5bdf40bf-78d2-4369-970b-ca96dcc0cdf8   ext4                                     
/dev/sda9        d1b92c40-94b0-4474-a90f-e8534de418ee   swap                                     
/dev/sdc1        C2BA-0B9F                              vfat       SHART-III                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda8        /media/5bdf40bf-78d2-4369-970b-ca96dcc0cdf8 ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 5bdf40bf-78d2-4369-970b-ca96dcc0cdf8
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 5bdf40bf-78d2-4369-970b-ca96dcc0cdf8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5bdf40bf-78d2-4369-970b-ca96dcc0cdf8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 5bdf40bf-78d2-4369-970b-ca96dcc0cdf8
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5bdf40bf-78d2-4369-970b-ca96dcc0cdf8 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f8008d1e008ce54a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=5bdf40bf-78d2-4369-970b-ca96dcc0cdf8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=d1b92c40-94b0-4474-a90f-e8534de418ee none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 213.4GB: boot/grub/grub.cfg
 213.3GB: boot/initrd.img-2.6.31-14-generic
 213.3GB: boot/vmlinuz-2.6.31-14-generic
 213.3GB: initrd.img
 213.3GB: vmlinuz


```

/EDIT2: @oldfred  ...sorry, to answer your question I installed from ISO image on a separate partition at the end of the drive. I didn't have Windows on my pc enough time to run wubi from it haha.
Thanks for your help!

---

### Post by oldfred on 2010-04-04
I see two boot flags, you can only have one and on a primary partition. Windows uses that to know which windows partition is the boot and any later windows installs copy boot files to that partition. You need to remove the one on sda6 with gparted, disk utility or linux command line.

Your grub seems to be missing core.img. Did you have any errors at the end of your install? You can reinstall grub by chrooting into your system or total Ubuntu reinstall using manual so you reuse the current partitions.  I can give you instructions on chrooting into your system and doing a reinstall of grub.

---

### Post by agar_agar on 2010-04-04
> **oldfred said:**
> I see two boot flags, you can only have one and on a primary partition.

I see it too. It must be empty, but how did it become boot? My guess is the Windows Recovery Disk 'thought' it was the primary.

> Your grub seems to be missing core.img. Did you have any errors at the end of your install? You can reinstall grub by chrooting into your system or total Ubuntu reinstall using manual so you reuse the current partitions.  I can give you instructions on chrooting into your system and doing a reinstall of grub.

Total reinstall would be fine, but I'm afraid I still need Windows to do some Visual Studio work. So I'd prefer if you teach me how to reinstall grub. I'm a good learner. heh ;)
/EDIT: I had no errors during install.

---

### Post by oldfred on 2010-04-04
This is a full chroot from a liveCD or other working install, # is comments:

Of course you must first know what partition you want to mount, in this example I'm using sda3:

sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).

apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
#apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
#purge old and reinstall new to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by agar_agar on 2010-04-14
Ok. Finally, I gave up and let Ubuntu take over the whole drive. I even had it write on top of the Acer recovery partition I didn't want to lose. I had done a back up though.

Thanks for your kind advice anyway.

P.S. I'm not sure it is caused by my strange previous setup (I didn't wipe the disk prior to installation) but after installing and updating 9.10 it returns the same recurrent message after every boot which ends with the line: "Checking battery status ...done" then shows a prompt where I can't type anything without getting some kind of cryptic characters. Help?
here`s the related thread [http://ubuntuforums.org/showthread.php?p=9119897#post9119897](http://ubuntuforums.org/showthread.php?p=9119897#post9119897)

---

