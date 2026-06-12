---
title: "No Boot - Get Busybox"
date: 2011-05-01
forum: General Help
---

### Post by jackn on 2011-05-01
Asus laptop, Ubuntu 11.04.

The system won't boot.
Instead, I get Busybox, a shell. 
I've had no trouble booting after upgrading to Natty a day or two ago. I've booted successfully many times since.

I'm now connecting using XP, as I double boot.
So, no hardware issues here.

Importantly, I can't even use the 'Recovery Mode' option offered in the Grub menu. It, too, yields Busybox.

The issue is mentioned in several threads, always relating to installation attempts, it seems, which isn't my case.

I've tried to solve the issue by following what's suggested in several threads: hitting 'e' in the Grub menu to edit the boot, and changing the splash command to 'all_generic_ide'. While I've tried all possible combinations, I don't really know how to go about this, let alone whether it should help. 
The boot commands I see when I hit 'e' show 'splash' twice. I've tried modifying by adding 'all_generic_ide' after either 'splash' or replacing either one or both with it.
To no avail.

At this point, I cannot boot into Natty Ubuntu.
When I get into Busybox, I have to turn off  the laptop manually using the power switch.

What can I do?
Thanks,
jackn

---

### Post by Rubi1200 on 2011-05-01
Hi,
sorry to hear you are experiencing these troubles.

The best thing to do right now is the following so we can get a better overview of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jackn on 2011-05-01
OK, Rubi, I'm on it.
Thank you very much.
jackn

---

### Post by jackn on 2011-05-01
OK, Rubi, here are the contents of the RESULTS.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,302,559    29,302,497   7 HPFS/NTFS
/dev/sda2          29,302,621   234,440,703   205,138,083   5 Extended
/dev/sda5          29,302,623    87,891,614    58,588,992  83 Linux
/dev/sda6         195,379,200   234,440,703    39,061,504  83 Linux
/dev/sda7         187,553,792   195,366,911     7,813,120  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4E344889344875CD                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        23bc9754-d880-4af2-aa50-3454d1b62a8d   ext3                                     
/dev/sda6        4db020c6-c4f0-403f-bd65-1d5c570ab594   ext4                                     
/dev/sda7        0828c8f0-ac36-4198-9e4b-f76a8e3de074   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2e 3f 3e 3f 44 3f 4d 3f  5d 3f 63 3f 6a 3f 7c 3f  |.?>?D?M?]?c?j?|?|
00000010  84 3f 89 3f 9b 3f a4 3f  b4 3f ba 3f bf 3f d3 3f  |.?.?.?.?.?.?.?.?|
00000020  d8 3f ea 3f 00 f0 09 00  44 01 00 00 f7 31 17 32  |.?.?....D....1.2|
00000030  1c 32 2c 32 3e 32 70 32  b1 32 b8 32 c2 32 c7 32  |.2,2>2p2.2.2.2.2|
00000040  cc 32 dc 32 06 33 1f 33  54 33 87 34 97 34 9c 34  |.2.2.3.3T3.4.4.4|
00000050  a1 34 b1 34 d6 34 db 34  eb 34 0c 35 1d 35 5a 35  |.4.4.4.4.4.5.5Z5|
00000060  5f 35 72 35 98 35 9d 35  b0 35 c6 35 cf 35 d8 35  |_5r5.5.5.5.5.5.5|
00000070  e6 35 06 36 0f 36 1d 36  27 36 64 36 6e 36 89 36  |.5.6.6.6'6d6n6.6|
00000080  8e 36 a6 36 b9 36 ce 36  d3 36 eb 36 12 37 35 37  |.6.6.6.6.6.6.757|
00000090  4a 37 51 37 56 37 6e 37  84 37 8d 37 92 37 aa 37  |J7Q7V7n7.7.7.7.7|
000000a0  c3 37 ca 37 df 37 ee 37  22 38 28 38 3e 38 43 38  |.7.7.7.7"8(8>8C8|
000000b0  48 38 58 38 81 38 86 38  98 38 fc 38 0e 39 35 39  |H8X8.8.8.8.8.959|
000000c0  3a 39 4c 39 a7 39 b9 39  e6 39 eb 39 fd 39 33 3a  |:9L9.9.9.9.9.93:|
000000d0  3c 3a 42 3a 47 3a 5c 3a  61 3a 73 3a b5 3a cc 3a  |<:B:G:\:a:s:.:.:|
000000e0  0b 3b 12 3b 22 3b 30 3b  4d 3b 5a 3b 60 3b 75 3b  |.;.;";0;M;Z;`;u;|
000000f0  92 3b a5 3b b6 3b c1 3b  ca 3b d2 3b d7 3b e7 3b  |.;.;.;.;.;.;.;.;|
00000100  10 3c 15 3c 21 3c 48 3c  77 3c 7c 3c 8e 3c b8 3c  |.<.<!<H<w<|<.<.<|
00000110  c3 3c c9 3c ce 3c e3 3c  e8 3c fa 3c 18 3d 48 3d  |.<.<.<.<.<.<.=H=|
00000120  6d 3d 83 3d 89 3d 8e 3d  98 3d a7 3d b6 3d bb 3d  |m=.=.=.=.=.=.=.=|
00000130  cb 3d d0 3d e6 3d f5 3d  fc 3d 02 3e 14 3e 3d 3e  |.=.=.=.=.=.>.>=>|
00000140  42 3e 55 3e 68 3e 76 3e  7b 3e 89 3e b9 3e f7 3e  |B>U>h>v>{>.>.>.>|
00000150  11 3f 4a 3f 4f 3f 69 3f  79 3f 87 3f be 3f c3 3f  |.?J?O?i?y?.?.?.?|
00000160  d5 3f ec 3f fa 3f 00 00  00 00 0a 00 e0 00 00 00  |.?.?.?..........|
00000170  25 30 2a 30 3d 30 50 30  5e 30 63 30 71 30 a1 30  |%0*0=0P0^0c0q0.0|
00000180  dc 30 f6 30 2c 31 46 31  56 31 64 31 98 31 aa 31  |.0.0,1F1V1d1.1.1|
00000190  c1 31 cf 31 fa 31 ff 31  12 32 25 32 33 32 38 32  |.1.1.1.1.2%23282|
000001a0  46 32 76 32 b1 32 cb 32  01 33 1b 33 2b 33 39 33  |F2v2.2.2.3.3+393|
000001b0  6d 33 7f 33 96 33 a4 33  d0 33 d5 33 e7 33 00 fe  |m3.3.3.3.3.3.3..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 40 ff 7d 03 00 fe  |..........@.}...|
000001d0  ff ff 05 fe ff ff a3 f0  e5 09 00 38 54 02 00 00  |...........8T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by jackn on 2011-05-01
Rubi, RESULTS.txt suggests studying the end of the SYSLOG:
```
ubuntu@ubuntu:~$ dmesg | tail
[  581.200642]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  581.200665]         0c a9 ce 25 
[  581.200674] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  581.200685] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 0c a9 cd c8 00 01 00 00
[  581.200707] end_request: I/O error, dev sda, sector 212454949
[  581.200731] JBD: Failed to read block at offset 4553
[  581.200742] JBD: recovery failed
[  581.200745] ata1: EH complete
[  581.200751] EXT4-fs (sda6): error loading journal

```

