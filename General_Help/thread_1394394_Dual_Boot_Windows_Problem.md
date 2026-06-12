---
title: "Dual Boot Windows Problem"
date: 2010-01-30
forum: General Help
---

### Post by ebro173 on 2010-01-30
I apologize up front if this question has already been asked and/or solved.  I've tried looking and I've tried following suggestions in other posts to solve these problems.  Most notably, I've followed a howto here:

[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

Up until a few days ago I have been using both Ubuntu 8.04 (64-bit) and Windows Vista on my Acer Extensa 4420-5239 Laptop.  It is an AMD64 processor with ATI radeon X1250. Then I was goofing around trying to be able to stream video from my laptop to a TV through an S-Video cable when booted into Ubuntu.  I did some damage... See posts 8 and 9 of this thread for background on that:

[http://ubuntuforums.org/showthread.php?t=1357324&highlight=s-video](http://ubuntuforums.org/showthread.php?t=1357324&highlight=s-video)

So, now I have two problems with the laptop that I want to fix.

1) I can no longer boot into Windows.

2) I think my glitchy display (when I'm in Ubuntu) might do better if I get fglrx back in order.

I'm hoping to get help with the Windows boot problem from this thread.

I use Grub and I can boot into Ubuntu no problem.  I've always had two boot options in the Grub screen for Windows.  One for Windows Vista Recovery.  One for Windows Vista. Now, after following meierfra's howto that is linked above, I have a third entry for Vista.  At first when trying to boot into Vista with my regular Grub list entry I wouldn't even get to the login screen.  The HD light would just go dead and I would get a black screen. My strategy when this happens is to just kill by holding down the power button.  Now after following meierfra's howto I can get to the screen where I enter my Windows password and then the HD light and the screen go dark and I have to kill the comp.

A few additional notes to the info above.  One, I can't really follow meierfra's steps.  I am not allowed access to overwrite the bootmgr or the boot folder on the windows C drive when I try the manual option.  Additionally the recovery console can't find bcedit.  I also don't get into the command line/revocery console in the fashion that the howto describes (i.e. pressing f10). Another point is that I am able boot into the Windows Vista Recovery option that I've always had listed in the Grub menu and was also able to do so prior to trying meierfra's how to.  (I've also tried scheduling the chkdsk /p for next startup and letting that do its magic to no avail.)  Also, I've been able to mount the C:\ drive partition while in Ubuntu - I have to force it at first because of shutting down with the power button.

So I vaguely think Acer has some other funky boot set up (maybe I'm wrong about this).  There's this other sort of hidden windows install that I have used to try to reinstall the basic Windows image that I made on a couple of dvd's when I first got the computer and configured it. The Acer documentation isn't so good - referencing some manual that, as far as I can tell, I never got.  When in Ubuntu, I can also mount this other hidden windows install.

Still, when trying to boot into Windows normally, I can only get to the point where I put in my Windows password and then black screen etc...

As for number two, if you can just suggest a good tutorial, I'm sure I must have followed one in the first place.

Thanks for your suggestions.

---

### Post by meierfra. on 2010-02-01
> Still, when trying to boot into Windows normally, I can only get to the point where I put in my Windows password 

Since you can get to the login screen, it means that my howto worked and the problems are probably not caused by the boot loader.


> (I've also tried scheduling the chkdsk /p for next startup and letting that do its magic to no avail.) 
Did  "chkdsk" run at startup ?  Did it correct any errors?  You should also  try "chkdsk /r".

Could you follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script, and post the RESULTS.txt. (I don't think the information will help very much in your case,  but one never knows)

---

### Post by ebro173 on 2010-02-02
Hey, thanks for the reply.  

I did run the chkdsk /p.  I scheduled it for the next restart when I was logged into Windows safe mode.  I may not have payed close enough attention but I did not that any errors were fixed.  I will try the chkdsk /r suggestion.

As for the results of the script:
 
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3fecb06e

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048    90,794,547    70,312,500   7 HPFS/NTFS
/dev/sda3          90,799,380   213,841,214   123,041,835   5 Extended
/dev/sda5          90,799,443   168,923,474    78,124,032   b W95 FAT32
/dev/sda6         168,923,538   204,073,694    35,150,157  83 Linux
/dev/sda7         204,073,758   213,841,214     9,767,457  82 Linux swap / Solaris
/dev/sda4         213,841,215   234,436,544    20,595,330  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A20A-9608                              vfat       PQSERVICE                     
/dev/sda2        3A240EDB240E99D1                       ntfs       ACER                          
/dev/sda4        d56a923a-1509-4a84-b054-35c432d7f889   ext3       linuxOS                       
/dev/sda5        4F30-0640                              vfat                                     
/dev/sda6        b5d93fba-24f9-4ff5-bcf4-846b8a1d2723   ext3                                     
/dev/sda7        f91a699c-cdba-42ae-8a8f-a0723b7e83d7   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda5        /dos                     vfat       (rw,utf8,umask=007,gid=46)
/dev/sda6        /home                    ext3       (rw,relatime)


=========================== sda4/boot/grub/menu.lst: ===========================

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
timeout        60

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
# kopt=root=UUID=d56a923a-1509-4a84-b054-35c432d7f889 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet splash noapic

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=d56a923a-1509-4a84-b054-35c432d7f889 ro splash noapic
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=d56a923a-1509-4a84-b054-35c432d7f889 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (Recovery)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista
root        (hd0,1)
savedefault
makeactive
chainloader    +1

# This entry added by me on January 29, 2010 to try to help fix the Windows Vista boot process 
# on /dev/sda2
title        Vista
rootnoverify    (hd0,1)
chainloader    +1

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=d56a923a-1509-4a84-b054-35c432d7f889 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4F30-0640  /dos            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=b5d93fba-24f9-4ff5-bcf4-846b8a1d2723 /home           ext3    relatime        0       2
# /dev/sda7
UUID=f91a699c-cdba-42ae-8a8f-a0723b7e83d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by dbowlin17 on 2010-02-02
Alright, I had a similar issue here. I was unable to boot into XP, when I installed grub 1.97 (grub2) it then automatically found all appropriate partitions with operating systems installed and my issue was resolved. You can go into terminal ```
 sudo apt-get install grub2
``` that is what i believe that I used to get grub2. after installing grub2, i had no issues. maybe it will help you. i have a link to my thread with the actual code and what people suggested to help me. [http://ubuntuforums.org/showthread.php?t=1394472](http://ubuntuforums.org/showthread.php?t=1394472) hope this helps.

---

### Post by meierfra. on 2010-02-02
Deleted. Did not contain any useful information,

---

### Post by dbowlin17 on 2010-02-02
i read his post to say the issue was with windows not starting. i had that same issue. windows was not being pushed off the screen, it just wouldn't start. He says that he has entries for windows and ubuntu in grub, just the windows won't start. That was the issue I had until I updated my grub.

---

### Post by ebro173 on 2010-02-02
I tried running chkdsk /r.  I payed attention while it was running and I saw that no errors were found.  I still have the same issue - after putting in my login credentials, Windows won't really start/black screen. 

I really wouldn't mind living completely Windows free.  Its just that I can't stream video from ESPN360 or the UEFA champions league in Ubuntu yet - nor other things like NBC sitcoms.  I've registered my dissatisfaction on their websites...

So I'm still interested to try a few things to get Windows working again.  I do like a good puzzle, even if I may blow up a few things once in a while.

Also, an update, it seems the screen problem may be getting worse or that it fluctuates from not noticeable problem to very grainy.  It will be one way for the whole time I'm logged in then after I shut down and restart it may be different.

---

### Post by meierfra. on 2010-02-02
Sorry, I don't  think  I will be able to give you any  real advice. So here are just a couple of comments:

> I am not allowed access to overwrite the bootmgr or the boot folder on the windows C drive when I try the manual option. 
My tutorial was made for the case that bootmgr and /Boot are missing. If you want  you can rename bootmgr and /Boot from Ubuntu and then try again.  But since your are able to get to the Login screen, I don't think there is anything wrong with bootmgr and the bcd.


> Additionally the recovery console can't find bcedit
Did you try the Vista CD I linked in my tutorial?  You might also get the  [UBCD]("http://www.ultimatebootcd.com/") It has all kinds of diagnostic tools. (But I'm not really familiar with them.)

> referencing some manual that, as far as I can tell, I never got.
Often one can find those manuals  online somewhere.

---

### Post by dbowlin17 on 2010-02-02
are you able to do anything windows related when you try to start it from grub? or explain what happens when you try to start using grub please.

---

### Post by ebro173 on 2010-02-02
meierfra, I appreciate the comments.  I did try the cd you linked in post 4 of your other thread.  I'll look into this UBCD you linked here and you're right, I should have tried to locate a copy of that manual.  The thing is I think I did what the manual is going to tell me to do - I went through this whole routine to reinstall the Windows image (not sure I'm using the image term right) which asked me to put in disc 1 then disc 2 etc.  So I thought even without the manual I may have covered that base. Its worth a check though.

Hey dbowlin17, from my first post:

> 
Now after following meierfra's howto I can get to the screen where I enter my Windows password and then the HD light and the screen go dark and I have to kill the comp.
I get to the Windows login screen by selecting the regular Windows options in my Grub menu list.  Also,

> 
...I am able boot into the Windows Vista Recovery option that I've always had listed in the Grub menu and was also able to do so [even] prior to trying meierfra's how to.
Here are some irrelevant thoughts:  My situation just shows how robust Ubuntu/Linux really is.  I mean, I was able to blow up a Tv by connecting it to my computer while I was logged into Ubuntu (I'm willing to admit that I did something wrong that I'm still ignorant of): I clearly did some damage to the computer as well.  But, Ubuntu is still running fundamentally flawless - granted the display is a little funky.  I already liked Linux/Ubuntu. Now I'm convinced its a tank. I don't know why everyone I talk to about it is so resistant.  They just get all glazed over like I just started talking another language...  Well, at least not here on the forums. Or, did I just kill this thread?

:P

---

### Post by dbowlin17 on 2010-02-03
sorry there for not reading the post in full detail. I can then not provide any other advice, except to clear that partition, and start over, but first try accessing the files from ubuntu. who knows, maybe that will help. Sorry.

---

### Post by ebro173 on 2010-02-03
No worries dbowlin17.  
 
I'm probably going to keep tinkering.  I'll post back here if I find something that fixes the problem.

---

