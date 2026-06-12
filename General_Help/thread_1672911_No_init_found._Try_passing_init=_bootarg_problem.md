---
title: "No init found. Try passing init= bootarg problem"
date: 2011-01-21
forum: General Help
---

### Post by ztschutt on 2011-01-21
My notebook was booting back up from hibernation when the battery ran out and it shut off. When I tried to start it up again I got a "No init found. Try passing init= bootarg problem" error. This has happened before and I tried to use the same fix (sudo fsck /dev/sda5), but this time I got an unexpected error:
> ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
Does anyone know how I could fix this? I have tried everything I did last time and none of it is working. :(

Edit: I want to add that I am trying to fix this using a 10.10 live cd, don't know if that will change anything though.

---

### Post by Rubi1200 on 2011-01-22
You could try this:

```
lsof | grep sda5
``` to try to identify what's using /dev/sda5 and kill it.

I also suggest the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ZeroRider13 on 2011-01-22
Hey, Im having the same problem and after doing the fsck fix, I have three options, no action, copy original to backup, or vice versa.  Which do I do to save it?  Also when I try to get the results file the third stup of information gathering just stays.  It never creates a new results file, or gives me a new line on terminal.  Please help me out, thanks a lot.

---

### Post by ztschutt on 2011-01-22
When I ran the first command you suggested I got this error:
> ubuntu@ubuntu:~$ lsof | grep sda5
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
jbd2/sda5  449       root  cwd   unknown                                /proc/449/cwd (readlink: Permission denied)
jbd2/sda5  449       root  rtd   unknown                                /proc/449/root (readlink: Permission denied)
jbd2/sda5  449       root  txt   unknown                                /proc/449/exe (readlink: Permission denied)
jbd2/sda5  449       root NOFD                                          /proc/449/fd (opendir: Permission denied)

Then when I tried your boot info script it froze at this point and I had to close it: 
> ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 


---

### Post by Rubi1200 on 2011-01-22
I know this is a hassle, but we have seen occasions when, for some reason, doing this from an Ubuntu CD does not work.

Two possibilities; either Puppy Linux or Knoppix.

Knoppix is my favorite as a LiveCD. Then try the procedures again. You may have to preface the lsof command with sudo.

---

### Post by ztschutt on 2011-01-22
Your script worked on the live cd, so here is the results.txt
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

sda6: _________________________________________________________________________

    File system:       ext4
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

/dev/sda1               2,048     2,000,895     1,998,848  82 Linux swap / Solaris
/dev/sda2           2,002,942   312,580,095   310,577,154   5 Extended
/dev/sda5    *      2,002,944    31,297,535    29,294,592  83 Linux
/dev/sda6          31,299,584   312,580,095   281,280,512  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/cloop0                                             iso9660    KNOPPIX_FS                    
/dev/sda1        7a266e06-b373-48fb-9792-9d689dde0cb9   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e41d06dd-044e-4f74-acaa-64d4ea768539   ext4                                     
/dev/sda6        b62ada52-d69b-43f1-8658-3cd52626aba3   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
/dev/sr0         /mnt-system              iso9660    (ro,relatime)
/dev/cloop       /KNOPPIX                 iso9660    (ro,relatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1c 01 00 00 00 00 00 00  a7 9b 22 00 ed 05 00 00  |..........".....|
*
00000020  1c 01 00 00 00 00 00 00  95 a1 22 00 5a 05 00 00  |..........".Z...|
*
00000040  1c 01 00 00 00 00 00 00  f0 a6 22 00 e8 05 00 00  |..........".....|
*
00000060  1c 01 00 00 00 00 00 00  d9 ac 22 00 58 05 00 00  |..........".X...|
*
00000080  1c 01 00 00 00 00 00 00  32 b2 22 00 e9 05 00 00  |........2.".....|
*
000000a0  1c 01 00 00 00 00 00 00  1c b8 22 00 60 05 00 00  |..........".`...|
*
000000c0  1c 01 00 00 00 00 00 00  7d bd 22 00 ec 05 00 00  |........}.".....|
*
000000e0  1c 01 00 00 00 00 00 00  6a c3 22 00 5e 05 00 00  |........j.".^...|
*
00000100  1c 01 00 00 00 00 00 00  c9 c8 22 00 ec 05 00 00  |..........".....|
*
00000120  1c 01 00 00 00 00 00 00  b6 ce 22 00 5e 05 00 00  |..........".^...|
*
00000140  1c 01 00 00 00 00 00 00  15 d4 22 00 ee 05 00 00  |..........".....|
*
00000160  1c 01 00 00 00 00 00 00  04 da 22 00 6b 05 00 00  |..........".k...|
*
00000180  1c 01 00 00 00 00 00 00  70 df 22 00 fa 05 00 00  |........p.".....|
*
000001a0  1c 01 00 00 00 00 00 00  6b e5 22 00 5e 05 00 00  |........k.".^...|
000001b0  1c 01 00 00 00 00 00 00  6b e5 22 00 5e 05 80 ac  |........k.".^...|
000001c0  31 7c 83 fe ff ff 02 00  00 00 00 00 bf 01 00 fe  |1|..............|
000001d0  ff ff 05 fe ff ff 02 00  bf 01 00 08 c4 10 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

/home/knoppix/Desktop/boot_info_script055.sh: line 892:  3754 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error
  No volume groups found
mdadm: No arrays found in config file or automatically

I got this when I ran the first command:
> knoppix@Microknoppix:~$ sudo lsof | grep sda5
jbd2/sda5 3757       root  cwd       DIR        0,1        0          1 /
jbd2/sda5 3757       root  rtd       DIR        0,1        0          1 /
jbd2/sda5 3757       root  txt   unknown                                /proc/3757/exe

---

### Post by Rubi1200 on 2011-01-22
Are you able to mount sda5 from Knoppix?

The results do not look good.

Other than the mounting failed error, there seems to be no indication of a file-system.

I will ask some others to take a look, but you may have little choice but to start over again.

---

### Post by ztschutt on 2011-01-22
When I tried to mount the drive I got this error. I really wish I didn't have to erase everything. If you say there is no way I can fix this I will start reinstalling Ubuntu.
> knoppix@Microknoppix:~$ udisks --mount /dev/sda5
Mount failed: Daemon is inhibited

---

### Post by Rubi1200 on 2011-01-22
There is one more thing we can try.

From the LiveCD, run this command (just copy/paste):

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo mount  --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf && sudo chroot /mnt
```*If* this works it will bring you to a root prompt and we can take it from there.

---

### Post by Quackers on 2011-01-22
With my limited knowledge of file systems, it appears that your file system thinks that it's open already. I suspect that may be due to improper shutdown when the power failed. I have seen others with similar problems who have re-installed. I am not syaing it's not fixable! But if it is, I don't know how :-( There are many people here who may have a better idea of what's going on, and whether it can be fixed, than I do though :-)

---

### Post by Rubi1200 on 2011-01-22
Some other options to try and at least rescue your data.

It might be worth trying System Rescue CD or Parted Magic for recovery purposes or to try and mount the partition and see what is going on.

---

### Post by ztschutt on 2011-01-22
That command didn't work so I guess I'll just start reinstalling Ubuntu. Too bad we couldn't save the data. Thanks for trying though.

---

### Post by ztschutt on 2011-01-22
Sadly my home partition was encrypted and I hadn't copied down the key yet, so I can't get any of my data. But thanks anyway.

---

### Post by Rubi1200 on 2011-01-22
Well, you are welcome for the help but I am sorry about the data.

As Quackers pointed out, you may want to be careful in future about hibernating as it seems this can be a problem especially on laptops.

---