Indeed, sda6, as suggested already by RESULTS.txt, is at fault.
What to do about it, I wouldn't know.

Hope this is useful, and thanks,
jackn

---

### Post by Rubi1200 on 2011-05-01
Do you know with certainty which partition is the / root partition?

I assume sda5 may be /home since it is formatted as ext3. Is that correct?

In any event, sda6 has a problem:
> wrong fs type, bad option, bad superblock on /dev/sda6,        missing codepage or helper program, or other error

This is what you can try from the LiveCD to try and fix it:
```
sudo e2fsck -f -y -v /dev/sda6
```
Let the command complete and, assuming there are no errors, you should be able to reboot, taking out the CD, and be back in Ubuntu.

---

### Post by jackn on 2011-05-01
I'm pretty sure that sda6, the faulty one, is root. 
sda5 is a 'files' (data) partition which is, strictly speaking, part of /home, so /home is on sda6, like /.

From the live CD, I cannot mount sda6, while I can sda5, in which I can see my files. 
As only sda6 is left unknown (other two are Swap and Win), it must be root. Doesn't it also make sense given the failure to boot? 
I mean, wouldn't the system boot alright (and then fail to mount the data files) if sda5 had a problem instead of sda6?

In any case, I'm trying the remedy you've suggested, Rubi.
Will report.

Thanks,
Haim

---

### Post by jackn on 2011-05-01
Worked a treat...
I'm working off of the hard disk now.
Lovely.

Checked all the partitions from Disk Utility, and indeed they are what we figured above.

I wonder how the / partition got corrupted in the first place...
Oh, well.

This is very impressive.
Thank you very much for all the wonderful help, Rubi.

jackn

---

### Post by Rubi1200 on 2011-05-01
No problem, you are more than welcome :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

