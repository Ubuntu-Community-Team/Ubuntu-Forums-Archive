---
title: "Computer won't boot"
date: 2010-02-23
forum: General Help
---

### Post by blur xc on 2010-02-23
For some reason it can't find the / partition while booting Ubuntu 9.10 nbr.

I boot into the live usb and I can mount the partition and access the files, but in palimpset it says that my /dev/sda5 is an unrecognized partition.

```
sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 194161/1313280 files, 839651/5242880 blocks (check in 2 mounts)

``````


sudo fsck -fpv /dev/sda5
fsck from util-linux-ng 2.16

  194161 inodes used (14.78%)
     158 non-contiguous files (0.1%)
     172 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 153650/23
  839651 blocks used (16.02%)
       0 bad blocks
       1 large file

  131340 regular files
   16486 directories
      68 character device files
      26 block device files
       0 fifos
     389 links
   46225 symbolic links (40377 fast symbolic links)
       7 sockets
--------
  194541 files
```

```
sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="2fc3ac1c-20c7-4c99-93d2-69ce7363b95a" TYPE="ext3" 
/dev/sda1: UUID="CABC9824BC980CD7" TYPE="ntfs" 
/dev/sda3: LABEL="PE" UUID="CCED-990E" TYPE="vfat" 
/dev/sda6: UUID="eeb91c58-2b5f-4939-ade8-0090bea6f029" TYPE="swap" 
/dev/sda7: UUID="a0c247b7-ff52-4db4-9f77-21facb5da92e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="B83B-24EB" TYPE="vfat" 

```

```
cat etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
# UUID=b429650a-19bd-4231-afb1-bd3f6502e3d1 /               ext4    errors=remount-ro 0       1
/dev/sda5    /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a0c247b7-ff52-4db4-9f77-21facb5da92e /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=eeb91c58-2b5f-4939-ade8-0090bea6f029 none            swap    sw              0       0

```

blkid didn't show a uuid for sda5 which I thought was weird.  I found instruction on the internet to assing a UUID, and when I did that, all that happened was that XP would no longer boot either.  Then I tried changing the fstab (as shown above) to mount the drive by /dev/sda5 instead of using the uuid, and that didn't work.  I suspect the problem is with grub, but dunno.

Thanks,
BM

---

### Post by blur xc on 2010-02-23
I thought I should add these-

---

### Post by blur xc on 2010-02-25
bump-

Seriously, no one has a clue for how to fix this?

thanks,
BM

---

### Post by oldfred on 2010-02-25
It seems strange that fstab says the original install was sda7 and the UUID matches. And that blkid does not show sda5??

Lets see what the boot script shows:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by blur xc on 2010-02-25
> **oldfred said:**
> It seems strange that fstab says the original install was sda7 and the UUID matches. And that blkid does not show sda5??

Lets see what the boot script shows:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Ok- got it!  Thanks-```


              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

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

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20e3bf26

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2          41,945,715   302,230,844   260,285,130   5 Extended
/dev/sda5          41,945,778    83,891,429    41,945,652  83 Linux
/dev/sda6         298,037,943   302,230,844     4,192,902  82 Linux swap / Solaris
/dev/sda7          83,891,493   298,037,879   214,146,387  83 Linux
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dfa76

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,015,231     2,015,200   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2fc3ac1c-20c7-4c99-93d2-69ce7363b95a   ext3                                     
/dev/sda1        CABC9824BC980CD7                       ntfs                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda5: ambivalent result (probably more filesystems on the device)
/dev/sda6        eeb91c58-2b5f-4939-ade8-0090bea6f029   swap                                     
/dev/sda7        a0c247b7-ff52-4db4-9f77-21facb5da92e   ext3                                     
/dev/sdb1        B83B-24EB                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

---

### Post by meierfra. on 2010-02-25
> dev/sda5: ambivalent result (probably more filesystems on the device)


blkid is confused about  the file system  of /dev/sda5.  

Could you post the output of

```
sudo hexdump -C -s 0x410 -n 2 /dev/sda5
```

Try  mounting  /dev/sda5 via:

```
sudo mount /dev/sda5 -t ext4 /mnt
```

I have seen similar cases where you just have to create a file on /dev/sda5 to fix the problem. So if mounting was successful do
```
sudo touch /mnt/empty_file
sudo blkid -p /dev/sda5
```

If blkid  was able to determine the UUID of /dev/sda5, you should be all set. 

But if "blkid -p" returns the  "ambivalent result" result error,we will  have to have a closer look at /dev/sda5:

There is a program called [wipefs ]("http://karelzak.blogspot.com/2009/11/wipefs8.html") which is able to detect the signatures  of most file systems and is also able to erase all the unwanted signatures.  Unfortunately its is very new  and  you will have to compile it from source. If you would like to give that a try, here are the instructions:

Download   [util-linux-ng-2.17.tar.gz]("ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/v2.17/util-linux-ng-2.17.tar.gz") to your Desktop.

Right click the file and choose "Extract Here"

Open a terminal.

```
cd ~/Desktop
mkdir Util
cd util-linux-ng-2.17
sudo ./configure --prefix=$HOME/Desktop/Util --without-ncurses 
sudo make
sudo make install
```

This installed the Util-Linux package to the folder Util on your desktop.
"make" and "make install" probably will return few error messages.  But "wipefs" still should work just fine.

Next  run wipefs via

```
cd  ~/Desktop/Util/sbin
sudo ./wipefs /dev/sda5

