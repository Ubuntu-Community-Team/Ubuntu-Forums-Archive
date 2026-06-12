---
title: "Recovering windows"
date: 2011-07-16
forum: General Help
---

### Post by Aceofspades138 on 2011-07-16
okay so i was wondering if there was any way for me to recover windows and all the files from it.
i typed in these codes
     Code:
     sudo fdisk -l <-- lower case letter l, not number 1 cat /etc/fstab df -h 
And this is my output

XXXXXXX:~$ sudo fdisk -l
[sudo] password for ace138: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23687   190262093    7  HPFS/NTFS
/dev/sda2           28933       30401    11799742+   7  HPFS/NTFS
/dev/sda3           23687       28932    42133505    5  Extended
/dev/sda5           23687       28541    38989824   83  Linux
/dev/sda6           28541       28932     3142656   82  Linux swap / Solaris

Partition table entries are not in disk order
XXXXXXXXXXX:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=054a1c42-7442-4c24-a064-1eb5a90a2317 none            swap    sw              0       0
XXXXXXXXXXXXX:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              37G  2.8G   32G   8% /
none                  1.5G  636K  1.5G   1% /dev
none                  1.5G  196K  1.5G   1% /dev/shm
none                  1.5G   92K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
XXXXXXXXXXXXX:~$

---

### Post by Quackers on 2011-07-16
You should be able to view your Windows files from the Places menu in Ubuntu.
What's the problem exactly? Doesn't Windows boot? 
Have you run sudo update-grub in the terminal in Ubuntu?

---

### Post by Aceofspades138 on 2011-07-16
OOO i found my files but i want to actually have the computer start in windows instead of Ubuntu because more than one person use this computer.

i am a complete noob and i know nothing about this lol.
But when i do the menu.lst i don't see anything like Windows its just all Ubuntu kernels.
  I'm so confused with this is, its overwhelming lol.

and thanks for fast reply :)

---

### Post by Quackers on 2011-07-16
You don't say what version of Ubuntu you are using.
Try opening a terminal and type in ```
sudo update-grub
``` and press enter. Then enter your password and watch as grub.cfg is configured.
You should see the Windows Loader recognised.
If it is, reboot and you should now see a grub menu which gives you the choice of which operating system to boot. The top item will be Ubuntu.
If you're not sure copy/paste the terminal output of sudo update-grub in your next post.

---

### Post by Aceofspades138 on 2011-07-16
Heres my output

XXXXXX:~$ sudo update-grub
[sudo] password for XXXX: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-10-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by Quackers on 2011-07-16
What version of Ubuntu are you using? It appears that grub legacy is being used which means it's likely to be an old version of Ubuntu.

Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Aceofspades138 on 2011-07-16
This is a lot lol
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   380,524,248   380,524,186   7 NTFS / exFAT / HPFS
/dev/sda2         464,792,580   488,392,064    23,599,485   7 NTFS / exFAT / HPFS
/dev/sda3         380,524,542   464,791,551    84,267,010   5 Extended
/dev/sda5         380,524,544   458,504,191    77,979,648  83 Linux
/dev/sda6         458,506,240   464,791,551     6,285,312  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F43E57913E574C2C                       ntfs       COMPAQ
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda5        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a   ext4       
/dev/sda6        054a1c42-7442-4c24-a064-1eb5a90a2317   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 11.04 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a

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

title        Ubuntu 11.04, kernel 2.6.38-10-generic
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro quiet splash 
initrd        /boot/initrd.img-2.6.38-10-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro  single
initrd        /boot/initrd.img-2.6.38-10-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro  single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, memtest86+
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=054a1c42-7442-4c24-a064-1eb5a90a2317 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 209.726348877 = 225.191952384  boot/grub/menu.lst                             1
 183.580673218 = 197.118246912  boot/grub/stage2                               1
 183.018554688 = 196.514676736  boot/initrd.img-2.6.38-10-generic              2
 182.331272125 = 195.776712704  boot/initrd.img-2.6.38-8-generic               2
 182.413394928 = 195.864891392  boot/vmlinuz-2.6.38-10-generic                 1
 183.580547333 = 197.118111744  boot/vmlinuz-2.6.38-8-generic                  1
 183.018554688 = 196.514676736  initrd.img                                     2
 182.331272125 = 195.776712704  initrd.img.old                                 2
 182.413394928 = 195.864891392  vmlinuz                                        1
 183.580547333 = 197.118111744  vmlinuz.old                                    1


