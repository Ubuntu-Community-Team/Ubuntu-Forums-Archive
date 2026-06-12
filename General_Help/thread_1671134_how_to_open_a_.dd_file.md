---
title: "how to open a .dd file?"
date: 2011-01-19
forum: General Help
---

### Post by supasoaker on 2011-01-19
my apologies my first post didn't load properly............

I have just run testdisk and saved some possibly recovered data, but i don't know how to access it.......... it is saved as an image file (.dd) ................ any help much appreciated...!

---

### Post by supasoaker on 2011-01-19
please excuse the bump............

---

### Post by supasoaker on 2011-01-20
bad bumpage.................

---

### Post by anglican on 2011-01-20
> **supasoaker said:**
> my apologies my first post didn't load properly............

I have just run testdisk and saved some possibly recovered data, but i don't know how to access it.......... it is saved as an image file (.dd) ................ any help much appreciated...!The answer depends on whether you've imaged a partition or the entire device. If it's a partition then something like:
```
sudo mount -o loop -t auto /home/yourname/drive_image.dd /mnt/disk_image
```should be what you need. If it's an image of the entire device then take a look at this:

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

H

---

### Post by dandnsmith on 2011-01-20
I suggest you visit [wiki for testdisk](http://www.cgsecurity.org/wiki/TestDisk) where it is all spelt out.

I found it requires careful reading, as the presentation isn't always obvious (seems at times to confuse the saving-to-dd and the restoring files from dd)

Good luck

---

### Post by supasoaker on 2011-01-20
> **anglican said:**
> The answer depends on whether you've imaged a partition or the entire device. If it's a partition then something like:
```
sudo mount -o loop -t auto /mnt/disk_image /home/yourname/drive_image.dd
```should be what you need. If it's an image of the entire device then take a look at this:

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

H

thanks for the help everyone! I found that thread you mentioned above when I searched - didn't do anything, but i have not tried to my wits end yet..........will give it another go and report back.........

---

### Post by supasoaker on 2011-01-20
> **anglican said:**
> The answer depends on whether you've imaged a partition or the entire device. If it's a partition then something like:
```
sudo mount -o loop -t auto /mnt/disk_image /home/yourname/drive_image.dd
```should be what you need. If it's an image of the entire device then take a look at this:

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

H

thanks for the help everyone..............I found the thread you mention above earlier when I did a search - didn't work though........

I get this which is the same as what the guy who posted the thread was complaining about:

```
 dan@dan-desktop:~$ sudo mount -o loop -t auto /mnt/disk_image /home/dan/downloads/image.dd
/mnt/disk_image: No such file or directory 
```Then I tried it as he recommended and still can't get anywhere, when I press enter the next line the terminal prints is:

```
 dan@dan-desktop:~$ 
```

so it doesn't look like it does anything!

---

### Post by anglican on 2011-01-21
> **supasoaker said:**
> thanks for the help everyone..............I found the thread you mention above earlier when I did a search - didn't work though........

I get this which is the same as what the guy who posted the thread was complaining about:

```
 dan@dan-desktop:~$ sudo mount -o loop -t auto /mnt/disk_image /home/dan/downloads/image.dd
/mnt/disk_image: No such file or directory 
```Then I tried it as he recommended and still can't get anywhere, when I press enter the next line the terminal prints is:

```
 dan@dan-desktop:~$ 
```so it doesn't look like it does anything!Try doing:
```
sudo mkdir /mnt/disk_image

```first. You can't mount something on a mountpoint that doesn't exist.

H

---

### Post by psusi on 2011-01-21
> **anglican said:**
> Try doing:
```
sudo mkdir /mnt/disk_image

```first. You can't mount something on a mountpoint that doesn't exist.

H

Or just drop the disk_image part and mount it in /mnt.

---

### Post by supasoaker on 2011-01-22
> **anglican said:**
> Try doing:
```
sudo mkdir /mnt/disk_image

```first. You can't mount something on a mountpoint that doesn't exist.

H

that gives me this:

```


dan@dan-desktop:~$ sudo mkdir /mnt/disk_image
[sudo] password for dan: 
dan@dan-desktop:~$ sudo mount -o loop -t auto /mnt/disk_image /home/dan/downloads/image.dd
/mnt/disk_image: Is a directory


```

Please excuse all the noob questions!

---

### Post by psusi on 2011-01-22
You got the arguments backwards.  It is device/file dir, not the other way around.

---

### Post by supasoaker on 2011-01-23
> **psusi said:**
> You got the arguments backwards.  It is device/file dir, not the other way around.

thanks - I had tried that before but it didn't work, then I found the destination was missing a capital letter. So it now works............however................I now get this:

```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dan@dan-desktop:~$ 

```

I suspected this with some other stuff I tried, anyone have any ideas as to what I can do to repair it? should I start another thread?

---

### Post by psusi on 2011-01-23
Read post #4 again.

---

### Post by supasoaker on 2011-01-27
I did read the post agian thanks. I have had some success but still need guidance if anyone can offer it.

I have managed to restore the HDD to the most recent installation of Ubuntu. This is great news!

The problem is I need to recover data that was on the installation before that, I perform a 'deeper search' on the HDD but am unable to properly decipher what to do next.

A 'deeper search' does show data has been found, but usually reports that it is unable to find partition information. This I would expect but was under the impression that Testdisk can read the data without such partition tables.

I am going through it all and am going to put together the details to publish if anyone can help.

Any comments/guidance on where I am currently welcome!

---

### Post by psusi on 2011-01-27
It can't read data that has been overwritten.  If you formatted the partition then everything needed to locate files is gone.

---

### Post by supasoaker on 2011-01-27
After a 'deep search' I get this:

```


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 200 GB / 186 GiB - CHS 24322 255 63

The harddisk (200 GB / 186 GiB) seems too small! (< 286 GB / 266 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                11510 254  9 34840 154  2  374790144
  Linux                11513 204 20 34843 104 13  374790144
  Linux                11514  79 22 34843 234 15  374790144

[ Continue ]
EXT4 Large file Sparse superblock Recover, 191 GB / 178 GiB


```Then clicking 'continue I get this screen:

```


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 200 GB / 186 GiB - CHS 24322 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 24318 254 63  390684672
D HPFS - NTFS              0  32 33    12 223 19     204800
D Linux                    0  32 33 23329 187 26  374790144
D HPFS - NTFS             12 223 19    25 159  5     204800
D HPFS - NTFS             12 223 20 24320 199  7  390506496
D HPFS - NTFS          16963   0  1 24319 254 63  118190205
D Linux Swap           23329 219 59 24321  73 56   15927280

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS found using backup sector!, 200 GB / 186 GiB




NTFS found using backup sector!, 104 MB / 100 MiB
EXT4 Large file Sparse superblock, 191 GB / 178 GiB
NTFS, 104 MB / 100 MiB
NTFS found using backup sector!, 199 GB / 186 GiB
NTFS found using backup sector!, 60 GB / 56 GiB
SWAP2 version 1, 8154 MB / 7776 MiB


```listed at the bottom is what is printed on the screen as I choose different partitions going downwards.

I have tried a cople of things and have no idea how to interpret this properly. I had data copied on the HDD running a fresh install of Ubuntu, formatted by accident with another fresh install of Ubuntu now I need to try and get my data back........the data I need was all copied into one folder which was around 110 GB........

Any help/advice much appreciated!

---

### Post by supasoaker on 2011-01-27
> **psusi said:**
> It can't read data that has been overwritten.  If you formatted the partition then everything needed to locate files is gone.

wow - but i thought only the partition tables would be erased and data can still be recovered by reading the disk............? As I said in the post above it was overwritten by another fresh install - it doesn't overwrite the whole HDD first does it?

I also fear I made a mistake early on as I haven't used Testdisk before, I know it all a bit better now though and above print out is what I am seeing on my screen - this will be one for the books if I can't get my data back..........

---

### Post by psusi on 2011-01-27
> **supasoaker said:**
> wow - but i thought only the partition tables would be erased and data can still be recovered by reading the disk............? As I said in the post above it was overwritten by another fresh install - it doesn't overwrite the whole HDD first does it?

If all you did was erase the partition table, then testdisk can rebuild it after it scans the disk and finds the partition.  If you formatted the partition, then the inodes were overwritten so there is no way to figure out what files were where.

---

### Post by supasoaker on 2011-01-27
yep - as far as I am aware I only erased the partition tables, it was a standard install of Ubuntu which says 'erase disks and install' but as far as I am aware all this does is affect the partition tables..............

---

### Post by psusi on 2011-01-27
> **supasoaker said:**
> yep - as far as I am aware I only erased the partition tables, it was a standard install of Ubuntu which says 'erase disks and install' but as far as I am aware all this does is affect the partition tables..............

No, it repartitions the disk, then formats the partition, and then copies files to it.

---

