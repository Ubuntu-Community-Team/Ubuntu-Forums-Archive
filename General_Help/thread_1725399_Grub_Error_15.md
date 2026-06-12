---
title: "Grub Error 15"
date: 2011-04-09
forum: General Help
---

### Post by rganesh27 on 2011-04-09
Hi, this is my first thread for help after using Ubuntu for over 2 years.
Im Presently on 10.10, and im also running WinXP alongside.

prelude....a month ago, i found in some thread that Swap space wasnt really necessary for RAM of over 1 GB, and true to it, i wasnt using using much of my 4GB allocated for swap ever.............so i deleted it ( dunno if it was wise, but didnt face any problems when i first deleted)

today, i found out from another thread on a way to extend the size of /home directory if it was on a seperate mountpoint, and if space was available on my hard disk.
i just had 1 GB allocated to home directory and it used to fill up quite rapidly (due to cache from google chrome).
I made a backup of my home directory contents, and i deleted the /home partition through the Disk utility.Somehow i couldnt combine the two unallocated spaces under a single partition...why is that?
(My plan was to combine that 1GB and the 4GB from the earlier swap space to use a 5GB home partition.) 

............and then i restarted.. :( *sigh*

and ever since i have been seeing the Grub error,and am not able to access my operating systems normally.

GRUB Loading stage 1.5

Grub loading, please wait...
Error 15 

i am attaching the results.txt from my system obtained by booting through a liveCD. Something tells me that the way ive been following has been a roundabout one or a very inefficient one...please let me know where ive been going wrong and how can i restore my system to normalcy

Thanks
Ganesh

---

### Post by rganesh27 on 2011-04-10
from the results.txt file, it said that Stage2 was looking into /dev/sda10 for the menu.lst file, but in my case ( through sudo blkid) that location refers to /tmp.

i copied the /boot/grub folder from my /boot partition (/dev/sda9) into /tmp and now i am able to see the grub menu,and have come to windows now, but cant log into ubuntu.

please let me know if any more info is required....im stuck!:(

---

### Post by Hedgehog1 on 2011-04-10
Here is the script output with the 'CODE' tags so it is easier to read:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #266373828 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda7 and looks 
                       at sector 297282044 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda9 and 
                       looks at sector 297003516 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2    *        144,585    82,060,019    81,915,435   7 HPFS/NTFS
/dev/sda3          82,060,020   204,941,204   122,881,185   7 HPFS/NTFS
/dev/sda4         204,941,205   312,576,704   107,635,500   f W95 Ext d (LBA)
/dev/sda5         204,941,268   235,657,484    30,716,217   b W95 FAT32
/dev/sda6         235,657,548   266,373,764    30,716,217   7 HPFS/NTFS
/dev/sda7         266,373,828   282,005,009    15,631,182  83 Linux
/dev/sda8         282,005,073   293,716,394    11,711,322  83 Linux
/dev/sda9         295,676,388   297,620,189     1,943,802  83 Linux
/dev/sda10        297,620,253   304,769,114     7,148,862  83 Linux
/dev/sda11        304,769,178   312,576,704     7,807,527  83 Linux
/dev/sda12        293,716,458   295,676,324     1,959,867  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0A03                              vfat       DellUtility                   
/dev/sda10       c96c98cb-035d-4e70-88dc-b45280af3f1a   ext3                                     
/dev/sda11       fc45791d-1e0f-4725-9f57-c65610b0330a   ext3                                     
/dev/sda12       79679c39-7e74-420a-9c32-c2ac72f65a55   ext2                                     
/dev/sda2        1CBCB1E6BCB1BA9A                       ntfs       OS-XP                         
/dev/sda3        26E82E8BE82E58F7                       ntfs       ~!!DATA!!~                    
/dev/sda5        8055-A52D                              vfat       NEW VOLUME                    
/dev/sda6        8E68B75468B739B3                       ntfs       New Volume                    
/dev/sda7        420608ea-3ccc-47cd-a7cd-a925e3809c98   ext3                                     
/dev/sda8        72c78481-3963-4b48-9139-faeb6c559d92   ext3                                     
/dev/sda9        618f6271-1760-49fd-842a-16d6f799ca57   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda7        /media/420608ea-3ccc-47cd-a7cd-a925e3809c98 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda9        /media/618f6271-1760-49fd-842a-16d6f799ca57 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda3        /media/~!!DATA!!~        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda2/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2
# Entry for /dev/sda9 :
UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
# Entry for /dev/sda11 :
UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2
# Entry for /dev/sda12 :
UUID=f9a409ad-faa4-4dfc-83e3-ec6cc9824f5f /home ext3 relatime 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/OS-Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/t!!DATA!!t ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/OS-XP ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda7: Location of files loaded by Grub: ===================


 139.2GB: boot/grub/stage2

============================= sda9/grub/menu.lst: =============================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Debian GNU/Linux, kernel 2.6.35-25-generic
root		(hd0,9)
kernel		/vmlinuz-2.6.35-25-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
initrd		/initrd.img-2.6.35-25-generic

title		Debian GNU/Linux, kernel 2.6.35-25-generic (recovery mode)
root		(hd0,9)
kernel		/vmlinuz-2.6.35-25-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
initrd		/initrd.img-2.6.35-25-generic

#title		Debian GNU/Linux, kernel 2.6.32-22-generic
#root		(hd0,11)
#kernel		/vmlinuz-2.6.32-22-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
#initrd		/initrd.img-2.6.32-22-generic

#title		Debian GNU/Linux, kernel 2.6.32-22-generic (recovery mode)
#root		(hd0,11)
#kernel		/vmlinuz-2.6.32-22-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
#initrd		/initrd.img-2.6.32-22-generic

#title		Debian GNU/Linux, kernel 2.6.31-15-generic
#root		(hd0,11)
#kernel		/vmlinuz-2.6.31-15-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
#initrd		/initrd.img-2.6.31-15-generic

#title		Debian GNU/Linux, kernel 2.6.31-15-generic (recovery mode)
#root		(hd0,11)
#kernel		/vmlinuz-2.6.31-15-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
#initrd		/initrd.img-2.6.31-15-generic

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,9)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows Loader
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=================== sda9: Location of files loaded by Grub: ===================


 152.0GB: boot/grub/stage2
 152.2GB: grub/menu.lst
 152.3GB: grub/stage2
 151.5GB: initrd.img-2.6.31-15-generic
 151.4GB: initrd.img-2.6.32-22-generic
 151.4GB: initrd.img-2.6.35-25-generic
 151.4GB: vmlinuz-2.6.31-15-generic
 151.4GB: vmlinuz-2.6.32-22-generic
 151.4GB: vmlinuz-2.6.35-25-generic
```

Now we will see what we can see - :D

***The Hedge***

---

### Post by Hedgehog1 on 2011-04-10
When you deleted and then re-created the /dev/sda9 ('/home') partition, the new partiton as a very different UUID from the old one:

New UUID:
```
/dev/sda9        618f6271-1760-49fd-842a-16d6f799ca57   ext3 
```

Old UUID as recored in /etc/fstab:

```
# Entry for /dev/sda9 :
UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
```

Here are the steps to correct this:

Please boot off the LiveCD/LiveUSB, select 'TRY'.

```
sudo mount /dev/sda7 /mnt
```

```
gksudo gedit /mnt/etc/fstab
```

Add the comment (the '#') to the old line and add the new line:

```
# Entry for /dev/sda9 :
**[COLOR="Red"]#[/COLOR]**UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
**[COLOR="Red"]UUID=618f6271-1760-49fd-842a-16d6f799ca57 /home ext3 relatime 0 2[/COLOR]**
```

Then save file and exit the editor.

Now you can reboot from the hard drive and you should not see the  error anymore.  

***The Hedge***

:KS

p.s. Your previous '/home' data is gone, sadly.

---

### Post by rganesh27 on 2011-04-10
Thank you for your time to reply, i tried the step that you have indicated, but the situation remains the same.
looks like stage2 in the grub keeps looking for menu.lst in my /tmp location.

i have added a screenshot (modified so that the partition details are in the same screen) to express my present condition (hopefully in a less confusing manner :P)

would it help if i do a switchover to grub2? will it automatically identify my partitions correctly?..
my main intention was to expand my /home directory size :(

thanks again for your help :)
[IMG]file:///home/ubuntu/Desktop/Screenshot_main.png[/IMG]

---

### Post by rganesh27 on 2011-04-12
*bump*

please, can any1 help me with what i need to look for to solve this? :(

---

### Post by rosencrantz on 2011-04-12
Did you run update-grub?

---

### Post by rganesh27 on 2011-04-12
No, i havent yet run update-grub.
for some time now, i have only been able to access the boot screen and windows by copying the grub folder to my "/tmp" location.

---

### Post by Hedgehog1 on 2011-04-13
rganesh27,

I just noticed that your '/home' partition is defined twice:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2
# Entry for /dev/sda9 :
[B][COLOR="Red"]UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
[/COLOR][/B]# Entry for /dev/sda11 :
UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2
# Entry for /dev/sda12 :
**[COLOR="red"]UUID=f9a409ad-faa4-4dfc-83e3-ec6cc9824f5f /home ext3 relatime 0 2[/COLOR]**
```

Could I ask you to that script again and then lets talk about bringing some order to your partitions (and in the process get GRUB working again?)

I am thinking that bringing down to 3 Ubuntu partitions would give you more useful space and less confusion:

[B]/dev/sda7 as '/'
/dev/sda9 as '/home'
/dev/sda13 as swap[/B]

**_First, I need to see how your PC looks now, please._**

Please boot off the hard disk, or boot the LiveCD/LiveUSB and select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


***The Hedge***

:KS

---

### Post by jacob.david on 2011-04-13
Did you try to repair the installation with a bootable disk. I have done it quite a while ago and don't remember exactly. But when you boot from the installable CD/DVD, and choose the repair option it should be able to recover your existing setup and fix it.

---

### Post by rganesh27 on 2011-04-13
@the Hedge..here's the present state..

 ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #266373828 on boot drive #1
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda7 and looks 
                       at sector 297282044 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda9 and 
                       looks at sector 297003516 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst  [COLOR=DarkRed] [/COLOR][U][COLOR=DarkRed]*(you are able to see this here because i copied it to this location manually)*[/COLOR]
[/U] 
sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2    *        144,585    82,060,019    81,915,435   7 HPFS/NTFS
/dev/sda3          82,060,020   204,941,204   122,881,185   7 HPFS/NTFS
/dev/sda4         204,941,205   312,576,704   107,635,500   f W95 Ext d (LBA)
/dev/sda5         204,941,268   235,657,484    30,716,217   b W95 FAT32
/dev/sda6         235,657,548   266,373,764    30,716,217   7 HPFS/NTFS
/dev/sda7         266,373,828   282,005,009    15,631,182  83 Linux
/dev/sda8         282,005,073   293,716,394    11,711,322  83 Linux
/dev/sda9         295,676,388   297,620,189     1,943,802  83 Linux
/dev/sda10        297,620,253   304,769,114     7,148,862  83 Linux
/dev/sda11        304,769,178   312,576,704     7,807,527  83 Linux
/dev/sda12        293,716,458   295,676,324     1,959,867  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0A03                              vfat       DellUtility                   
/dev/sda10       c96c98cb-035d-4e70-88dc-b45280af3f1a   ext3                                     
/dev/sda11       fc45791d-1e0f-4725-9f57-c65610b0330a   ext3                                     
/dev/sda12       79679c39-7e74-420a-9c32-c2ac72f65a55   ext2                                     
/dev/sda2        1CBCB1E6BCB1BA9A                       ntfs       OS-XP                         
/dev/sda3        26E82E8BE82E58F7                       ntfs       ~!!DATA!!~                    
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8055-A52D                              vfat       NEW VOLUME                    
/dev/sda6        8E68B75468B739B3                       ntfs       New Volume                    
/dev/sda7        420608ea-3ccc-47cd-a7cd-a925e3809c98   ext3                                     
/dev/sda8        72c78481-3963-4b48-9139-faeb6c559d92   ext3                                     
/dev/sda9        618f6271-1760-49fd-842a-16d6f799ca57   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/~!!DATA!!~        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2
# Entry for /dev/sda9 :
#UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /home ext3 relatime 0 2
# Entry for /dev/sda11 :
UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2
# Entry for /dev/sda12 :
UUID=f9a409ad-faa4-4dfc-83e3-ec6cc9824f5f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/OS-Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/t!!DATA!!t ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/OS-XP ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda7: Location of files loaded by Grub: ===================


 139.2GB: boot/grub/stage2

============================= sda9/grub/menu.lst: =============================

# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
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
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title        Debian GNU/Linux, kernel 2.6.35-25-generic
root        (hd0,9)
kernel        /vmlinuz-2.6.35-25-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
initrd        /initrd.img-2.6.35-25-generic

title        Debian GNU/Linux, kernel 2.6.35-25-generic (recovery mode)
root        (hd0,9)
kernel        /vmlinuz-2.6.35-25-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
initrd        /initrd.img-2.6.35-25-generic

#title        Debian GNU/Linux, kernel 2.6.32-22-generic
#root        (hd0,11)
#kernel        /vmlinuz-2.6.32-22-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
#initrd        /initrd.img-2.6.32-22-generic

#title        Debian GNU/Linux, kernel 2.6.32-22-generic (recovery mode)
#root        (hd0,11)
#kernel        /vmlinuz-2.6.32-22-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
#initrd        /initrd.img-2.6.32-22-generic

#title        Debian GNU/Linux, kernel 2.6.31-15-generic
#root        (hd0,11)
#kernel        /vmlinuz-2.6.31-15-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
#initrd        /initrd.img-2.6.31-15-generic

#title        Debian GNU/Linux, kernel 2.6.31-15-generic (recovery mode)
#root        (hd0,11)
#kernel        /vmlinuz-2.6.31-15-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
#initrd        /initrd.img-2.6.31-15-generic

title        Debian GNU/Linux, kernel memtest86+
root        (hd0,9)
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows Loader
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=================== sda9: Location of files loaded by Grub: ===================


 152.0GB: boot/grub/stage2
 152.2GB: grub/menu.lst
 152.3GB: grub/stage2
 151.5GB: initrd.img-2.6.31-15-generic
 151.4GB: initrd.img-2.6.32-22-generic
 151.4GB: initrd.img-2.6.35-25-generic
 151.4GB: vmlinuz-2.6.31-15-generic
 151.4GB: vmlinuz-2.6.32-22-generic
 151.4GB: vmlinuz-2.6.35-25-generic

============================= sda10/grub/menu.lst: =============================

# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
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
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title        Debian GNU/Linux, kernel 2.6.35-25-generic
root        (hd0,9)
kernel        /vmlinuz-2.6.35-25-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
initrd        /initrd.img-2.6.35-25-generic

title        Debian GNU/Linux, kernel 2.6.35-25-generic (recovery mode)
root        (hd0,9)
kernel        /vmlinuz-2.6.35-25-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
initrd        /initrd.img-2.6.35-25-generic

#title        Debian GNU/Linux, kernel 2.6.32-22-generic
#root        (hd0,11)
#kernel        /vmlinuz-2.6.32-22-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
#initrd        /initrd.img-2.6.32-22-generic

#title        Debian GNU/Linux, kernel 2.6.32-22-generic (recovery mode)
#root        (hd0,11)
#kernel        /vmlinuz-2.6.32-22-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
#initrd        /initrd.img-2.6.32-22-generic

#title        Debian GNU/Linux, kernel 2.6.31-15-generic
#root        (hd0,11)
#kernel        /vmlinuz-2.6.31-15-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro quiet splash
#initrd        /initrd.img-2.6.31-15-generic

#title        Debian GNU/Linux, kernel 2.6.31-15-generic (recovery mode)
#root        (hd0,11)
#kernel        /vmlinuz-2.6.31-15-generic root=UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 ro single
#initrd        /initrd.img-2.6.31-15-generic

title        Debian GNU/Linux, kernel memtest86+
root        (hd0,9)
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows Loader
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=================== sda10: Location of files loaded by Grub: ===================


 154.6GB: grub/menu.lst
 154.6GB: grub/stage2 
```

---

### Post by rganesh27 on 2011-04-13
> **jacob.david said:**
> Did you try to repair the installation with a bootable disk. I have done it quite a while ago and don't remember exactly. But when you boot from the installable CD/DVD, and choose the repair option it should be able to recover your existing setup and fix it.

No jacob, i havent tried.... by "existing setup", do you mean the info on the present partitions?...thats where i want to clean up things a bit..i wanted to combine my unallocated space(which i obtained by deleting swap) to /home..and now things look a bit messy, as The Hedge has suggested, i would like to clear that up first..:)

---

### Post by Hedgehog1 on 2011-04-13
rganesh27,

Thanks for the updated script output.  This is actually beginning to make a twisted sort of sense!

I am going to ask you to comment out a few more lines from your /etc/fstab file.  I will explain why I am suggesting  each change.

Here is the total change suggested change (changes in red):

```
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
**[COLOR="Red"]#UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2[/COLOR]**
# Entry for /dev/sda9 :
#UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /home ext3 relatime 0 2
# Entry for /dev/sda11 :
**[COLOR="Red"]#UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2[/COLOR]**
# Entry for /dev/sda8 :
UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2
# Entry for /dev/sda12 :
UUID=f9a409ad-faa4-4dfc-83e3-ec6cc9824f5f none swap sw 0 0
...
```

Now the detail of why:

```

# Entry for /dev/sda10 :
**[COLOR="Red"]#UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2[/COLOR]**
# Entry for /dev/sda9 :
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /home ext3 relatime 0 
```

You have your '/boot' pointing to your '/home' partition.  It really needs to be using the the '/' (root) partition (then you can stop copying the grub menu list).  By commenting out this line, Linux will use the '/' partition for anything not defined as to another partition.

```
# Entry for /dev/sda11 :
**[COLOR="Red"]#UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2[/COLOR]**
```

By not defining the '/tmp', it will Linux will use your '/' partition for this, too.

This will reduce your partition count by 2 more.

Please do not trust the '/dev/sdaxx' in the comments of /ext/fstab, instead used the UUIDs of partitions for figure out which ones can be deleted.  But first, lets get you booting without having to copy files.

Once these changes are done, and you boot into Ubuntu on the hard disk, you may have to do this again:

```
sudo update-grub
```

This please run the script and post the script output again so we can delete unused partitions and resize the ones you are using to give you more room.

***The Hedge***

:KS

List of Ubuntu UUIDS and their real /dev/sda**xx** values:
```
                                     
/dev/sda7        420608ea-3ccc-47cd-a7cd-a925e3809c98   ext3                                     
/dev/sda8        72c78481-3963-4b48-9139-faeb6c559d92   ext3                                     
/dev/sda9        618f6271-1760-49fd-842a-16d6f799ca57   ext3 
/dev/sda10       c96c98cb-035d-4e70-88dc-b45280af3f1a   ext3                                     
/dev/sda11       fc45791d-1e0f-4725-9f57-c65610b0330a   ext3                                     
/dev/sda12       79679c39-7e74-420a-9c32-c2ac72f65a55   ext2

```

---

### Post by rganesh27 on 2011-04-13
Should i run update-grub* after* i make the changes in fstab and* before* i boot from my hard drive* as well?*
i just tried commenting the 2 lines and saved it. (i also took out that grub folder that i copied into /tmp earlier). When i rebooted without running update-grub , i ran into error 15 again.

---

### Post by rosencrantz on 2011-04-13
If you make any changes to your partition/OS boot setup, you need to run update-grub to let grub adapt to the changes, I assume.
Up to now I had to use it only after kernel updates on my secondary SuSE distribution.
I am not sure how much of the grub configuration is rewritten in the process, but it is a very easy thing to try.
Also, grub shouldn't rely on the fstab contents, as it uses the (hdx,y) syntax to identify partitions.

---

### Post by rganesh27 on 2011-04-14
rosencrantz,  I've run update grub, and now when i boot, it brings me to grub> prompt.

i tried the commands..
root
...gave me (hd0,msdos7)

linux /vmlinuz root=/dev/sda7 ro
....here it gave me an error saying "no loaded kernel"

how should i go about this?

---

### Post by rganesh27 on 2011-04-14
oops...it was "file not found" error when i typed in linux /vmlinuz...

i think im gonna try using linux /vmlinuz-2.6.35-25-generic root=/dev/sda7

---

### Post by rosencrantz on 2011-04-14
And I thought you'd get a boot menu with this... Well, you can't have it all.
root (hd0,msdos7) looks funny. Shouldn't it be (hd0,6) if you linux system is on /dev/sda7?
I must admit I am a bit stumped with your having /boot on a separate partition in your old fstab. No idea what that does to grub. Have you changed fstab, and is /boot now on the system partition, as suggested by hedgehog? (This might account for grub not finding a kernel image in /boot)
I'm curious: *why* did you have /boot on a separate partition? LVM?

---

### Post by rosencrantz on 2011-04-14
Erm, correction:
root (hd0,msdos7) is the grub root, so you have to use whatever partition /boot is on. 'msdos7' still looks weird to me. 
And is /vmlinuz-2.6.35-25-generic a symlink into /boot?

---

### Post by rganesh27 on 2011-04-14
well..the /vmlinuz-2.6.35-25-generic line didnt work as well....again file not found

> **rosencrantz said:**
> And I thought you'd get a boot menu with this... Well, you can't have it all.
root (hd0,msdos7) looks funny. Shouldn't it be (hd0,6) if you linux system is on /dev/sda7?
I must admit I am a bit stumped with your having /boot on a separate partition in your old fstab. No idea what that does to grub. Have you changed fstab, and is /boot now on the system partition, as suggested by hedgehog? (This might account for grub not finding a kernel image in /boot)
I'm curious: *why* did you have /boot on a separate partition?

im not sure why that happens..searched a bit and found users having the same (hd0,msdosX)..like (hd0,X) => /dev/sdaX

my fstab looks like
```
=============================== sda7/etc/fstab: ===============================  # /etc/fstab: static file system information. # #  -- This file has been automaticly generated by ntfs-config --  # # <file system> <mount point>   <type>  <options>       <dump>  <pass>  proc /proc proc defaults 0 0 # Entry for /dev/sda7 : UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1 # Entry for /dev/sda10 : UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2 # Entry for /dev/sda9 : #UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2 #UUID=618f6271-1760-49fd-842a-16d6f799ca57 /home ext3 relatime 0 2 # Entry for /dev/sda11 : #UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2 # Entry for /dev/sda8 : UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2 # Entry for /dev/sda12 : UUID=f9a409ad-faa4-4dfc-83e3-ec6cc9824f5f none swap sw 0 0 /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 /dev/sda6 /media/OS-Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0 /dev/sda3 /media/t!!DATA!!t ntfs-3g defaults,locale=en_US.UTF-8 0 0 /dev/sda2 /media/OS-XP ntfs-3g defaults,locale=en_US.UTF-8 0 0  
```


i dont really remember why i used /boot on a seperate partition..(maybe sum1 suggested it to me years back!?!:confused:)

do you know how to access windows from the Grub> prompt?...now im unable to get past this prompt :(

---

### Post by rganesh27 on 2011-04-14
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
#UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2
# Entry for /dev/sda9 :
#UUID=d1a0bbff-7bb7-4ab0-9b60-99b345954cec /home ext2 relatime 0 2
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /home ext3 relatime 0 2
# Entry for /dev/sda11 :
#UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2
# Entry for /dev/sda12 :
UUID=f9a409ad-faa4-4dfc-83e3-ec6cc9824f5f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/OS-Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/t!!DATA!!t ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/OS-XP ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

i shud hav tried this!

---

### Post by Hedgehog1 on 2011-04-14
This is getting a little too tricky.

We need the contents of the old '/boot' partitions '/boot' directory copied to the '/boot' directory of the '/' partition.

**[SIZE="3"]I think my head may explode soon.[/SIZE]**

You can remove the comment from the: 

```
**[COLOR="Red"]#[/COLOR]**UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2

```

to become:

```
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2

```

if you want.

-------

Perhaps the real key is to save your data and make a clean install of Ubuntu. This is sounding better and better.

**rganesh27** - would that work for you?


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-14
Do you have your Windows XP install CD?  You can do a FIXMBR to start booting from windows while we work out the Ubuntu side of things.


If you can get your documents off the Ubuntu partitions:

Using the LiveCD/LiveUSB, you can make a clean install (and start booting XP again in the process) by deleting /dev/sda7 - /dev/sda12:

```

/dev/sda7         266,373,828   282,005,009    15,631,182  83 Linux
/dev/sda8         282,005,073   293,716,394    11,711,322  83 Linux
/dev/sda9         295,676,388   297,620,189     1,943,802  83 Linux
/dev/sda10        297,620,253   304,769,114     7,148,862  83 Linux
/dev/sda11        304,769,178   312,576,704     7,807,527  83 Linux
/dev/sda12        293,716,458   295,676,324     1,959,867  83 Linu
```

And then manually create these 3 partiton instead to install Ubuntu into:

```

/dev/sda7  etx4 '/' (root) 12 gigs
/dev/sda8  ext4 '/home' (whatever space sda7 and sda9 didn't use)
/dev/sda9  swap (1024 megs)

```

And then install this way:

[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]

Your sda7 = pictures sdc1,
Your sda8 = pictures sdc2,
Your sda9 = pictures sdc3,

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

[SIZE="3"]Be sure to install the boot loader on **/dev/sda** ![/SIZE]


***The Hedge***

:KS

---

### Post by rosencrantz on 2011-04-14
A general howto for the Grub prompt:
[http://planetstephanie.net/2009/05/27/grub2-rescue-mode/](http://planetstephanie.net/2009/05/27/grub2-rescue-mode/)
Try to chainload Windows (it's on /dev/sda2, right?) from the Grub prompt (I know it should work on grub 1, and it can do no worse than fail for grub 2):
rootnoverify (hd0,1) 
makeactive
chainloader --force +1
boot
If this doesn't work, you can try (hd0,0) instead of (hd0,1). I've never had to boot a Windows not on the first partition, so I'm not quite sure which to choose.
@all: going to sleep now. Depending on your time zone, I'd recommend the same before doing anything drastic...

---

### Post by rganesh27 on 2011-04-14
Guys!..made some "progress" :P

first of all..a bigg thank you to both rosencrantz and TheHedge :)
and a bigg sorry as well for confusing things out here :P

The_Hedge, i would like to keep the clean install as my last option, because presently i have a few time and internet availability constraints on my side (*was looking at may 3rd for meddling further if i'd made no real progress*)

well..i followed the method 3 :CHROOT method provided in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) , and i got back my menu..by which ive come to windows...not able to access ubuntu though....._im not sure what to change at the edit.._

in that [link]("https://help.ubuntu.com/community/Grub2"),for Steps 4 and 5,in my case,i entered:
 
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda9 /mnt/boot (because i have a seperate boot partion)
also i did
sudo mount /dev/sda8 /mnt/usr (i tried the steps without including this line and it said "broken /usr..")
i did not mount /home   ( did not know what to do here..not sure if i _now_ have a /home partiton at all!!?:confused: )

[COLOR="DarkRed"]*i had made a few modifications to /etc/fstab by looking at entries from "sudo blkid" (dunno if these are one and the same..). This was done BEFORE i used the CHROOT method.(grub reinstall SIMPLEST - Copy GRUB 2 Files from the LiveCD)......i havent got back to ubuntu and checked the RESULTS.TXT or anything now) *
[/COLOR]
if i'm anywhere close to getting back to normalcy, please do let me know, otherwise i'll do the clean install later on...lets spare ourselves from the confusion!

thanks again!! :)

---

### Post by rosencrantz on 2011-04-14
Your substitutions look quite correct. I don't think you need to mount /home for the CHROOT method, as it doesn't affect files in /home. 
If home is correctly set up in fstab, you should still have it. The procedure is:
1) grub determines root and boot partitions to get at its config files, kernel and initrd.
2) The kernel loads the file system and partitions according to fstab.

So, you weren't able to boot the installed Ubuntu. Did you get to the grub rescue?
Copying from the grub2 help page you used and this discussion [https://bbs.archlinux.org/viewtopic.php?id=85603](https://bbs.archlinux.org/viewtopic.php?id=85603):

set root=(hd0,10)
linux /vmlinuz-2.6.35-25-generic root=/dev/sda7
initrd /initrd.img-2.6.35-25-generic
boot

This is assuming your boot partition is still on sda10 and the linux root on sda7. Note the different roots! The root in line one is the one grub uses to find its config files and kernel images (your boot partition), the one in line two is the root the kernel is using for the Ubuntu file system (the system partition).
I also learned something: Apparently grub2 has a (hdX,Y) syntax different from grub1. 
Grub 1: sda5=(hd0,4)
Grub 2: sda5=(hd0,5)
I hope I used the correct syntax above. If you are unsure, try something like ls (hd0,10) from the grub rescue terminal to see whether you identified the partitions correctly. Also, I made some assumptions about the file names for kernel image and initrd. Try ls (hd0,10)/boot to check.

---

### Post by rganesh27 on 2011-04-14
> **rosencrantz said:**
> 
So, you weren't able to boot the installed Ubuntu. Did you get to the grub rescue?
Copying from the grub2 help page you used and this discussion [https://bbs.archlinux.org/viewtopic.php?id=85603](https://bbs.archlinux.org/viewtopic.php?id=85603):

set root=(hd0,10)
linux /vmlinuz-2.6.35-25-generic root=/dev/sda7
initrd /initrd.img-2.6.35-25-generic
boot

I also learned something: Apparently grub2 has a (hdX,Y) syntax different from grub1. 
Grub 1: sda5=(hd0,4)
Grub 2: sda5=(hd0,5)


i tried following the above steps....(pressing c when the menu comes up)..but the grub> prompt that comes up did not accept commands like "set root=..." and  "ls..". The command "root" however showed (hd0,8).

then i rebooted,..
my menu shows some 4 entries for my ubuntu..(taken from menu.lst i suppose?..because i remember commenting out those earlier kernel versions, but now they just showed up)..and on the top it said Grub 0.97....and my "root =" line (1st line)was pointing to (hd0,11).

the second line "linux /vmlinuz..." had the UUID for my /dev/sda7 (which contains my "/" ..420somethings..)..

i tried "e" from the menu..and changed that (hd0,11) to (hd0,8)...pressed "b"
.....few seconds.. and..it started booting..webcam lit up..harddrive showed activity..and then the splash screen....and i kept watching the white dots turn to orange..and back.....after a while i stopped counting...it went forever...looks like its searching and searching...

---

### Post by rosencrantz on 2011-04-14
Oh, so you are on grub 1. (grub 0.97)
First question, how did you get it, I thought you used the grub2 howto? Did you use an old live CD (pre-9.10)?

In that case, the grub rescue syntax is probably:

root (hd0,Y)
kernel /vmlinuz-2.6.35-24-generic root=/dev/sdaX
initrd /initrd.img-2.6.35-24-generic
boot

Commands like ls don't work for grub 1 (legacy), only grub2.

X and Y are your boot and Ubuntu root partitions.
You did see a bootsplash and hardware response, which means that Grub has done its job and the kernel has taken over. 
To see what's wrong now, remove the 'quiet' from your grub kernel options, which should replace the bootsplash with text messages.

---

### Post by rganesh27 on 2011-04-14
rosencrantz,
i followed the steps as you guided..thanks!!..the startup process had stalled because it couldnt mount my "/home2"...so it suggested to press "S" for Skip, and the rest progressed smoothly..(atleast it looked like.. :P )

..When i did that CHROOT stuff, ( i followed the instructions for Grub2..the same link that i've posted and the exact steps as well) and used 10.10 Live CD for it....really not sure why my Grub 1 would come in ?!..looks like a mutated form of grub!!
 before i followed those steps, i had copied my backed up /home directory to the 4 GB location that now forms my /home, but after logging in(as user(username: r2d2), not as root) i am not able to open any application, not even able to write to my desktop ( when i tried to save a screenshot), so yes..it looks to be a permissions issue...everything looked user..."root" group..."root"..; but a few things..say my cairo dock is visible  with the theme that i last used....the permissions for these folders(.config/cairo-dock) are also "root", im able to use the system monitor, terminal...play songs thru vlc, but not able to launch any browser.. 

i think i'll update in a while after switching to the root user....find it slightly uncomfortable to navigate here in elinks..(not sure if text alignment comes out properly!)...:P

---

### Post by rganesh27 on 2011-04-14
Oh yes..that went well! 

the error that came up on startup regarding the /home2 ..(/dev/sda12) was regarding "trying to mount ext3 on ext2"...how would you suggest i correct this?

and found another thing...there is another boot/grub folder within my boot location..and everything here looks like grub2 (no sign of menu.lst)..

i changed the ownership of "r2d2" (my /home/user folder) to "r2d2" and group "r2d2"..is that a right move?

---

### Post by rosencrantz on 2011-04-15
Well, using the root user for day-to-day stuff is pretty dangerous, especially when connected to the internet.
Can you post your present fstab and ownership and permissions of your home folder (ls -l /home/r2d2)?
If you don't own your home folder, try 
chown -R r2d2:users /home/r2d2
If the home folder doesn't have owner permissions try
chmod -R o+rw /home/r2d2

---

### Post by rosencrantz on 2011-04-15
Eugh, forgot to send off that answer, but fortunately you already knew what to do...
r2d2 as group works too, it's the same for my /home
trying to mount ext3 as ext2... could it be that you specified ext3 in fstab and it's really ext2 or vice versa?
Check your partition setup with gparted, and change the file system entry in fstab if necessary.

---

### Post by rganesh27 on 2011-04-15
:)..chown performed..and ownership regained!..
fstab entry for /home2 showed a ext3 type while disk utility had a ext2 filesystem type...I changed it back to ext2 in fstab and it booted properly :)

now..i dunno if im standing inside a house made of matchsticks with regard to my grub and filesystem..i shall look into the details of handling grub2 a bit later, but i need to know a few things..

1) Am i presently using Grub1 or Grub2?..looks like Grub1...menu.lst was present and i edited that to match my present values.I was able to run update-grub after making that modification in fstab and no errors were reported..does this command work with grub legacy as well?

2) When i do a kernel update, should i switch over to grub2?..what precautions should i take here?...

3) My /etc/fstab looks like this:
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=420608ea-3ccc-47cd-a7cd-a925e3809c98 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=c96c98cb-035d-4e70-88dc-b45280af3f1a /tmp ext3 relatime 0 2
# Entry for /dev/sda9 :
UUID=618f6271-1760-49fd-842a-16d6f799ca57 /boot ext3 relatime 0 2
# Entry for /dev/sda11 :
UUID=fc45791d-1e0f-4725-9f57-c65610b0330a /home ext3 relatime 0 2
# Entry for /dev/sda8 :
UUID=72c78481-3963-4b48-9139-faeb6c559d92 /usr ext3 relatime 0 2
# Entry for /dev/sda12 :
#UUID=fc45791d-1e0f-4725-9f57-c65610b0330a /home2 ext3 relatime 0 2
UUID=79679c39-7e74-420a-9c32-c2ac72f65a55 /home2 ext2 relatime 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/OS-Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/t!!DATA!!t ntfs-3g defaults,locale=en_US.UTF-8 0 0

```
 _i dont have swap space now...is that fine_..or should i change something (i have 2GB RAM).i dont use high memory intensive applications on my ubuntu...the maximum limits sometimes reached are by firefox/chrome and amarok...other than that, my earlier swap space was pretty much unused..
Is it advisable to make further modifications to my filesystem now? ( as suggested by TheHedge?)

phew!.....feel a loooot relieved now! :) thanks to TheHedge,rosencrantz and the entire community!!

---

