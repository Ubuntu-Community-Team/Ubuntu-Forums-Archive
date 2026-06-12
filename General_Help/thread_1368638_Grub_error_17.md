---
title: "Grub error 17"
date: 2009-12-30
forum: General Help
---

### Post by tsuna27 on 2009-12-30
I have a laptop with XP and Ubuntu on a dual boot, today I used Gparted and deleted a small empty partition and moved the space to my ubuntu partition, i reboot and now I get this 

GRUB Loading stage1.5.

Grub loading, please wait...
Error 17

I read a bunch of other post but still no help

Please Help me

---

### Post by tsuna27 on 2009-12-30
Is Super Grub Disk A good way to fix?

Okay so I used Super Grub Disk and now I can get into Ubuntu but If i try to boot into Windows XP it does not work 

What can I do?

---

### Post by tsuna27 on 2009-12-31
bump

---

### Post by Leppie on 2009-12-31
what version of grub do you have?
could you post the output of this command:
```
$sudo grub-install -v
```

---

### Post by tsuna27 on 2009-12-31
grub-install (GNU GRUB 0.97)

---

### Post by Leppie on 2009-12-31
unfortunately, i don't have any experience with grub legacy.
could you [download and run meierfra's]("http://sourceforge.net/projects/bootinfoscript/") script and post the generated RESULTS.txt?

don't forget to make it executable before trying to run:
```
$sudo chmod +x boot_info_script0XX.sh  ##replace XX with the current version number
```

---

### Post by tsuna27 on 2009-12-31
I get chmod: cannot access `boot_info_script044.sh': No such file or directory
I downloaded it to my desktop

---

### Post by Leppie on 2009-12-31
> **tsuna27 said:**
> I get chmod: cannot access `boot_info_script044.sh': No such file or directory
I downloaded it to my desktop

did you change to the Desktop folder first?
```
$cd Desktop
```

---

### Post by tsuna27 on 2010-01-03
Um, nothing happened

matthew@matthew-laptop:~$ cd Desktop
matthew@matthew-laptop:~/Desktop$ sudo chmod +x boot_info_script044.sh
[sudo] password for matthew: 
matthew@matthew-laptop:~/Desktop$

---

### Post by Leppie on 2010-01-03
then you need to execute it:
```
$sudo bash ./boot_info_script*.sh
```

---

### Post by tsuna27 on 2010-01-05
okay here are the results

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09390939

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,505,314    71,505,252   7 HPFS/NTFS
/dev/sda2         110,302,290   117,194,174     6,891,885  1c Hidden W95 FAT32 (LBA)
/dev/sda3          71,505,315   110,302,289    38,796,975   5 Extended
/dev/sda5         108,599,463   110,302,289     1,702,827  82 Linux swap / Solaris
/dev/sda6    *     71,505,441   107,057,159    35,551,719  83 Linux
/dev/sda7         107,057,223   108,599,399     1,542,177  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="761CE4591CE415C1" TYPE="ntfs" 
sda2: LABEL="HDDRECOVERY" UUID="0B01-07DC" TYPE="vfat" 
sda5: UUID="2bf04064-f07f-4e1c-9a82-bb7432f2bb04" TYPE="swap" 
sda6: UUID="46bc29a2-a2ae-4c5c-b6ae-bb3212afd628" TYPE="ext3" 
sda7: UUID="2ec67bbc-0bce-4f71-8c1f-09665260c2c3" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matthew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matthew)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=7 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628

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

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        46bc29a2-a2ae-4c5c-b6ae-bb3212afd628
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        46bc29a2-a2ae-4c5c-b6ae-bb3212afd628
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        46bc29a2-a2ae-4c5c-b6ae-bb3212afd628
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        46bc29a2-a2ae-4c5c-b6ae-bb3212afd628
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        46bc29a2-a2ae-4c5c-b6ae-bb3212afd628
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=46bc29a2-a2ae-4c5c-b6ae-bb3212afd628 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=2ec67bbc-0bce-4f71-8c1f-09665260c2c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/menu.lst
  38.8GB: boot/grub/stage2
  38.6GB: boot/initrd.img-2.6.27-7-generic
  43.4GB: boot/initrd.img-2.6.28-17-generic
  43.4GB: boot/vmlinuz-2.6.27-7-generic
  38.5GB: boot/vmlinuz-2.6.28-17-generic
  43.4GB: initrd.img
  38.6GB: initrd.img.old
  38.5GB: vmlinuz
  43.4GB: vmlinuz.old

