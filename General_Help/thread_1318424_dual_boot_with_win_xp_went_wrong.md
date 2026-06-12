---
title: "dual boot with win xp went wrong"
date: 2009-11-07
forum: General Help
---

### Post by sensay on 2009-11-07
I have two hard drives, one dedicated to ubuntu with three partitions, / /home and swap space.

The second drive has one partition with some files stored and a second partition i intended to install windows xp on. From what i read online i expected a relatively painless procedure because both systems are on seperate hard drives (as foolish as it now seems, i figured it would be simple be a case of choosing which HDD loaded in the BIOS..xp or ubuntu rather than a traditional dual boot) and that if anything went wrong at least one OS would load and id set about repairing the other from there.

When i boot now i simply get a black screen, neither GRUB or the winxp boot screen appear. Changing which hdd i boot from in the bios makes no difference.

Im posting this from a 9.04 live cd

Please help, id really rather recover ubuntu than install it again..

---

### Post by mechro on 2009-11-07
Open a Terminal (Applications > Accessories > Terminal)

Enter the following...

**sudo fdisk -l**

(l = lower case letter L)

Post results here.

---

### Post by sensay on 2009-11-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92629d73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          13       13654   109568000    7  HPFS/NTFS
/dev/sda2           13655       30401   134520277+   b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42796ed3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2553    20506941   83  Linux
/dev/sdb2            2554       38913   292061700    5  Extended
/dev/sdb5            2554        3526     7815591   82  Linux swap / Solaris
/dev/sdb6            3527       38913   284246046   83  Linux

Thanks for the quick reply

---

### Post by mechro on 2009-11-07
That looks OK.

What version of Ubuntu is it? Please, please let it be 9.04 ;) otherwise I'll have to continue reading up on my Grub2 :(

Which did you install first?

---

