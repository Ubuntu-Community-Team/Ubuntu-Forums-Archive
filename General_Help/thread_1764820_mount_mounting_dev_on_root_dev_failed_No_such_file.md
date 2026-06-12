---
title: "mount: mounting /dev on /root/ dev failed: No such file or directory"
date: 2011-05-22
forum: General Help
---

### Post by rich52x on 2011-05-22
ubuntu 10.10 won't boot, instead a screen comes up saying:

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or Direcoty
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg
```Then something about busybox that i can't remember, then:
```
(initramfs)
```The only major change that's been made to my system recently is that the power system box thing has been replaced recently after the computer would not power on.

---

### Post by Rubi1200 on 2011-05-22
Hi,
have you tried booting into recovery mode or an older kernel?

When you start the computer highlight the entry for 10.10 (your details say 11.04?) and then press "c" to get a grub> prompt.

At the prompt type ls and tell us what the output is please and if you know which partition the install is on that is producing the error.

Thanks.

---

### Post by rich52x on 2011-05-23
It's on my family computer, which is still running 10.10. The problem persists when booting into an older kernel or into recovery, 
The output from ls is:
```
(hd0) (hd0, msdos6) (hd0, msdos5) (hd0, msdos2) (hd0, msdos1)
```Thanks for replying btw :) 

rich

---

### Post by Rubi1200 on 2011-05-23
Thanks for posting the information. 

Since you don't say which partition the Ubuntu install is on I will have to guess a little.

In any event, hd0 is the primary disk and unless you have Windows installed I will guess that hd0,1 is the Ubuntu install and 5 and 6 are /home and swap respectively.

So, using the instructions to get a grub> prompt do this and Enter after each line:

```
set prefix=(hd0,1)/boot/grub 
set root=(hd0,1) 
insmod linux 
linux /vmlinuz root=/dev/sda1 ro 
initrd /initrd.img 
boot
```If this allows you to boot, then run ```
sudo update-grub
``` back in Ubuntu.

If hd0,1 (sda1) is not the Ubuntu install (and you will know quite quickly because it will display an error message, then try hd0,5 or hd0,6 using the syntax and format above).

If none of this works, then please post the output of the boot info script. There is a link at the bottom of my post with instructions.

Let me know how it goes and if you have any more questions.

---

### Post by rich52x on 2011-05-23
I do have windows installed actually, when I run this ommands, it's all okay until I run the 'insmod linux' command, where it says 'error: no device is set'. I have tried putting hd0, 1, hd0, 5 and hd0,6.
I will try the boot script now

---

### Post by Rubi1200 on 2011-05-23
> **rich52x said:**
> I do have windows installed actually, when I run this ommands, it's all okay until I run the 'insmod linux' command, where it says 'error: no device is set'. I have tried putting hd0, 1, hd0, 5 and hd0,6.
I will try the boot script now
Okay, bad guess :(

Here are specific instructions for the boot script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rich52x on 2011-05-23
Is it normal for it to hang on - 'Searching sda5 for information...'

Cos it's been like that for around 20minutes the first time i tried, and about 15 minutes now while im trying again
Still no RESULTS.TXT file created yet

---

### Post by Rubi1200 on 2011-05-24
No, that is not normal. We've seen this before with file-systems that are damaged (as indicated by your first post).

Try downloading and burning to CD a live distro called Slax:
[http://www.slax.org/get_slax.php](http://www.slax.org/get_slax.php)

Then boot the computer with it and follow the instructions for the boot script with one exception; you do not need to preface the command with sudo in the terminal.

---

### Post by rich52x on 2011-05-24
cheers man ill let you know the results by tomorrow night

need to hit the hay

---

### Post by rich52x on 2011-05-27
ok so today i went to the computer tto boot into slax, but i checked out if anything had changed with ubuntu, and for whatever reason, it magically started working
it told me that it was checking the disk for errors
then the gdm came up.

I guess i'll mark this as solved, i suppose
cheers for all the help man

---

### Post by Rubi1200 on 2011-05-27
> **rich52x said:**
> ok so today i went to the computer tto boot into slax, but i checked out if anything had changed with ubuntu, and for whatever reason, it magically started working
it told me that it was checking the disk for errors
then the gdm came up.

I guess i'll mark this as solved, i suppose
cheers for all the help man
That is great news :-)

If you still want us to take a closer look if there are other issues, you can run the boot script I mentioned before from within Ubuntu and post the results here.

In any event, if this is solved I am really glad to hear it.

---

### Post by rich52x on 2011-06-08
Hey again, my new laptop, after a few days of having ubuntu installed on an extended partition, has randomly come up with a staggeringly similar error for seemingly no reason at all. Its a dual boot of Natty 64bit and Windows 7 Home Premium 64bit, The 4 primary partitions are:

/dev/sda1 - SYSTEM
/dev/sda2 - C:/
/dev/sda4 (extended)
                   - /dev/sda5 - /
                   - /dev/sda6 - swap
/dev/sda3 -  RECOVERY

When in the livecd, the ubuntu partition, '47GB Filesystem' will not mount with error:

```
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The output from the boot info script is as follows

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/burg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   839,962,623   839,553,024   7 NTFS / exFAT / HPFS
/dev/sda3         942,362,624   976,560,127    34,197,504   7 NTFS / exFAT / HPFS
/dev/sda4         839,964,670   941,423,315   101,458,646   5 Extended
/dev/sda5         839,964,672   932,329,471    92,364,800  83 Linux
/dev/sda6         932,331,520   941,423,315     9,091,796  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        529E3A819E3A5E23                       ntfs       SYSTEM
/dev/sda2        C218B02D18B02279                       ntfs       
/dev/sda3        E4E24D7EE24D55C8                       ntfs       RECOVERY
/dev/sda5        df4b23bc-1aba-477d-aa5b-d1530359b995   ext4       
/dev/sda6        89ab2762-573c-4246-96ec-65457bdefb6d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 81 05 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff 02 60  81 05 d4 c2 8a 00 00 00  |.......`........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Cheers if you guys can help me at all

I'm determined to not have to revert to windows :P

---

### Post by Rubi1200 on 2011-06-09
Hi,
sorry to hear you are having troubles (again). First a question, why are you using burg as a boot manager? To be honest, I have seen a few threads where it only seemed to cause problems. The GRUB menu can be configured to do what you want with Grub Customizer:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Okay, somehow you seem to have damage to the file-system on sda5. So, from the LiveCD this is what you need to do:

open a terminal and run the following command:

```
sudo e2fsck -f -y -v /dev/sda5
```

After the command completes, and assuming no errors, reboot taking out the CD and you should be back in Ubuntu.

Let me know how it goes please.

---

### Post by rich52x on 2011-06-09
Many, many thanks my friend, I am indeed back in ubuntu

And i just installed burg to try it out and see what its like tbh

but upon looking around I come to the same conclusion you concerning the problems it causes, I'll just go back to the ol' standard grub for now :)

---

### Post by Rubi1200 on 2011-06-09
Excellent! I am really pleased you got this sorted out :-)

---

### Post by kollektivgeist on 2011-09-07
Hello!

I seem to have a similar problem. I use Windows Vista and Ubuntu 11.04 at the same partition. (As you can see I am new to Ubuntu.) Somehow my Windows crashed and now the Linux doesn't start anymore.

> Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootorg.

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)

I tried to fix it by following this thread, downloaded the boot_info_script file and got following result:

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048   711,477,247   686,899,200   7 NTFS / exFAT / HPFS
/dev/sda3         711,477,248 1,300,840,191   589,362,944   7 NTFS / exFAT / HPFS
/dev/sda4       1,300,840,446 1,953,523,711   652,683,266   5 Extended
/dev/sda5       1,300,840,448 1,929,758,719   628,918,272  83 Linux
/dev/sda6       1,929,760,768 1,953,523,711    23,762,944  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C044479B444792D8                       ntfs       WINRE
/dev/sda2        B4A449F6A449BC1C                       ntfs       SYSTEM
/dev/sda3        46264BB8264BA7AF                       ntfs       
/dev/sda5        3128d7f2-2f4e-4e62-92b1-70d5e3e30ebf   ext4       
/dev/sda6        07e3880d-0d85-4d66-a5e2-69383c853c9f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


I hope you can help me with this.
Does it cause any problems that I use Ubuntu 10.10 live-disk?

If I missed the right thread, please move the post.

Thanks.

---

### Post by kollektivgeist on 2011-09-07
If you need this Information too:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc347115f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       44288   343449600    7  HPFS/NTFS
/dev/sda3           44288       80974   294681472    7  HPFS/NTFS
/dev/sda4           80974      121602   326341633    5  Extended
/dev/sda5           80974      120122   314459136   83  Linux
/dev/sda6          120123      121602    11881472   82  Linux swap / Solaris
and

> ubuntu@ubuntu:~$  sudo bash ~/Desktop/boot_info_script*.sh

boot_info_script version: 0.60        [17 May 2011]


[COLOR=Red]"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.[/COLOR]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".


---

### Post by kollektivgeist on 2011-09-08
No more help needed, thx.

---