---

### Post by Leppie on 2010-01-05
try this:
```
$sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
$sudo update-grub
```

check if the menu is created correctly:
```
cat /boot/grub/menu.lst | grep Windows
```

---

### Post by tsuna27 on 2010-01-06
No, it still does not work, it does not even show the dual boot menu, it says starting grub then it just boots Ubuntu

---

### Post by Leppie on 2010-01-06
i will have to dig into grub legacy a bit deeper. will be back

---

### Post by wkulecz on 2010-01-06
> Okay so I used Super Grub Disk and now I can get into Ubuntu but If i try to boot into Windows XP it does not work 

If you can boot your Ubuntu but not windows you've probably corrupted the Windows chainloader.  Perhaps that smal partition you deleted had something windows needed to boot.

--wally.

---

### Post by Leppie on 2010-01-06
try adding the following section to your /boot/grub/menu.lst:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by jwbrase on 2010-01-06
Have you tried hitting escape once or twice when it says that it's starting Grub? It almost seems like the menu is being hidden, although "hiddenmenu" is commented out in menu.lst, so the menu shouldn't be hidden.

---

### Post by wkulecz on 2010-01-06
Make sure /boot/grub/menu.lst has a timeout set that is not zero, otherwise it just boot the default selection before you can hit ESC.

--wally.

---

### Post by tsuna27 on 2010-01-08
Leppie where in menu.lst do I add that?

---

### Post by jwbrase on 2010-01-09
> **tsuna27 said:**
> Leppie where in menu.lst do I add that?

It appears to already be in your menu.lst.

---

### Post by meierfra. on 2010-01-09
> It appears to already be in your menu.lst. 


No longer.  "update-grub" for Legacy Grub does not have  the ability to detect other OSs.  So moving the old menu.lst and running "update-grub" removed Windows from the Grub menu and also changed "#hiddenmenu" to "hiddenmenu".
So one needs to restore the original menu.lst.

Please open a terminal and run

```
sudo cp /boot/grub/menu.lst.old /boot/grub/menu.lst

```


> now I can get into Ubuntu but If i try to boot into Windows XP it does not work 

Can you tell us exactly what happened when you chose XP at the Grub menu.

---

### Post by tsuna27 on 2010-01-11
I did the 
sudo cp /boot/grub/menu.lst.old /boot/grub/menu.lst
[FONT=monospace]
and now I get the option to dual boot


If I press XP it tells me there's a problem and I get the option to go into safe mode

If I press start Windows normally I get the windows screen for about 3 secs and then 

my laptop reboots
[/FONT]

---

### Post by meierfra. on 2010-01-11
Sounds like a windows and not a Grub problem.

If you have a Windows CD, I suggest to go to the repair console (Press "r")

and  type

```
map
```

This should tell you what the drive letter of your Windows partition is.
Then

```
fixboot X:
chkdsk  /r X:
```

Here X has to replaced by the drive letter of your Windows partition. 
I'm not sure that this will  cure your problem, we might also have to have a look at you Windows registry. But we'll worry about that later.

---

### Post by tsuna27 on 2010-01-13
is there a way without a windows CD?

---

### Post by Leppie on 2010-01-13
> **tsuna27 said:**
> is there a way without a windows CD?
do you not have one?

---

### Post by tsuna27 on 2010-01-15
I thought I had a disk, but I can not seem to find it

SGD does not work for me, when I just boot windows it does the same thing, crash promt to safe mode or normal and then it just puts the XP boot up screen for .5 secs.

---

