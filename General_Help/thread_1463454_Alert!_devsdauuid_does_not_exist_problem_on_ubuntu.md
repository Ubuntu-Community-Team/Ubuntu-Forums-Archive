---
title: "Alert! /dev/sda/uuid does not exist problem on ubuntu 9.10"
date: 2010-04-27
forum: General Help
---

### Post by kennyboi9o9of88 on 2010-04-27
I'm fairly new to ubuntu and don't really know how to do much with it besides simply use it. Aside from that note, I have been using it for about a month or two and just yesterday morning, it didn't boot. I would get the message that the uuid file does not exist. I've been online looking for fixes since yesterday morning and nothing has helped at all. I've read online that I should run fdisk -l to obtain info to share with others, but that command doesn't work in any command prompt I open. 
 
I am running Ubuntu 9.10 with the latest patches and I'm sure you guys know that it runs Grub2 loader...if that helps at all. 
 
Any help would be greatly appreciated. I know I'll get flamed for being a noob but go ahead. As long as my computer is fixed I'll take what you got.

---

### Post by CannibalZerg on 2010-04-27
Run **sudo blkid** - it shows disk's UUID. 
Here you can find more details: [http://www.mail-archive.com/debian-user@lists.debian.org/msg551875.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg551875.html)

---

### Post by john newbuntu on 2010-04-27
Welcome to Ubuntu and to the forums Kenny.  It would help us a lot if you could furnish more details.

Boot from the Ubuntu liveCD, choose "try ubuntu without any changes" and open the following link in a browser:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

This is our forum member Meirfra's bootinfoscript.  Download and run it using the procedure given here:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The output of this script goes into a file called "RESULTS.TXT" on your desktop and contains a whole lot of details.  Please post this output.

---

### Post by kennyboi9o9of88 on 2010-04-28
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2fc5becd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   500,029,299   499,822,452   7 HPFS/NTFS
/dev/sda3         500,029,488   976,773,167   476,743,680   5 Extended
/dev/sda5         500,029,551   964,695,311   464,665,761  83 Linux
/dev/sda6         964,695,375   976,773,167    12,077,793  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33543353

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   490,231,807   490,024,960   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9454723654721AE6                       ntfs       System Reserved               
/dev/sda2        688C7D858C7D4F16                       ntfs                                     
/dev/sda5: ambivalent result (probably more filesystems on the device)
/dev/sda6        b6cd92c8-b3a2-4666-9e42-6bbef9dda308   swap                                     
/dev/sdb1        307CEE4E7CEE0E82                       ntfs       System Reserved               
/dev/sdb2        2A0CF0EE0CF0B5C3                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


Hope this helps.

---

### Post by john newbuntu on 2010-04-28
Even though the partition info identifies /dev/sda5 to be a linux partition, the boot info summary has no knowledge of it.  Perhaps repairing /dev/sda5 might help.
Boot from a liveCD, open up a terminal (application->accessories->terminal) and run this command:
```
sudo e2fsck -C0 -p -f -v /dev/sda5
```

If this gives any errors, then run:
```
sudo e2fsck -f -y -v /dev/sda5
```

Then try booting normally without the liveCD.  If you are still unable to boot, post the output of the above commands.

---

### Post by kennyboi9o9of88 on 2010-04-29
I ran this command and got
```
sudo e2fsck -C0 -p -f -v /dev/sda5
```

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
                                                                               
  167041 inodes used (1.15%)
     145 non-contiguous files (0.1%)
     119 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 144441/99/37
18389983 blocks used (31.66%)
       0 bad blocks
       1 large file

  118913 regular files
   19622 directories
      68 character device files
      26 block device files
       0 fifos
     391 links
   28395 symbolic links (22352 fast symbolic links)
       8 sockets
--------
  167423 files
```
It didn't work. I tried to boot and still get the same alert! problem
I'll try the second code and see what happens

---

### Post by kennyboi9o9of88 on 2010-04-29
Both codes worked perfectly fine without errors, but the problem still persist

---

### Post by john newbuntu on 2010-04-29
When it complains about that error, it generally should drop to a shell which is a grub> prompt.  At this prompt, try typing these commands and see if it helps:

```
ls -l (hd0,5)/
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img
boot
```

If this does not work, again post the outputs. Also, post any other output that you get prior to the "Alert.." error on boot.

---

### Post by kennyboi9o9of88 on 2010-04-30
when you say type in the code ls -l (hd0, 5)/
do you mean I should type it in after I try to boot in the black screen after it gives the drop to shell message?

I tried typing in ls -l (hd0, 5)/ but it says 
/bin/sh: syntax error: "(" unexpected

If i try it without parantheses, it says 
ls: hd0: no such file or directory
ls: 5/ no such file or directory

---

### Post by john newbuntu on 2010-04-30
I was under the impression that you are still in the grub menu. It appears as though you are getting a shell prompt like "$" or "#".  The commands I gave you should be run on the grub command line.

So when you boot into Ubuntu, as soon as you get the grub boot screen, press "c".  This will get you into the command line mode and a prompt like "grub>" where you would type those commands.

---

### Post by kennyboi9o9of88 on 2010-05-03
omg john you are a life saver. It worked and I would have never ever figured it out.

Thanks so much for everything. I owe you one haha

---