```

 "wipefs /dev/sda5"  displays some basic information on all the file systems found on /dev/sda5,    but does  not change anything.   Post that  information.

---

### Post by blur xc on 2010-02-27
> **meierfra. said:**
> blkid is confused about  the file system  of /dev/sda5.  

Could you post the output of

```
sudo hexdump -C -s 0x410 -n 2 /dev/sda5
```Try  mounting  /dev/sda5 via:



Here's the output-
```
00000410  8f 13                                             |..|
00000412

```

Thanks for your help.  I'll try the other instructions right now.  The drive does mount just fine from using the mount command.

BM

---

### Post by blur xc on 2010-02-27
> **meierfra. said:**
>  There is a program called [wipefs ]("http://karelzak.blogspot.com/2009/11/wipefs8.html") which is able to detect the signatures  of most file systems and is also able to erase all the unwanted signatures.  Unfortunately its is very new  and  you will have to compile it from source. If you would like to give that a try, here are the instructions:

Download   [util-linux-ng-2.17.tar.gz]("ftp://ftp.kernel.org/pub/linux/utils/util-linux-ng/v2.17/util-linux-ng-2.17.tar.gz") to your Desktop.

Right click the file and choose "Extract Here"

Open a terminal.

```
cd ~/Desktop
mkdir Util
cd util-linux-ng-2.17
sudo ./configure --prefix=$HOME/Desktop/Util --without-ncurses 
sudo make
sudo make install
```This installed the Util-Linux package to the folder Util on your desktop.
"make" and "make install" probably will return few error messages.  But "wipefs" still should work just fine.

Next  run wipefs via

```
cd  ~/Desktop/Util/sbin
sudo ./wipefs /dev/sda5

``` "wipefs /dev/sda5"  displays some basic information on all the file systems found on /dev/sda5,    but does  not change anything.   Post that  information.

Ok- did like you said and creating a file on sda5 didn't fix it.  wifefs didn't work either.

```
./wipefs /dev/sda5
wipefs: probing initialization failed
```

Thanks,
BM

---

### Post by meierfra. on 2010-02-27
> ```
./wipefs /dev/sda5
wipefs: probing initialization failed
```

Did you use "sudo"?:


```

cd  ~/Desktop/Util/sbin
[COLOR="Red"]sudo [/COLOR]./wipefs /dev/sda5

```

---

### Post by blur xc on 2010-02-27
> **meierfra. said:**
> Did you use "sudo"?:


```

cd  ~/Desktop/Util/sbin
[COLOR=Red]sudo [/COLOR]./wipefs /dev/sda5

```

Oops- I feel a bit stupid.  

So- I ran wipefs and it spit out the filesystem type and the uuid- then I ran blkid and it spit out the uuid for sda5, so I rebooted and BAM!  I'm posting from my all fixed ubuntu system.

It's amazing how simple the fix was- yet it took a month to find it!  

Now it's time to do some updates and hope nothing else breaks...

Thanks!
BM

---

### Post by meierfra. on 2010-02-27
> I'm posting from my all fixed ubuntu system.
Great.

But I'm a little bit confused.  Just running "" sudo ./wipefs /dev/sda5" should not have fixed anything.  Did you do anything else?  Maybe creating the file on /dev/sda5 fixed the problem (sometimes it takes a couple of seconds for the  file system to update, so if you ran "blkid write after you created the file, it might have been to early to detect a change)

---

### Post by meierfra. on 2010-02-27
Your problem was fixed by creating the file. I just found this:

```
# Minix filesystems - Juan Cespedes 
0x410	leshort		0x137f		Minix filesystem
[COLOR="Red"]0x410[/COLOR]	leshort		[COLOR=RED]0x138f	[/COLOR]	Minix filesystem, 30 char names
0x410	leshort		0x2468		Minix filesystem, version 2
0x410	leshort		0x2478		Minix filesystem, version 2, 30 char nam

```

Which matches your output:

```
[COLOR="Red"]00000410  8f 13  [/COLOR]                                           |..|
00000412
```

So you have been affected by this bug:

[https://bugs.launchpad.net/ubuntu/+bug/518582](https://bugs.launchpad.net/ubuntu/+bug/518582)

Would you mind following the link and then click on 

"This bug affects x people" Does this bug affect you" ( or "This bug affects you)

to let launchpad know that you have been affected by the bug.
You might also leave a comment.   Thanks.

---

### Post by blur xc on 2010-02-27
> **meierfra. said:**
> Your problem was fixed by creating the file. I just found this:

```
# Minix filesystems - Juan Cespedes 
0x410    leshort        0x137f        Minix filesystem
[COLOR=Red]0x410[/COLOR]    leshort        [COLOR=RED]0x138f    [/COLOR]    Minix filesystem, 30 char names
0x410    leshort        0x2468        Minix filesystem, version 2
0x410    leshort        0x2478        Minix filesystem, version 2, 30 char nam

```Which matches your output:

```
[COLOR=Red]00000410  8f 13  [/COLOR]                                           |..|
00000412
```So you have been affected by this bug:

[https://bugs.launchpad.net/ubuntu/+bug/518582](https://bugs.launchpad.net/ubuntu/+bug/518582)

Would you mind following the link and then click on 

"This bug affects x people" Does this bug affect you" ( or "This bug affects you)

to let launchpad know that you have been affected by the bug.
You might also leave a comment.   Thanks.

thanks!  I did like you said and clicked on this bug affects me...

BM

---

### Post by kamalghazali on 2010-11-07
thanks meierfra, 

My ubuntu stuck with same bug, for month tried to look for solution. Finally manage to solved them by following your simple but yet precise instruction

have some :popcorn:

---

