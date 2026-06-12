---
title: "Commands to identify discs/partitions?"
date: 2009-12-01
forum: General Help
---

### Post by kansasnoob on 2009-12-01
I've been trying to find just the right command(s) to be run from a Live CD to include in a tutorial, actually an addition to a tutorial:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Specifically regarding a new mount/chroot procedure I've cooked up and tested.

The only problem I have is describing how to correctly identify the proper root partition to be mounted. I'll grant you that "fdisk -l" is quite often enough but what if it's a nightmare like mine:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       14879    36772753+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       17103    16635276   83  Linux
/dev/sda11          17104       17870     6160896   83  Linux
/dev/sda12          17871       19457    12747546   83  Linux

Partition table entries are not in disk order


Then of course once you know the drive designation(s) you can run "sudo parted /dev/sdX print" (of course replacing X with the proper designation) which is a bit more "human readable" but still:

> Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  122GB   37.7GB  logical   ext3
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3


Finally the only other thing I can think of is to have them run meierfra's Boot Info Script which is excellent but almost seems like overkill in this application:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Example (of the pertinent part):

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - Main 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


You can see that provides very good info regarding each partition but I hate to confuse people with a really huge file, because the Boot Info script also includes a lot more than just disc/partition ID.

Is this even clear as mud???????????????

I think a HowTo should be both explanatory so a person knows what they're doing but also fairly simple and as brief as possible.

All suggestions welcome, and thanks in advance.

Oh, and I'm not smart enough to parse meirefra's Boot Info Script and apply only what I want to one of my own! Maybe someday, but not yet :)

---

### Post by ibuclaw on 2009-12-01
Best way I can think of is from grub0.97 itself.

```

iain@netbook:~$ sudo grub

grub> find /etc/issue
 (hd0,0)
 (hd0,1)

grub> cat (hd0,0)/etc/issue
Fedora release 7 (Moonshine)
Kernel \r on an \m


grub> cat (hd0,1)/etc/issue
[COLOR="Red"]Ubuntu 9.10 \n \l[/COLOR]


grub> 

```
Although that doesn't cover weird setups to whom have /etc on a separate filesystem?

Regards
Iain

---

### Post by kansasnoob on 2009-12-01
> **tinivole said:**
> Best way I can think of is from grub0.97 itself.

```

iain@netbook:~$ sudo grub

grub> find /etc/issue
 (hd0,0)
 (hd0,1)

grub> cat (hd0,0)/etc/issue
Fedora release 7 (Moonshine)
Kernel \r on an \m


grub> cat (hd0,1)/etc/issue
[COLOR="Red"]Ubuntu 9.10 \n \l[/COLOR]


grub> 

```
Although that doesn't cover weird setups to whom have /etc on a separate filesystem?

Regards
Iain

Hey, good to see you around! Been a while.

I haven't yet tried this from a live CD but from Karmic w/grub2:

> lance@lance-desktop:~$ sudo grub
[sudo] password for lance: 
sudo: grub: command not found
lance@lance-desktop:~$ grub> find /etc/issue
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
lance@lance-desktop:~$ 


You see we'll almost undoubtedly be dealing with both legacy grub and grub2 along with various Win bootloaders.

Maybe I should bug meierfra:

[http://sourceforge.net/users/meierfra/](http://sourceforge.net/users/meierfra/)

---

### Post by efflandt on 2009-12-01
Gparted on live CD's shows disk labels, assuming you labeled your partitions with useful names.  But that does not help if partitions have no labels.

---

### Post by kansasnoob on 2009-12-01
> **efflandt said:**
> Gparted on live CD's shows disk labels, assuming you labeled your partitions with useful names.  But that does not help if partitions have no labels.

True, and I do always label mine, but a HowTo needs to address those who have no idea what's up. I'm talking about those who still come on board talking about drive C, drive F, etc.

---

### Post by ibuclaw on 2009-12-02
> **kansasnoob said:**
> Hey, good to see you around! Been a while.
I hadn't noticed I had left, but thanks, and Hello to you too. ;)
> **kansasnoob said:**
> 
I haven't yet tried this from a live CD but from Karmic w/grub2:

Aye, I assume you have installed the legacy grub on your system before running "sudo grub"

Also, **grub>** resembles the legacy grub prompt. You don't type that in directly.
What you type in instead:
```
cat (hd0,0)/etc/issue
```
But that is in the legacy grub prompt... if that makes sense.

It won't work in bash/other shells.

Forgot to mention also, that once you identify the partition with the correct /etc/issue, then you can check that partition's /etc/fstab to see which partition is the / partition for that setup.

Again, in the **legacy grub prompt** (not in shell)
```
cat (hd0,0)/etc/fstab
```
It's not foolproof, but makes a workable replacement of using a script to tell you.

Regards
Iain

---