```

---

### Post by crua9 on 2011-07-16
What vs of Ubuntu are you running

---

### Post by Quackers on 2011-07-16
Well Windows is still there at least :-)
For some reason you have Ubuntu 11.04, which is the latest release, but you have grub legacy installed rather than grub2. Grub2 is the default bootloader for Ubuntu 11.04.
Have you had grub problems and followed a guide to re-install grub?

---

### Post by Aceofspades138 on 2011-07-16
Yes. i probably should of told u this earlier sorry lol.
but i un-installed grub 2 for original grub cause i didn't like grub2.

And phew thought i lost it :)

So if i reboot ill be able to choose if i want vista or Ubuntu?

---

### Post by Quackers on 2011-07-16
Not at the moment. With grub2 it would be fixed now.
Sadly as I have never used grub legacy I am not sure what needs to be done about it.
I will contact another member and see if he can advise you further.

---

### Post by Aceofspades138 on 2011-07-16
I have nothing under 
### END DEBIAN AUTOMAGIC KERNELS LIST

What am i supposed to use to boot into windows?

---

### Post by Quackers on 2011-07-16
Well, normally grub2 :-) but you don't have it.
I don't know whether the member I have contacted is online at the moment but he will doubtless be about soon.
Sit tight for the moment.

---

### Post by Aceofspades138 on 2011-07-16
Lol im upgrade to grub2 to cause u less trouble.
I thought that some thing different but i was wrong.

---

### Post by Quackers on 2011-07-16
You can wait for the other member. If you prefer grub legacy then keep it :-)
I prefer grub2 myself as it does more and, to me, it's more straightforward.
If you want to go back to grub2 follow steps 2 to 5 in the CHROOT section of the guide below, but put sudo then a space in front of the commands given.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Aceofspades138 on 2011-07-16
Thanks , 
i dont know anything about the "grub" family so ill take your word for it lol
here
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   380,524,248   380,524,186   7 NTFS / exFAT / HPFS
/dev/sda2         464,792,580   488,392,064    23,599,485   7 NTFS / exFAT / HPFS
/dev/sda3         380,524,542   464,791,551    84,267,010   5 Extended
/dev/sda5         380,524,544   458,504,191    77,979,648  83 Linux
/dev/sda6         458,506,240   464,791,551     6,285,312  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F43E57913E574C2C                       ntfs       COMPAQ
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda5        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a   ext4       
/dev/sda6        054a1c42-7442-4c24-a064-1eb5a90a2317   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

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
# kopt=root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a

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

title        Chainload into GRUB 2
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 11.04, kernel 2.6.38-10-generic
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro quiet splash
initrd        /boot/initrd.img-2.6.38-10-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-10-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro single
initrd        /boot/initrd.img-2.6.38-10-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro quiet splash
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro single
initrd        /boot/initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, memtest86+
uuid        1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 1881d6e4-2ab9-4b90-a860-6ab54d24ac2a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F43E57913E574C2C
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1881d6e4-2ab9-4b90-a860-6ab54d24ac2a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=054a1c42-7442-4c24-a064-1eb5a90a2317 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 183.586563110 = 197.124571136  boot/grub/core.img                             1
 209.604743958 = 225.061380096  boot/grub/grub.cfg                             1
 213.625495911 = 229.378629632  boot/grub/menu.lst                             1
 183.018554688 = 196.514676736  boot/initrd.img-2.6.38-10-generic              2
 182.331272125 = 195.776712704  boot/initrd.img-2.6.38-8-generic               2
 182.413394928 = 195.864891392  boot/vmlinuz-2.6.38-10-generic                 1
 183.580547333 = 197.118111744  boot/vmlinuz-2.6.38-8-generic                  1
 183.018554688 = 196.514676736  initrd.img                                     2
 182.331272125 = 195.776712704  initrd.img.old                                 2
 182.413394928 = 195.864891392  vmlinuz                                        1
 183.580547333 = 197.118111744  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Quackers on 2011-07-16
Did you run this line?
```
sudo apt-get purge grub grub-pc grub-common
``` because it appears that menu.lst is still present.
When you ran sudo update-grub did the Windows Loader appear as grub.cfg was run?
It appears that it may have done.

---

### Post by Aceofspades138 on 2011-07-16
i think so

blahblahblah:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done


do i edit the grub.cfg?

---

### Post by Quackers on 2011-07-16
Ok it's bite the bullet time :-)
Reboot and you should see a grub menu with a list of items to boot.
Press the down arrow on your keyboard until the Vista entry on /dev/sda1 is highlighted. Press enter and hopefully Vista will boot.

---

### Post by Aceofspades138 on 2011-07-16
Thank you! i am currently on my Vista right now
is there anything on this site like +rep or somthing?
How can i repay you?

and can you make it so that vista is at top and it automatically picks that one instead of Ubuntu?

---

### Post by Quackers on 2011-07-17
Sorry Aceofspades138, I had to sleep :-)
No rep but thanks anyway.
I'm glad to hear Vista is back again.
Yes you can make Vista the top item in the grub menu, so that if nothing is pressed at the grub menu Vista will boot by default.
You need to edit a file.
In the terminal type (or copy/paste) ```
gksu gedit /etc/default/grub
``` then press enter, then type your password and press enter.
A new windows will open up. This is your /etc/default/grub file.
Go to the first proper line of text which is ```
GRUB_DEFAULT=0
``` the "0" in that line is telling grub to boot the first menu entry by default.
You need to change that number to correspond with the menu entry that is your Vista on /dev/sda1 line.
If that Vista entry is the second item in the grub menu change the "0" to a "1". If Vista on /dev/sda1 is the third entry in the grub menu change the number to a "2" etc, etc.
When changed, click on "File" then "save". Leave a couple of seconds then click on "File" then "Quit" and the window will close.
In the terminal run ```
sudo update-grub
``` and when it's finished Vista should be your top entry in the grub menu. Check it with a reboot.

---

