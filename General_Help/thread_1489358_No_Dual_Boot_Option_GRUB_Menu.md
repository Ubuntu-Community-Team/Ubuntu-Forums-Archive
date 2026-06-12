---
title: "No Dual Boot Option GRUB Menu"
date: 2010-05-21
forum: General Help
---

### Post by jcdlinux on 2010-05-21
Hi,

I am once again experiencing problems trying to dual boot. This is what happened:

I installed XP and left a partiton for Ubuntu. I then proceded to install ubuntu 10.04 manually. I set up "swap" 1GB, root "/" to 10 GB and "/home" for both root and home I used ext4. Installation proceeded without a problem. Once finished I was asked to restart, but while booting, I never got the option to select between Windows XP or Ubuntu; it just booted straight into Ubuntu.

How do I fix this without having to reinstall everything again? Any solutions or ideas?

Appreciate any help you can give!

Thanks

---

### Post by john newbuntu on 2010-05-21
From the Desktop, open a terminal - (Applications->Accessories->Terminal) and enter the following command:
```
sudo update-grub
```Does this code see any windows OS?  If it does, reboot and check if things are ok.  You may have to hold the shift key to display grub.
If it does not, can you please run the following commands and post the output:
```
sudo fdisk -lu
cat /etc/default/grub
```

---

### Post by NotMarkus on 2010-05-21
What does your [FONT="Fixedsys"]/etc/defaults/grub[/FONT] file say with regards to [FONT="Fixedsys"]GRUB_HIDDEN_TIMEOUT[/FONT]?

It should have (hopefully) detected that you have more than one OS, but if it didn't, the line will be uncommented and will read ```
GRUB_HIDDEN_TIMEOUT=0
```

Changing it to ```
#GRUB_HIDDEN_TIMEOUT=0
``` will disable the hidden menu feature. You will need to run [FONT="Fixedsys"]update-grub[/FONT] after changing this file though.

---

### Post by jcdlinux on 2010-05-21
Thanks for the fast replies!

> Does this code see any windows OS?

Well, this is the output:

```
user@user-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

user@user-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5a5a5a5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16126   520281089   260132482    f  W95 Ext'd (LBA)
/dev/sda2       520282112   522280959      999424   82  Linux swap / Solaris
/dev/sda3   *   522280960   541812735     9765888   83  Linux
/dev/sda4       541812736   625141759    41664512   83  Linux
/dev/sda5           16128   520281089   260132481    7  HPFS/NTFS
user@user-desktop:~$ 


```

> What does your /etc/defaults/grub file say with regards to GRUB_HIDDEN_TIMEOUT?

It should have (hopefully) detected that you have more than one OS, but if it didn't, the line will be uncommented and will read 

Here is the output:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by NotMarkus on 2010-05-21
Unfortunately it looks like it doesn't recognize your windows partition in grub. I looked around a little bit and came across this:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_multiple_OS_on_a_single_computer](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_multiple_OS_on_a_single_computer)

:\ 

I'm not sure if you used a LiveCD and Ubuntu Desktop, but if so you might need to recreate your old boot records and install Ubuntu with a different method. Following the link in that section will provide you with a ton of info that should solve your problem.

Good luck.

---

### Post by john newbuntu on 2010-05-21
So, grub does not see windows.  Windows is on /dev/sda5 which is a logical partition.  If I am right, Win needs to be on an active primary partition with the boot flag set for it to be a working system.  But linux partitions could be in either primary or logical partitions.
Prior to installing Ubuntu, did you log on to XP and check if everything was OK?  If you have not checked it, I feel it would not have worked anyway.  

So, you might have to change your partitioning scheme and create a primary partition to put XP on. Also set the boot flag on that partition.

Since this looks like a fresh install, you could start with 100GB NTFS on sda1, Let sda2 be extended and contain sda5,6,7 for root,home and swap - all totaling around 100GB for Linux.  Leave 100GB as a spare partition for now for data share and later on partition it as NTFS.  Of course you can fine tune these according to your present and future needs.
Once you set this up, reinstall the OSs and then see if it works.

Note: Can you please re-confirm that XP should be installed on a primary partition?

---

### Post by jcdlinux on 2010-05-21
I don't know if this is exactly what you are asking, but when I installed windows xp, I deleted an old partition, and made a new one for it. Since I left another partition intact (NTFS at the time) for Linux, when I installed Windows XP it was marked as "D:/" instead of "C:/". Later when installing Ubuntu I remember there was an option for selecting Primary (default) and logical... I left it primary, finished install, restarted and it went straight to Ubuntu. 

I did access XP a couple of times before installing Ubuntu and installed some drivers and software and there was no problem.

So, is there any way I can make XP primary or does that involve reformatting and  reinstalling everything again?

What about removing Ubuntu and then try installing again and setting it to logical, or will there be problems with the MBR? I won't be able to fix a Windows MBR because my xp CD for some reason never takes me to the recovery console, or never lets me choose to repair Windows.

---

### Post by john newbuntu on 2010-05-21
It is possible that you were able to work with XP because of the other OS on the C: partition(primary) which contained XP's boot files,  Now that the primary has been wiped out by the Ubuntu install, grub is not able to identify XP in the logical partition(no boot files).

One possible solution to this is to convert the XP logical partition to a primary one and then repair it first to get the XP bootloader on it.  This will save you some time.  You will want to also set the boot flag on it.   I must admit I am not very familiar in playing with the partitioning table in converting a logical partition to a primary one.  You can google for some examples or I hope someone else can help you in this area.  Here is one example I found where caljohnsmith shows on how it can be done:  [http://ubuntuforums.org/showthread.php?t=1008458](http://ubuntuforums.org/showthread.php?t=1008458)

---

### Post by oldfred on 2010-05-22
If it is just a new install it will be better to reinstall. Partition tables have lots of rules and when editing you have to make sure you follow all those rules.

If you want to see some more info:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

More info on how windows works:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by jcdlinux on 2010-05-22
Thanks,

I will check all the info provided in the links and see what I can do about it. I wouldn't really want to reinstall again, because I already loaded each OS with software and files (specially XP which has about 25GB of backup files). If I could find a way for GRUB to recognize XP, it would obviously be better. Also, I won't be able to repair windows, because the CD I have never prompts for a repair, nor the option to go into Recover Console (I really don't understand why, but I have tried it a few times). Anyway, I'll be checking the links and If I find anything, I will post back.

Again, Thanks!

---

### Post by oldfred on 2010-05-22
Windows only boots thru the primary partition with the boot flag. So unless it sees a primary partition and the boot flag it will not even see it to repair it. Windows will work if you have another window install in a primary and then the second one in a logical can boot thru the one in the primary. 

You have used all 4 primary partitions. Normally linux installs swap to a logical and linux will work from a logical but windows will not. You have things reverse.

I do not know what this will do. You could delete swap, shrink your windows so you can add swap afterwards.

this supposedly reorders partition, just be aware it may cause other problems. I do not know if it renumbers them or not and if you do not have swap will the windows then become sda4. IF that happens your linux will change to sda3 and you will have to reinstall grub and possibly fix fstab.
this occasionally fixes issues and is worth trying or it may do nothing:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

---

