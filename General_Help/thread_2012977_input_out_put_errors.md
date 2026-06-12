---
title: "input out put errors"
date: 2012-06-30
forum: General Help
---

### Post by qwertyjjj on 2012-06-30
I am trying to transfer data to Dropbox, specifically, my thunderbir dprofile so I can get access to email while travelling using my usb stick and other computers.
I get the fllowing error:
Error while copying "global-messages-db.sqlite-journal".
Error opening file: Input/output error

Strangely enough, I also get this error while trying to copy VirtualBox VMs to a usb drive so I am not sure what is causing this.

---

### Post by qwertyjjj on 2012-07-01
Any idea son how to solve this?
Should I be using the terminal to copy large files instead of nautilus?
The thunderbird profile is 750Mb in folder files, no idea why sqllite doesn;t copy.
The VMs are 10Gb each.

---

### Post by sudodus on 2012-07-01
Are you trying to copy those data while the application is open?

---

### Post by qwertyjjj on 2012-07-01
> **sudodus said:**
> Are you trying to copy those data while the application is open?

No. Both Thiunderbird and VB are closed.
It starts copying. 
Thunderbird always fails on the sqlite file.
VB always fails about 2mins into the copying.
Is there a way to copy with verbose output to get a more detailed error?

---

### Post by sudodus on 2012-07-01
> **qwertyjjj said:**
> No. Both Thiunderbird and VB are closed.
It starts copying. 
Thunderbird always fails on the sqlite file.
VB always fails about 2mins into the copying.
Is there a way to copy with verbose output to get a more detailed error?
Is ***sqlite*** running with that file open?

The answer to your question is yes. It can be done with ***cp*** and the option -v (verbose). See ```
man cp
``` A better program for backup or copying is ***rsync*** which also has the option -v for verbose. ```
man rsync
``` is a good manual, almost a tutorial :-)

---

### Post by qwertyjjj on 2012-07-01
> **sudodus said:**
> Is ***sqlite*** running with that file open?

The answer to your question is yes. It can be done with ***cp*** and the option -v (verbose). See ```
man cp
``` A better program for backup or copying is ***rsync*** which also has the option -v for verbose. ```
man rsync
``` is a good manual, almost a tutorial :-)

I can't rsync as it's to an external hardrive that runs on some sort of Windows partition and I'm presuming the firmware on it is also on Windows? It's an iomega network drive.

Can't find anything with sqlite running and there are no bad bocks either:
j-media-centre@jmediacentre-A880G:~$ sudo badblocks -v /dev/sdb1 > bad-blocks
[sudo] password for j-media-centre: 
Checking blocks 0 to 488384000
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

j-media-centre@jmediacentre-A880G:~$ pidof sqlite
j-media-centre@jmediacentre-A880G:~$

---

### Post by sudodus on 2012-07-01
If you have free space on your internal drive, try to copy to an empty directory and make a compressed file of it, for example a tarball, that you should be able to copy to your external storage (Dropbox) or network drive.

---

### Post by qwertyjjj on 2012-07-02
> **sudodus said:**
> If you have free space on your internal drive, try to copy to an empty directory and make a compressed file of it, for example a tarball, that you should be able to copy to your external storage (Dropbox) or network drive.

An error occurred while adding files to the rnal drive again.
Why would xipping up the file and copying work?
It seems to have worked o the VMs and on the thunderbird profile.

cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/02. Madder Rose - Overflow [FC Kahuna Mix].mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/11. Medway - Flanker.mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/03. A.D.N.Y. pres. Leiva - Something For The Soul.mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/07. Lexicon Avenue - Here I Am [Hard Mix].mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/06. Francesco Farfa - Tribe & Trance [Voyager Remix].mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/04. LSG - Into Deep [Medway Remix].mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/08. Luzon - The Baguio Track.mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/09. Cevin Fisher - Music Saved My Life.mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/10. Jean-Phillippe Aviance - Useless.mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/05. Sphere - Gravi Tech.mp3': No such file or directory
cp: cannot create regular file `/home/j-media-centre/.gvfs/backup on iomega.local/Music/Various - Global Underground #014: Hong Kong - Mixed By John Digweed (Disc 1)/01. Underworld - Cups [Salt City Orchestra Mix].mp3': No such file or directory
j-media-centre@jmediacentre-A880G:~$

---

### Post by sudodus on 2012-07-02
> An error occurred while adding files to the [COLOR="Red"]rnal[/COLOR] drive again.

What is rnal?

Maybe the file names contain characters that have a special meaning to the shell and or file system. Try renaming one of the files and see if it works better.

---

### Post by qwertyjjj on 2012-07-02
> **sudodus said:**
> What is rnal?

Maybe the file names contain characters that have a special meaning to the shell and or file system. Try renaming one of the files and see if it works better.

rnal = external but a typo.
But I am getting these input ouput on lots of things VMs, thunderbird profile, music folder. I'm pretty sure they copied correctly before.
No bad blocks on anything sow aht else can I tourbleshoot?

---

### Post by sudodus on 2012-07-02
Bad blocks: you can check with the S.M.A.R.T. information of the drives.

File system corruption is tested in by the own software:

For ext3 and ext4 file systems, when you boot from a CD or USB linux boot drive and mount no other drive ```
sudo e2fsck -f /dev/sdxy
``` For example use the Ubuntu install CD/USB.

For FAT32 and NTFS file systems, you boot Windows and run ```
chkdsk /f
``` from a command line interface.

---

### Post by qwertyjjj on 2012-07-03
> **sudodus said:**
> Bad blocks: you can check with the S.M.A.R.T. information of the drives.

File system corruption is tested in by the own software:

For ext3 and ext4 file systems, when you boot from a CD or USB linux boot drive and mount no other drive ```
sudo e2fsck -f /dev/sdxy
``` For example use the Ubuntu install CD/USB.

For FAT32 and NTFS file systems, you boot Windows and run ```
chkdsk /f
``` from a command line interface.

Is there anything else it could be?
Seeing as it happens regardless of the medium I copy to (internal, extHDD, or extUSB) could it be the internal drive?
I had a problem a while back where the internal drive was maxed out and it changed some permissions on files somehow so am not sure if that is related.

Here is the tar error which is separate to the Music folder errors listed earlier in the thread:
tar: Poker/Poker.vbox-tmp: Cannot open: Input/output error
tar: Exiting with failure status due to previous errors

---

### Post by sudodus on 2012-07-03
> **qwertyjjj said:**
> Is there anything else it could be?
Seeing as it happens regardless of the medium I copy to (internal, extHDD, or extUSB) could it be the internal drive?
I had a problem a while back where the internal drive was maxed out and it changed some permissions on files somehow so am not sure if that is related.

Here is the tar error which is separate to the Music folder errors listed earlier in the thread:
tar: Poker/Poker.vbox-tmp: Cannot open: Input/output error
tar: Exiting with failure status due to previous errors

1. You can use the tips in post #11 to check the internal drive too, the drive itself as well as its file systems.

2. And yes, since you know that you had problems with permissions, that can certainly be the cause of your problems.

*. I suggest that you ***backup*** all your personal files. Boot from a CD or USB linux boot drive and mount the drives from and to where you want to backup files and copy the files via cp, rsync, or a file browser.

If this works well, it is probably something bad with the operating system (bad installation). If it also works badly, there might be something wrong with either of the drives (physically or logically) or maybe a power supply unit, that is not delivering enough voltage and current to the attached units.

Please describe your drives, physical size, connection and power supply (direct or via USB for the external drive) and also post the output of
```
sudo fdisk -lu

```and
```
df
```
and
```
cat /etc/fstab
```

---

### Post by qwertyjjj on 2012-07-04
```

j-media-centre@jmediacentre-A880G:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c0af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945661439   972829696   83  Linux
/dev/sda2      1945663486  1953523711     3930113    5  Extended
/dev/sda5      1945663488  1953523711     3930112   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4024 MB, 4024434688 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7860224 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7487a834

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005770f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   614402047   307200992+  83  Linux
/dev/sdb2       614402048   976773119   181185536   83  Linux
j-media-centre@jmediacentre-A880G:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            957563524 614726296 294195744  68% /
udev                   1922972         4   1922968   1% /dev
tmpfs                   773148       956    772192   1% /run
none                      5120         0      5120   0% /run/lock
none                   1932868       132   1932736   1% /run/shm
/home/j-media-centre/.Private
                     957563524 614726296 294195744  68% /home/j-media-centre
/dev/sdb1            302380448 269418472  17601928  94% /media/New Volume
/dev/sdb2            178341368    191876 169090216   1% /media/83ca1808-0f82-4051-81ff-3ee4b2c83c7d
j-media-centre@jmediacentre-A880G:~$ cat /etc/fstab
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=8b930be0-6555-4cef-8233-144fc323655f /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptswap1 none swap sw 0 0
j-media-centre@jmediacentre-A880G:~$ 

```

I have a 500Gb USB drive, which I have now split into partitions.
I am going to try copying t an ext4 partition to see if it makes a difference as all the others are FAT but it has worked in the past so I am not sure it is that. Also, that doesn;t explain the fact that I can't tarball one of the VMs.
The internal HDD is 1TB.

---

### Post by sudodus on 2012-07-04
Just a thought: You have an encrypted home folder. Did you try to copy from it logged in as another user (for example superuser)? Could that cause your problems?

---