### Post by Joe Ker1086 on 2009-11-07
Have you looked into system rescue cd, look into it here [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page"), got some pretty useful tools, if you want you can just download testdisk, which can help restore partitions...i know you can use testdisk alone but not sure how it would work when running a live cd.

---

### Post by sensay on 2009-11-07
Unfortunately its ubuntu 9.10..

I had 9.04 originally installed on the larger drive and upgraded to 9.10 just a few days ago, then i installed windows on the smaller drive today.

I should have pointed out in the first message, windows didnt get to completion of installation, it got to the stage where it needed to reboot and continue, however, if im correct the loader should already be installed by that point anyway so the problem remains the same. Just thought i should add that in case it helps.

Thank you

EDIT: Just saw the post above.. If there is anyway i can do this without having to burn off a CD that would be great. I only have dual layer discs here (i really dont wanna use them) and i cant get a cd for about 14 hours, i was kinda hoping to have this fixed before then (if its possible!)

---

### Post by ranch hand on 2009-11-07
Read the link in my sig.  Down the list of links on that post is a link to restoring grub2 from the Live CD.

---

### Post by Joe Ker1086 on 2009-11-07
One other thing. Any time you install windows (apparently whether it succeeds or not) windows will wipe out the MBR of any other OS that is not windows...... Nice right! Try booting up your live cd into recovery mode and run the fixmbr command. I installed windows 7 and it did the same thing to my fedora install, although it could boot into windows.

---

### Post by mechro on 2009-11-07
Well already that sounds like sda has become sdb and vice versa which will confuse bootloaders.

We'll try and fix Ubuntu first.

In **Places > Computer** can you identify which disk is the Ubuntu / partition. It'll be something like disk or disk-1 etc.

---

### Post by Joe Ker1086 on 2009-11-07
Sorry for the double post, you can run the rescuecd from usb drive....but you need the cd to install it i believe...there is some info on that site about installing to usb stick, you might just want to try downloading testdisk....it allows you to write the MBR code to the first sector of the drive. If you need help using it let me know...you dont need to boot it from cd, you just run it within linux, [http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")

EDIT:

I think you can also get it by typing ***sudo apt-get install testdisk*** in terminal

---

### Post by sensay on 2009-11-07
Ok, thanks all for the posts, i am investigating alla dvice given :D

Mechro, when i look in Computer i see the following relevant places:

291.1GB Media (This is named as Disk in the top menu and it contains my home folder)
21.0GB Media (This is named as Disk1 and it contains my root directory

Then i just have my other drives partitions listed.

Cheers

EDIT: Joe Kerl, thanks for the advice. I have never used the tool before so i may have some basic questions when it comes to using it

---

### Post by mechro on 2009-11-07
Can you navigate to /Disk1/boot/grub and find the grub.cfg file? Post the contents of the file here.

---

### Post by sensay on 2009-11-07
There is no file of that name in that directory (hidden files are shown)

---

### Post by mechro on 2009-11-07
:shock::shock: Really.

I need a list...

In a Terminal do...

```
ls /Disk1/boot/grub
```

---

### Post by sensay on 2009-11-07
Er, so entering that command in the terminal just brings up a "No such file or directory' error. I cant find anyway to navigate to disk1 at all either

I can screenshot the folder if that would help?

EDIT: SS attached

---

### Post by mechro on 2009-11-07
Perhaps it was disk1 and not Disk1. Never mind.

You haven't got Grub2, it's the older version so can you post the contents of the **menu.lst** I see in your screenshot.

---

### Post by sensay on 2009-11-07
I tried a lot of variations of disk Disk DiSketc haha, none worked.

Ok, im guessing not having grub2 is gonna be helpful in this case? Must be because i upgraded and did not fresh install

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9b735de-bc58-48d7-a61f-b556e25f93bc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by mechro on 2009-11-07
Hopefully you can just reinstall that but we'll just check the UUID numbers. In a Terminal do...

**sudo blkid**

= lowercase BLKID

Press Enter if you're asked for a password.

---

### Post by sensay on 2009-11-07
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7EC8B858C8B80FFF" LABEL="Downloads" TYPE="ntfs" 
/dev/sda2: LABEL="WINDOZE" UUID="DB75-EDB2" TYPE="vfat" 
/dev/sdb1: UUID="f9b735de-bc58-48d7-a61f-b556e25f93bc" TYPE="ext3" 
/dev/sdb5: UUID="8a116e7c-cc70-4e16-a81a-2a00f8c3093d" TYPE="swap" 
/dev/sdb6: UUID="e6ba346d-9ed6-486e-9d29-61a056768d70" TYPE="ext3" 


What next?

Thanks for the help by the way! Im very grateful you jumped in so quick to assist me

---

### Post by mechro on 2009-11-07
Perhaps I'm just a sad old bugger!;) Thanks for the thanks.

I'll be back soon to tell you what to do next.

---

### Post by Joe Ker1086 on 2009-11-07
I'm tellin you, testdisk is the way to go. or you could try this [http://gag.sourceforge.net]("http://gag.sourceforge.net")

---

### Post by sensay on 2009-11-07
I downloaded testdisk and didnt know how to get it running (I feel so lame, i am a very new linux user!) basically i extracted it and there was no file explaining what to do and running any of the two bundled executable applications did nothing, running it as root from the terminal didnt work either.

Advice?

Thanks

EDIT: GAG seems like a last resort kind of option,id much rather be using the GRUB or windoze loader rather than a third party app, thanks for the link though.

---

### Post by Joe Ker1086 on 2009-11-07
Sorry, i should have explained that a little better, i had the same problem when i first tried using it. go to the executable file for testdisk, right click and go to properties, then open a terminal and type in the file location with the file name as the last / . example   **/home/documents/testdisk-6.11.3/linux/testdisk_linux**

Thats not the exact place its listed (or file name might not be 100% accurate) but that will load it within your terminal windows...you may have to use sudo first

---

### Post by mechro on 2009-11-07
Right, we need to identify how Grub is labelling your partitions/drives so in a Terminal do...

```
sudo grub
```

Press Enter for password. Then you'll get a grub> prompt do...

```
find /boot/grub/stage1
```

Post results here.

---

### Post by mechro on 2009-11-07
Testdisk is good but it's slightly going over the top for a grub re-install. It's more relevant for recovering corrupted or deleted partitions. At the moment it just looks like a problem with Grub.

---

### Post by sensay on 2009-11-07
Ok, got the app running, and chose the analyse option on my larger drive. It shows all the partitions correctly and then gives me a search option.I did this and it finds my ubuntu settings

Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  2552 254 63   41013882
L Linux Swap            2553   1  1  3525 254 63   15631182
L Linux                 3526   1  1 38912 254 63  568492092

when i proceed past this point (selecteing the * Linux partition) it gives me theoption to write boot information to disk.

Do i want to do this?

EDIT: Mechro, i kinda feel that too. Id rather go with a grub re installation if possible (its also a process i feel i should familiarize myself with.)

---

### Post by mechro on 2009-11-07
Have you seen my post above my Testdisk comment?

---

### Post by Joe Ker1086 on 2009-11-07
Ok, If it found your partitions but you didnt change anything writing it to disk will not do anything except tell you to reboot to make changes affective. I would first try the option in the main menu to write MBR code to first sector. That has fixed some of mine in the past.

EDIT:

Mechro may be right.......I have only ever used it where I completely blew out my partition table or deleted data.....but it has almost always worked for me (except with fedora)

---

### Post by sensay on 2009-11-07
Missed it, sorry. 

grub> find /boot/grub/stage1
 (hd1,0)


Joe Kerl, can i come back to you about the testdisk method if this fails? It seems a little complex and im totally unsure of what im doing there. Willing to give it a go if this doesnt work though!

---

### Post by Joe Ker1086 on 2009-11-07
Take my post with a grain of sand for now.....lets just resort to that if Mechro's fix does not work...sorry

---

### Post by sensay on 2009-11-07
A secondary option is always good and testdisk looks like a very useful application for more severe problems than this so im glad to know of it. Cheers

---

### Post by oldfred on 2009-11-07
If you want to know what bootloaders are in each drive this script runs all the commands you have run above as one and gives a lot of extra boot & MBR info, so we can tell what is installed where:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


With 2 drives I would keep ubuntu on one with grub in the MBR of that drive and windows on the other with windows boot in that drive. Since it is difficult to have windows boot Ubuntu, the first drive ends up as the Ubuntu drive so you can add windows to grub. When you do the install this way it does require some swapping of drive order in BIOS to get the drives ordered correctly during the install.

---

### Post by sensay on 2009-11-07
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 219351510.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92629d73

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848   219,342,847   219,136,000   7 HPFS/NTFS
/dev/sda2         219,351,510   488,392,064   269,040,555   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42796ed3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    41,013,944    41,013,882  83 Linux
/dev/sdb2          41,013,945   625,137,344   584,123,400   5 Extended
/dev/sdb5          41,014,008    56,645,189    15,631,182  82 Linux swap / Solaris
/dev/sdb6          56,645,253   625,137,344   568,492,092  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7EC8B858C8B80FFF" LABEL="Downloads" TYPE="ntfs" 
/dev/sda2: LABEL="WINDOZE" UUID="DB75-EDB2" TYPE="vfat" 
/dev/sdb1: UUID="f9b735de-bc58-48d7-a61f-b556e25f93bc" TYPE="ext3" 
/dev/sdb5: UUID="8a116e7c-cc70-4e16-a81a-2a00f8c3093d" TYPE="swap" 
/dev/sdb6: UUID="e6ba346d-9ed6-486e-9d29-61a056768d70" TYPE="ext3" 

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
/dev/sdb6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/WINDOZE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9b735de-bc58-48d7-a61f-b556e25f93bc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        f9b735de-bc58-48d7-a61f-b556e25f93bc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=f9b735de-bc58-48d7-a61f-b556e25f93bc /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=e6ba346d-9ed6-486e-9d29-61a056768d70 /home           ext3    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=8a116e7c-cc70-4e16-a81a-2a00f8c3093d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/menu.lst
   2.8GB: boot/grub/stage2
   2.7GB: boot/initrd.img-2.6.28-16-generic
   2.7GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-wl
   2.7GB: boot/vmlinuz-2.6.28-16-generic
   2.6GB: boot/vmlinuz-2.6.31-14-generic
   2.7GB: initrd.img
   2.7GB: initrd.img.old
   2.6GB: vmlinuz
   2.7GB: vmlinuz.old
```> With 2 drives I would keep ubuntu on one with grub in the MBR of that drive and windows on the other with windows boot in that drive. Since it is difficult to have windows boot Ubuntu, the first drive ends up as the Ubuntu drive so you can add windows to grub. When you do the install this way it does require some swapping of drive order in BIOS to get the drives ordered correctly during the install. What i expected to happen was to have to swap hard drive order via bios to have windows or ubuntu load. (with there own loaders) Seeing as i plan on very infrequently using the windows install it seemed more practical this way than having it in the GRUB loader. I dont need either drive to see each other either really, there will be no transferring or sharing of file between the two..

---

### Post by mechro on 2009-11-07
Again in a Terminal do...

```
sudo grub
```

Then...

```
root (hd1,0)
```

Then...

```
setup (hd1)
```

```
quit
```

This should make the Ubuntu drive bootable if you set the BIOS to boot from there.

If that works you can then consider your options for Windows.

---

### Post by mechro on 2009-11-07
Er... perhaps I meant to say if you set the Bios to boot from the other drive. I'm never sure until I actually do it. Try both!

---

### Post by sensay on 2009-11-07
Yes!

After following those commands and setting the ubuntu drive to boot first i saw the GRUB and here i am.

Whilst loading i noticed an error on screen, i didnt catch it all but the jist of it was that a mount point could not be mounted and it was pointing to sda6. Any idea what thats about? It also mentioned to press ctrl D to drop to a recovery shell but then continued to load normally.

Finally, what can i do from here to get my windoze bootable? At present it still takes me to a blank screen.

Sorry, i feel like im asking a lot! You have been super helpful

Thanks

---

### Post by mechro on 2009-11-07
I've got to go now but...

Don't worry too much about the error messages when booting. Investigate those another day.

If your confident that Windows is installed then you can repair the Windows boot using your XP disk. I can't remember the exact procedure but it's to do with the repair facility on the disc and the command fixmbr. Perhaps you could search or somebody will help you here.

Fixing the Windows boot may bork your Ubuntu Grub boot again but as long as you remember...

[B]sudo grub
root (hd1,0)
setup (hd1)
quit[/B]

...you can restore it.

This has already been linked in the thread but worth reading...

[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)

At some point you can even add Windows to your Grub boot.

---

### Post by sensay on 2009-11-07
Ok, i think i can get it from here then.

Cheers mate, thanks for your time.

---

### Post by Joe Ker1086 on 2009-11-07
Congrats on gettin it fixed, i feel like i hurt more than helped. Good luck gettin windows working again.

---

### Post by sensay on 2009-11-08
Just thought id finish this off by saying i got the scenario i wanted in the end.

I reinstalled windoze to the smaller drive, it loaded as would be expected (no grub, no ubuntu) and from that point i used the live cd to actually reinstall grub to the root partition. 

The result is now exactly as i had hoped. At the BIOS boot stages i simply select which hdd to load from and i get either windows or the grub loader dependant on choice.

Again, big thanks to all for the help

---

### Post by mechro on 2009-11-08
Cool. I did wonder whether you might have to edit Grub's device.map file as sometimes with more than one drive Grub can look in the wrong drive for root.

---

