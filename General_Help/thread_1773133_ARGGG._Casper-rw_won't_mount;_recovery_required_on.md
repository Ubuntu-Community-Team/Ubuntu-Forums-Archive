---
title: "ARGGG. Casper-rw won't mount; recovery required on readonly filesystem"
date: 2011-06-01
forum: General Help
---

### Post by Baniita on 2011-06-01
My live USB won't boot ("no operating system found"), so I at least want to recover the files I lost. I need these files ASAP, the latest by Friday.

 I don't even know if I tried to mount it correctly... Here's what I did.

EDIT: Yes, I AM a total nub. 8'D Please excuse me and my lack of ubuntu and programming skeillz.

```

Note: 'YULLENATION' is the name of my USB... Don't ask why.

root@ubuntu:/media/YULLENATION# mkdir /media/casper
root@ubuntu:/media/YULLENATION# mount -o loop casper-rw /media/casper
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
root@ubuntu:/media/YULLENATION# dmesg | tail
[ 3240.695701] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3260.659576] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3315.560208] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3320.551226] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3340.515057] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3480.262199] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3485.253120] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3515.199245] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[ 3530.655339] EXT3-fs (loop1): recovery required on readonly filesystem
[ 3530.655347] EXT3-fs (loop1): error: write access unavailable, cannot proceed
```So what is the problem here? Can anyone help me identify and solve it?
I really, really need to recover the files. They're just text documents, but it took me a long time and a lot of effort to get them done. Ideally, I'd like to fix the whole USB so it'll be bootable, but I'm more concerned about my files... (I had forgotten they were there, and didn't back them up. So stupiiiiiid.)


**Relevant (?) Boot Info Script:**
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.

sdd1: __________________________________________________________________________

    File system:       udf
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          8,064    15,646,719    15,638,656   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs 
/dev/sdd1                                               udf        YULLENATION

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/YULLENATION       udf        (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


```

---

### Post by Baniita on 2011-06-01
Oh man, if I only knew what the problem was. I don't even know where to start...

Edit1: Looked around more threads... Not working. = ___= SIGH....

---

