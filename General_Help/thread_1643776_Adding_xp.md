---
title: "Adding xp"
date: 2010-12-12
forum: General Help
---

### Post by katykat on 2010-12-12
This is my configuration:

Primary Channel Master: SDA1 - Removable Hard Drive - Currently 120Gb Full XP Install
Primary Channel Slave: CD/DVD reader/burner

Secondary Channel Master: SDB1: Jaunty
Secondary Channel Slave: SDC1: Meerkat fully loaded. 

I am in the process of deconstructing Jaunty to be replaced with a Linux web server testbed, a subject for a different thread. 


Note that SDA1 is REMOVABLE.
When I have a 15Gb junk XP drive in it with Grub on it, it will boot fine into Grub2 and give the the option of the 2 Ubuntus and XP. 

The current XP drive is a DEVELOPMENT SYSTEM and it has not been exposed to Grub - it boots directly into XP. GRUB IS NOT ACCESSIBLE. 

I would like to enable it to boot into Grub, but in the safest method possible. 


So, to summarize:
How to get Grub2 on an XP primary drive, and if possible restore the MBR if needed (Recovery Console is enabled on it, so I assume fixmbr would do the trick. Is there a way to reverse that if necessary and restore the Grub2 MBR???)

---

### Post by rickyrockrat on 2010-12-12
You need to add grub to whichever disk is permanently installed, which we all hope is not the XP drive.  You then add XP to the grub menu, and make sure the BIOS boots that drive first in the list of HDDs, and you should be golden.

---

### Post by tredegar on 2010-12-12
You just need to install grub2 to the MBR of the 120GB XP drive
But you cannot boot to linux when the XP drive is present
So you need to plug in the 120GB drive, boot from a live CD and follow the instructions [here]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html") to install grub2 to the MBR of /dev/sda.

In those instructions you'll have to mount "your ubuntu partition", but you have two of them. You need to choose one only. I would choose your sdc1 meercat partition to hold the grub2 config files. Just remember that when you want to **update-grub** you should do it running from meercat, because that is the partition where the config files are.

Once you have run **update-grub** there will be entries for win and win-recovery.

I haven't run win since '98, so I have no idea how to restore a windows MBR, but if you get into trouble, some win-wise person will help you.

---

### Post by rickyrockrat on 2010-12-12
ANY MBR is the first 512 bytes, so running dd will copy it:

```
dd if=/dev/sdx of=mysaved.mbr bs=512 count=1
```

This is the whole disk in Linux, i.e. /dev/sda, *not* /dev/sda1.

And restore it. Just make sure you get the right drive!

Sorry I didn't read the original post carefully. Too much multitasking.

Here's a good article on the MBR:

[http://home.teleport.com/~brainy/fat32.htm](http://home.teleport.com/~brainy/fat32.htm)

---

### Post by oldfred on 2010-12-12
Be careful copying the full 512 MBR as that includes the partition table. If from a different drive or you change partition table you will restore the old version which can lead to problems.

If you just want the boot loader:
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1
Zero out MBR and partition table
dd if=/dev/zero of=/dev/sda bs=512 count=1
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

I have seen where some have copied the mbr to mbr.bin and then used windows boot.ini to load the mbr.bin to boot Ubuntu.

Old systems only boot primary master, so how is it removeable and still bootable, or do you always have to have a drive plugged in? 

You can use a windows CD to run fixMBR to restore windows boot loader. You can also install Lilo's MBR which works just like windows in that it jumps to the active (boot flag) partition. From Ubuntu liveCD or just about any linux repair CD:

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by katykat on 2010-12-13
> **rickyrockrat said:**
> You need to add grub to whichever disk is permanently installed, which we all hope is not the XP drive. 


THAT is the thing. Linux on the second channels are the *permanent* drives. 

SDA on the Primary channel is *removable*.  The XP drive is basically half Linux anyway with Cygwin, and nearly all the Open Source development tools for Win. I am developing a web site, and want to do it in Win first before I port it over to Linux. 

However, currently when I want to boot into Linux I yank the 120gb Xp and toss in a small XP drive that was present when I installed Meerkat.  And after meerkat boots the first thing that happns when I log in is for that XP drive to be shut off. 

What I am thinking of now is wondering if there is a simple way of making a BootCD and just having it boot to that first, with grub2 (or whatever) offering a menu and defaulting to Meerkat. 

Booting to a USB thumb drive may be simpler, but my experience is that they do not like being left in place, and develop problems after a while. 

This scenario would give me more flexibility over SDA as then I may be able 'hopefully' to boot ANY hard drive I put in there. 

Meerkat is helluva lot faster than Jaunty, but still lags notably behind XP in file transfer speed. That is one reason I would boot into a smaller XP drive, and leave the large one off and not accumulating wear and tear. 

The small drives are basically throwaway.

---

### Post by katykat on 2010-12-13
> **tredegar said:**
> You just need to install grub2 to the MBR of the 120GB XP drive
But you cannot boot to linux when the XP drive is present
So you need to plug in the 120GB drive, boot from a live CD and follow the instructions [here]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html") to install grub2 to the MBR of /dev/sda.

In those instructions you'll have to mount "your ubuntu partition", but you have two of them. You need to choose one only. I would choose your sdc1 meercat partition to hold the grub2 config files. Just remember that when you want to **update-grub** you should do it running from meercat, because that is the partition where the config files are.

Once you have run **update-grub** there will be entries for win and win-recovery.

I haven't run win since '98, so I have no idea how to restore a windows MBR, but if you get into trouble, some win-wise person will help you.

--------------------------------------------------
The instructions seem to say: 

Boot to the live CD then:
mount /dev/**sdc1** /mnt
grub-install --root-directory=/mnt/ /dev/sdc
Reboot then
update-grub
(Meerkat is on SDC1)

But grub2 is *already* on Meerkat. 
I seen how finicky grub2 can be so dont want to do anything unnecessary. 

And wouldnt I need to chroot to SDC1 / directory (as well as mounting the processing and temp dirs there).
And *then* perhaps directly run grub-update? 

I may need to test this on a junk drive....

---

### Post by katykat on 2010-12-13
> **rickyrockrat said:**
> ANY MBR is the first 512 bytes, so running dd will copy it:

```
dd if=/dev/sdx of=mysaved.mbr bs=512 count=1
```This is the whole disk in Linux, i.e. /dev/sda, *not* /dev/sda1.

And restore it. Just make sure you get the right drive!

Sorry I didn't read the original post carefully. Too much multitasking.

Here's a good article on the MBR:

[http://home.teleport.com/~brainy/fat32.htm]("http://home.teleport.com/%7Ebrainy/fat32.htm")


Unfortunately that nice article is about FAT32. 
The XP drives are all NTFS, so not sure if would dd would be appropriate there. 
Or what the drive parameters would be if done in XP where I have all the Posix ports.
The man page there is clear as mud. 

I assume the utility is on the Live CD so that gives encouragement. 

The good thing is that on the XP recovery console I do have fixboot, and fixmbr. 

Just not so sure whether I would need both if something went wrong.

---

### Post by rickyrockrat on 2010-12-13
kitykat,
That nice article is about the MBR, which is the same for NTFS, Fatxx, Linux, etc. That was why I gave you the link.  dd works on anything.

oldfred is right, the code he pasted is safer, however I did note that it needed to be used on the right drive.  Blindly dumping anything on the first 512 bytes is a great way to totally hose a drive, since it does overwrite the partition table.

What I don't understand is if those linux drives are permanent, why you don't just add the grub entries there?  Since they are permanent, you could add 10 entires that were bogus until you had that particular drive installed, then invoke the grub entry for the drive installed. Sorta goes with your 'boot anything' idea.

Another way to pull this off, and it's much nicer than rebooting is to use VirtualBox.  Perhaps you're not using it for performance reasons?  With VirtualBox you could have XP, Meerkat, etc all running at the same time.

You can just edit your grub.conf/grub.cfg (why do they keep changing it?!) in whichever drive you use to boot from.

---

### Post by oldfred on 2010-12-13
Herman has info on using grub to boot. I think his rescue CD is just a boot to a command line, but I used his instructions to create a bootable USB and you can manually create a grub.cfg and include that in the CD. 

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by katykat on 2010-12-14
> **rickyrockrat said:**
> kitykat,
That nice article is about the MBR, which is the same for NTFS, Fatxx, Linux, etc. That was why I gave you the link.  dd works on anything.

What I don't understand is if those linux drives are permanent, why you don't just add the grub entries there?  Since they are permanent, you could add 10 entires that were bogus until you had that particular drive installed, then invoke the grub entry for the drive installed. Sorta goes with your 'boot anything' idea.

Another way to pull this off, and it's much nicer than rebooting is to use VirtualBox.  Perhaps you're not using it for performance reasons?  With VirtualBox you could have XP, Meerkat, etc all running at the same time.

You can just edit your grub.conf/grub.cfg (why do they keep changing it?!) in whichever drive you use to boot from.

A question here...
If the MBR is the same regardless of file system, with the exception of the Partition Table, if none of the XP drives were partitioned : Would the same MBR copy work on all the XP drives? 

Right now the machine is in Windoze as I am backing up the test XP drive and the Jaunty remnants, about half a million files, so I will not be able to test till tomorrow. 

I used Cygwin pull the MBR and it seems to work fine as far as copying. 

I only have 1.2G of memory on the machine, so i dont think virtualization would run too quick. 

What I will probably do is test with a junk XP drive by installing Fedora 14 into where Jaunty was. That should write to the XP drive partition table and create a grub menu. 

If all works well, then put the master XP drive in, and repeat the process. 

I'll prolly have one helluva grub menu....

Lilo scares the bejeezus outta me. In the old days I used to use loadlin, which would boot the kernel right from Windoze from a config.sys menu. 

Its good knowing what the options are though, and I am particuarly intrigued by the idea of making the Linux drives part of the boot.ini menu. Will need to look into that option.

---

### Post by katykat on 2010-12-14
> **oldfred said:**
> Herman has info on using grub to boot. I think his rescue CD is just a boot to a command line, but I used his instructions to create a bootable USB and you can manually create a grub.cfg and include that in the CD. 

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")


This last post seems like a mountain of info to goover, and I want to digest slowly. 

But its GOOD INFO!!

Many thanks. 

Off to bed..

---

### Post by oldfred on 2010-12-14
Windows boot is all the same. Not sure if there are slight differences between XP & before & Vista & later in MBR. There is in PBR - partition boot sector. Att the windows boot loader (and Lilo) does is review partition table and look for boot flag (active partition in Windows speak) and then jump to that partitions PBR. Lilo will let you directly boot XP (as only system) in an extended partition where windows will not. Windows only boots (first system) from a primary partition.

See this on Windows multiboot with mention of Linux at end. Article is long but just reviewing pictures is worthwhile on its own.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by katykat on 2010-12-15
I will need to print that out and study it for a spell. 

I gave it a shot today, and was half successful. 

To clarify, I have three XP drives here:
1. BFG = The whole XP thing, untouched by Linux. 
2. XAMPP = Web server drive, also without Linux exposure.
3. HONEYPOT= Test drive, sometimes test out downloaded trojans on this one. Has GRUB2 bootsector on it. 

I booted to XAMPP and installed Fedora 14 to the drive (not partition) where Jaunty was. 
Fedora offered no menu screen and jumped right into, well, Fedora...
Oops - no grub2. 

Restored XAMPPs MBR and pulled it. 

Plugged in HONEYPOT, booted right to Meerkat, and updated Grub. It found Fedora and added it to its menu. Fedora, Meerkat, and XP in HONEYPOT boot fine together. 

BFG is still the question mark. 
It looks like will have to copy the MBR out of HONEYPOT and place it on BFG. 

Or else just plug in BFG, boot to a Linux CD, and simply chroot to Meerkat and upadate grub!
(Too simple, perhaps??)

---

### Post by oldfred on 2010-12-15
The minute you have multiple drives and multiple systems you need to use this. I run this before & after every system change to be sure I changed what I thought I changed and to document system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by katykat on 2010-12-17
> **oldfred said:**
> The minute you have multiple drives and multiple systems you need to use this. I run this before & after every system change to be sure I changed what I thought I changed and to document system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.


Well, I tried copying bootsector with grub on it to virgin XP drive - no dice. Got grub rescue menu. 

Tried chrooting to Meerkat from CD and running grub-update, grub-update AND grub-install - no dice. 

Chrooting and trying to install Grub directly to the SDA XP drive - no luck there either. 

What WORKED was the RESCATUX Grub Repair CD. Booted into the Safe mode, and while the instructions were as clear as mud, I set it with XP as first, Fedora Second, and Meerkat third. 

It then booted into the Normal Grub2 menu.

Whats needed is a good utility for making grub fully portable, especially as Linux should be portable over machines of similar architecture. Rescatux seems to work, but is very unintuitive, especially at the main menu. 

There is a windoze utility called MBRFIX which is a simple means of managing and backing up the MBR at the Win command line. 
 



```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sdb2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

vg_linux-lv_root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

vg_linux-lv_home: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg_linux-lv_swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,057,614    30,057,552   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sdb2           1,026,048   234,440,703   233,414,656  8e Linux LVM


Drive: sdc ___________________ _____________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   226,764,799   226,762,752  83 Linux
/dev/sdc2         226,766,846   234,440,703     7,673,858   5 Extended
/dev/sdc5         226,766,848   234,440,703     7,673,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/vg_linux-lv_home e6595930-1dbc-4d08-9f14-b91f5c4cf730   ext4                                     
/dev/mapper/vg_linux-lv_root d2e83cbf-b0e2-48b4-8262-a1b249bafa17   ext4       _Fedora-14-i686-              
/dev/mapper/vg_linux-lv_swap 3fbf5767-11c8-424d-95b4-789325f8c1ac   swap                                     
/dev/sda1        7805-F230                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ec18a752-a627-45ae-8611-4b5ab94773e7   ext4                                     
/dev/sdb2        TQQgbV-7os1-T0r1-G1PU-oFUw-UrNV-70U7w2 LVM2_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        2d3a720f-114d-4ac6-82c3-6cd28a8bed9c   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        dbe1e2df-1717-496f-88c9-d18e579e0688   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
vg_linux-lv_home
vg_linux-lv_root
vg_linux-lv_swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/jaunty            ext4       (rw)
/dev/sda1        /media/7805-F230         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=0,gid=0,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

============================= sdb1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd1,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_linux-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd1,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd1,0)
    kernel /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/vg_linux-lv_root rd_LVM_LV=vg_linux/lv_root rd_LVM_LV=vg_linux/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initramfs-2.6.35.6-45.fc14.i686.img
    .0GB: initrd-plymouth.img
    .0GB: vmlinuz-2.6.35.6-45.fc14.i686

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=2d3a720f-114d-4ac6-82c3-6cd28a8bed9c ro acpi_sleep=nonvs  crashkernel=384M-2G:64M,2G-:128M 
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=2d3a720f-114d-4ac6-82c3-6cd28a8bed9c ro single acpi_sleep=nonvs
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2d3a720f-114d-4ac6-82c3-6cd28a8bed9c ro acpi_sleep=nonvs  crashkernel=384M-2G:64M,2G-:128M 
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=2d3a720f-114d-4ac6-82c3-6cd28a8bed9c ro single acpi_sleep=nonvs
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2d3a720f-114d-4ac6-82c3-6cd28a8bed9c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7805-f230
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Fedora (2.6.35.6-45.fc14.i686) (on /dev/mapper/vg_linux-lv_root)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ec18a752-a627-45ae-8611-4b5ab94773e7
    linux /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/vg_linux-lv_root rd_LVM_LV=vg_linux/lv_root rd_LVM_LV=vg_linux/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "Ubuntu Hardy Heron Symlink Boot" {
    linux    (hd3,1)/vmlinuz root=UUID=afeb6a59-d2e4-4a1e-9893-7c352d5806e6 ro quiet splash
    initrd    (hd3,1)/initrd.img
}
EOF

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=dbe1e2df-1717-496f-88c9-d18e579e0688 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 101.0GB: boot/grub/core.img
  14.4GB: boot/grub/grub.cfg
  50.7GB: boot/initrd.img-2.6.35-22-generic
  50.9GB: boot/initrd.img-2.6.35-22-generic-pae
 102.4GB: boot/vmlinuz-2.6.35-22-generic
 102.4GB: boot/vmlinuz-2.6.35-22-generic-pae
  50.9GB: initrd.img
  50.9GB: initrd.img.old
 102.4GB: vmlinuz
 102.4GB: vmlinuz.old

========================= vg_linux-lv_root/etc/fstab: =========================


#
# /etc/fstab
# Created by anaconda on Wed Dec 15 10:15:06 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/vg_linux-lv_root /                       ext4    defaults        1 1
UUID=ec18a752-a627-45ae-8611-4b5ab94773e7 /boot                   ext4    defaults        1 2
/dev/mapper/vg_linux-lv_home /home                   ext4    defaults        1 2
/dev/mapper/vg_linux-lv_swap swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  97 df e1 66 c9 fb 1b 3c  44 02 82 d6 67 1d 4a f8  |...f...<D...g.J.|
00000010  7a 34 80 44 75 34 44 21  13 31 a9 15 7e 99 c0 32  |z4.Du4D!.1..~..2|
00000020  51 5a 55 95 52 9e b1 e5  44 85 52 9b 1c 52 07 62  |QZU.R...D.R..R.b|
00000030  1c 4f 72 76 40 2f 91 05  0b 78 c7 6a 7e 97 3c fc  |.Orv@/...x.j~.<.|
00000040  ad d4 c0 ea 1c ab d6 aa  0b 1c b2 fa 31 88 4e 28  |............1.N(|
00000050  4f af b2 d0 df a6 41 6a  af cc aa 5f 9a 43 35 2b  |O.....Aj..._.C5+|
00000060  38 94 fe 9b 47 0d 1a 48  8c d3 c9 2f a7 3e 84 99  |8...G..H.../.>..|
00000070  93 64 e5 80 7d 3c 65 a8  6a d5 74 5d 80 0a ac f1  |.d..}<e.j.t]....|
00000080  8a 01 9c 00 bb fc 87 42  7f 6b 90 c9 1c d9 43 9f  |.......B.k....C.|
00000090  ff 5d 29 6d 6d 29 57 c2  44 f3 0b c5 c1 a4 b1 33  |.])mm)W.D......3|
000000a0  00 64 e8 13 f3 ba 8d 08  8f 30 75 54 0d 1a cb 66  |.d.......0uT...f|
000000b0  ed cd 95 67 93 48 00 e3  e3 44 21 cb 93 f8 86 b0  |...g.H...D!.....|
000000c0  99 26 8e 9b 68 86 aa 15  1c 8b 17 18 f8 70 a8 c3  |.&..h........p..|
000000d0  a6 ea d8 3d 95 72 f7 68  a4 98 71 60 ea 47 55 8c  |...=.r.h..q`.GU.|
000000e0  83 bf 6e 43 cf c2 43 03  26 1f 7c 6e f6 20 d4 c4  |..nC..C.&.|n. ..|
000000f0  7b 89 ef c3 19 7f 3a 0a  ef 50 7f a9 58 b7 96 33  |{.....:..P..X..3|
00000100  f0 30 9a ae ae c9 35 32  10 94 eb be 46 14 c0 1b  |.0....52....F...|
00000110  9b 14 51 93 25 8b 49 6a  94 81 d2 de b6 f5 92 53  |..Q.%.Ij.......S|
00000120  ce cb d6 7d c3 2f 62 a4  ac 91 f9 5c be 68 7e 54  |...}./b....\.h~T|
00000130  cf e4 14 1e 3d d0 9c 38  12 5f 5e 2f 29 48 dc ec  |....=..8._^/)H..|
00000140  ed 27 a3 02 00 19 06 a5  53 60 53 1e bf bc 8e fa  |.'......S`S.....|
00000150  70 e5 ee e7 69 15 7c 53  06 c3 e8 ff 17 10 6a 24  |p...i.|S......j$|
00000160  a9 e6 25 c5 fe 5e e0 0a  cf b0 ad 8e 5c a4 61 b5  |..%..^......\.a.|
00000170  d9 41 7e bc 04 0d 97 bd  66 53 37 de ea bb f2 24  |.A~.....fS7....$|
00000180  c5 74 ad a1 4c d2 85 7d  0e a6 07 12 2d 29 e7 a5  |.t..L..}....-)..|
00000190  33 ae e0 e9 a4 1b 6d 56  df 69 b6 94 a0 bb db e8  |3.....mV.i......|
000001a0  42 ea 41 e1 5d 05 d7 42  36 e1 04 93 54 26 e6 e9  |B.A.]..B6...T&..|
000001b0  6f 92 ed cd 5b aa 06 80  74 e0 47 1a d0 b2 00 fe  |o...[...t.G.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 18 75 00 00 00  |............u...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

File descriptor 8 (pipe:[18874]) leaked on lvscan invocation. Parent PID 3923: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvdisplay invocation. Parent PID 3928: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvdisplay invocation. Parent PID 3931: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvchange invocation. Parent PID 2939: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvdisplay invocation. Parent PID 3993: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvdisplay invocation. Parent PID 3996: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvchange invocation. Parent PID 2939: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvdisplay invocation. Parent PID 4052: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvdisplay invocation. Parent PID 4055: /bin/bash
File descriptor 8 (pipe:[18874]) leaked on lvchange invocation. Parent PID 2939: /bin/bash
mdadm: No arrays found in config file or automatically

```

---

### Post by oldfred on 2010-12-17
Either grub or the script often lie about which drive it is booting from, so sda entry probably means sdc1. It looks like if you set either sda or sdc as boot drives Ubuntu will boot.

Can you boot all 3 systems?

---

### Post by katykat on 2010-12-18
> **oldfred said:**
> Either grub or the script often lie about which drive it is booting from, so sda entry probably means sdc1. It looks like if you set either sda or sdc as boot drives Ubuntu will boot.

Can you boot all 3 systems?

Yes, with no problems.

And from any of the three XP drives I use for SDA.

Actually I am amazed that Fedora plays so well with this arrangement - wot, with its old style grub and weird partitioning system. 

I just did a complete update of meerkat - which was blocked for the past few weeks by me putzing with perl, now fixed. No problems.

---

### Post by oldfred on 2010-12-18
Glad it is working. :)

---

### Post by adrian15 on 2010-12-22
> **katykat said:**
> Rescatux seems to work, but is very unintuitive, especially at the main menu. 


Please explain how to improve Rescatux so that it is more intuitive. What menu options names would you have choosen?

Thank you very much!

adrian15

---

