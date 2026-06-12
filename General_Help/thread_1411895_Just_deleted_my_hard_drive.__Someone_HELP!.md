---
title: "Just deleted my hard drive.  Someone HELP!"
date: 2010-02-20
forum: General Help
---

### Post by myk02k on 2010-02-20
Hey guys.  Long story short, I was trying to mount an iso but was unable to because it was a raw CD.  Someone on the forums posted to use a command "dd" and set it at /dev/sdb1.  I know, it should've been set to a USB stick or clear partition, but the post was unspecific on and I inadvertently wiped my whole hard drive clean.

If there is SOMEBODY out there that can tell me how to recover everything before the DD, at the very least recover my files, please contact me.  My AIM screen name is "myk02k" if you can IM me over posting here, but any advice will be appreciated.

Thanks!

---

### Post by GSF1200S on 2010-02-20
> **myk02k said:**
> Hey guys.  Long story short, I was trying to mount an iso but was unable to because it was a raw CD.  Someone on the forums posted to use a command "dd" and set it at /dev/sdb1.  I know, it should've been set to a USB stick or clear partition, but the post was unspecific on and I inadvertently wiped my whole hard drive clean.

If there is SOMEBODY out there that can tell me how to recover everything before the DD, at the very least recover my files, please contact me.  My AIM screen name is "myk02k" if you can IM me over posting here, but any advice will be appreciated.

Thanks!

Oh man.. dude- short of using special recovery software, I dont think youre gonna have much luck. Dangit.. Are you sure the whole partition/hard drive is deleted? How do you know? Im not trying to doubt you, but thats a terrible thing to be wrong about.

---

### Post by spiky001 on 2010-02-20
Hi you could try testdisk  [http://www.google.co.uk/#hl=en&source=hp&q=testdisk&btnG=Google+Search&meta=&aq=f&oq=testdisk&fp=4e2b16d837d0816d](http://www.google.co.uk/#hl=en&source=hp&q=testdisk&btnG=Google+Search&meta=&aq=f&oq=testdisk&fp=4e2b16d837d0816d)

it has been a topic in these forums quite abit

---

### Post by myk02k on 2010-02-20
> **GSF1200S said:**
> Oh man.. dude- short of using special recovery software, I dont think youre gonna have much luck. Dangit.. Are you sure the whole partition/hard drive is deleted? How do you know? Im not trying to doubt you, but thats a terrible thing to be wrong about.

The hard drive was the only thing containing 5 years of college work, years of pictures, movies, music, etc.

As for the partition, when I try to mount it while running my live CD, I get this error, "Cannot mount volume.  mount: wrong fs type, bad option, bad superblock on /dev/sda1...."

---

### Post by GSF1200S on 2010-02-20
> **myk02k said:**
> The hard drive was the only thing containing 5 years of college work, years of pictures, movies, music, etc.

As for the partition, when I try to mount it while running my live CD, I get this error, "Cannot mount volume.  mount: wrong fs type, bad option, bad superblock on /dev/sda1...."

Have you tried using fsck on /dev/sda1? Maybe the filesystem is still recoverable.

Man, if testdisk doesnt work for you, I would say its worth taking it into a store and forking out the dough. Not to be a jerk, but maybe for future peace of mind you could grab a second harddrive? If its a desktop, you could put the drive in the case and setup rsync to make auto backups of your stuff via cron or whenever you want to run it. I have rsync backing up every 30 minutes- since rsync is an incremental backup, its pretty good on system resources and doesnt take long to backup small changes.

But, I realize you are trying to get this fixed, so good luck.. Sorry I cant help more..

---

### Post by JSeymour on 2010-02-20
> **myk02k said:**
> Hey guys.  Long story short, I was trying to mount an iso but was unable to because it was a raw CD.  Someone on the forums posted to use a command "dd" and set it at /dev/sdb1.
What was the exact dd command and was sdb1 your only partition?

Reason I ask: If sdb1 was your only partition, and dd was given enough input data, the entire partition's been over-written by the data fed to dd, and the only people with the technology to get it back are very, very expensive people.

If your data is on another partition, it might be easiest to boot from a live CD, mount the partition(s) your data is on, copy it off to a USB drive, reinstall from scratch and restore your data.

Jim

---

### Post by myk02k on 2010-02-20
> **GSF1200S said:**
> Have you tried using fsck on /dev/sda1? Maybe the filesystem is still recoverable.

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
fsck: fsck.udf: not found
fsck: Error 2 while executing fsck.udf for /dev/sda1

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

> **GSF1200S said:**
> Man, if testdisk doesnt work for you, I would say its worth taking it into a store and forking out the dough. Not to be a jerk, but maybe for future peace of mind you could grab a second harddrive? If its a desktop, you could put the drive in the case and setup rsync to make auto backups of your stuff via cron or whenever you want to run it. I have rsync backing up every 30 minutes- since rsync is an incremental backup, its pretty good on system resources and doesnt take long to backup small changes.

I just got a USB stick to see if I can get a live USB setup and use that for downloading testdisk.  Their website says nothing about recovering ext4 filesystems.  If I can't recover it, I'll consider bringing the drive to a store (Best Buy?).  

It's a laptop, but after this, I'd take serious consideration in regularly backing things up.  The sad part is that my Seagate external hard drive died and I'm waiting on a warantee replacement.  Prior to it dying, I had a recent backup of my home folder when I did a fresh install in Karmic.

> **JSeymour said:**
> What was the exact dd command and was sdb1 your only partition?

Reason I ask: If sdb1 was your only partition, and dd was given enough input data, the entire partition's been over-written by the data fed to dd, and the only people with the technology to get it back are very, very expensive people.

If your data is on another partition, it might be easiest to boot from a live CD, mount the partition(s) your data is on, copy it off to a USB drive, reinstall from scratch and restore your data.

Jim

I don't know what the specific command was for dd, but I'll do some Googling to see if I can find it.  It was to take a raw CD iso image and dd it to a USB stick.

---

### Post by JSeymour on 2010-02-20
> **myk02k said:**
> ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

... you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>This is from a live CD, I guess?  Did you try the alternate superblock, as suggested?

> **myk02k said:**
> If I can't recover it, I'll consider bringing the drive to a store (Best Buy?).  Somehow I doubt the Geek Squad is going to know how to deal with ext4 ;)

> **myk02k said:**
> I don't know what the specific command was for dd, but I'll do some Googling to see if I can find it.  It was to take a raw CD iso image and dd it to a USB stick.Was it something like "dd if=something.iso of=/dev/sda1"?  Was it a full .iso (as in 600MB+)?  Did dd run very long?

Here's the deal: "dd" stands for "device duplicate."  It takes whatever it's given for input and writes it to whatever it's given for output.  So if you give something like the command I noted above, and the input is, say, 600MB, dd is going to write that 600MB to the first 600MB of the target, pure and simple.  Anything that was in that 1st 600MB on the target will be overwritten and unrecoverable.  (Well, I imagine the NSA and certain very expensive recovery companies could get it back.  Maybe.  With sufficient incentive.)

dd is a no foolin' around command.

I suppose that if your data was in later blocks on the disk it might be recoverable.  I have no idea how, tho.  It's been a long, long time since I've tried to deal with this kind of thing--and when I last did it, disks were much, much smaller.

You might find this enlightening: [Understanding Unix/Linux File Systems]("http://www.cyberciti.biz/tips/understanding-unixlinux-file-system-part-i.html").  It's not the best-written thing in the world, but it'll give you an idea.  Here's another one: [Linux File Systems - Overview]("http://www.diskdatarecovery.net/linux-file-system")

Good luck!

Jim

---

### Post by The Real Dave on 2010-02-20
Ouch, learning the lesson the hardway. :( Testdisk is what you need I'd say. And yes, the latest version supports ext4 as far as I know. Try downloading the PartedMagic live disk, it includes a few useful tools like Testdisk, and another for photo recovery

---

### Post by myk02k on 2010-02-20
Sooo what should I click for ext4??

```
TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - ATA TOSHIBA MK5055GS

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.

```

---

### Post by myk02k on 2010-02-20
> **JSeymour said:**
> This is from a live CD, I guess?  Did you try the alternate superblock, as suggested?

Yea, from a live CD.  I'm running e2fsck and although it is registering errors for fix, would it be as effective as testdisk?

```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'var' in / (2) references inode 8193 in group 1 where _INODE_UNINIT is set.
Fix<y>? 
```


> Was it something like "dd if=something.iso of=/dev/sda1"?  Was it a full .iso (as in 600MB+)?  Did dd run very long?


Thanks for the advise.  That line of code looks like that was it.  It was a 4.5ish GB .iso.  My hard drive is 500GB (350ish full)

---

### Post by myk02k on 2010-02-20
```
 Entry 'data' in /???/???/cups (253961) has deleted/unused inode 942091.  Clear<y>? yes

Entry 'doc-root' in /???/???/cups (253961) references inode 950282 found in group 116's unused inodes area.
Fix<y>? yes

Entry 'doc-root' in /???/???/cups (253961) has deleted/unused inode 950282.  Clear<y>? yes

Entry 'drv' in /???/???/cups (253961) has deleted/unused inode 950283.  Clear<y>? yes

Entry 'fonts' in /???/???/cups (253961) references inode 958474 found in group 117's unused inodes area.
Fix<y->? yes

Entry 'fonts' in /???/???/cups (253961) has deleted/unused inode 958474.  Clear<y>? yes

Entry 'locale' in /???/???/cups (253961) has deleted/unused inode 958475.  Clear<y>? yes

Entry 'mime' in /???/???/cups (253961) references inode 966666 found in group 118's unused inodes area.
Fix<y>? yes

Entry 'mime' in /???/???/cups (253961) has deleted/unused inode 966666.  Clear<y>? yes

Entry 'ppdc' in /???/???/cups (253961) has deleted/unused inode 966667.  Clear<y>? yes

Entry 'profiles' in /???/???/cups (253961) references inode 974858 found in group 119's unused inodes area.
Fix<y>? yes

Entry 'profiles' in /???/???/cups (253961) has deleted/unused inode 974858.  Clear<y>? yes

Entry 'templates' in /???/???/cups (253961) has deleted/unused inode 974859.  Clear<y>? yes

Entry 'calibrate.ppm' in /???/???/cups (253961) has deleted/unused inode 133204.  Clear<y>? yes

Entry 'antspotlight.desktop' in .../screensavers (196618) has deleted/unused inode 132480.  Clear<y>? yes

Entry 'cosmos-slideshow.desktop' in .../screensavers (196618) has deleted/unused inode 133405.  Clear<y>? yes

Entry 'f-spot-screensaver.desktop' in .../screensavers (196618) has deleted/unused inode 138102.  Clear<y>? yes

Entry 'fiberlamp.desktop' in .../screensavers (196618) has deleted/unused inode 132483.  Clear<y>? yes

Entry 'footlogo-floaters.desktop' in .../screensavers (196618) has deleted/unused inode 133424.  Clear<y>? yes

Entry 'fuzzyflakes.desktop' in .../screensavers (196618) has deleted/unused inode 132485.  Clear<y>? yes

Entry 'glblur.desktop' in .../screensavers (196618) has deleted/unused inode 132486.  Clear<y>? yes

Entry 'glcells.desktop' in .../screensavers (196618) has deleted/unused inode 132487.  Clear<y>? yes

Entry 'glmatrix.desktop' in .../screensavers (196618) has deleted/unused inode 132488.  Clear<y>? yes

Entry 'glschool.desktop' in .../screensavers (196618) has deleted/unused inode 132489.  Clear<y>? yes

Entry 'glslideshow.desktop' in .../screensavers (196618) has deleted/unused inode 132490.  Clear<y>? yes

Entry 'gltext.desktop' in .../screensavers (196618) has deleted/unused inode 132491.  Clear<y>? yes

Entry 'hypertorus.desktop' in .../screensavers (196618) has deleted/unused inode 132492.  Clear<y>? yes

Entry 'personal-slideshow.desktop' in .../screensavers (196618) has deleted/unused inode 133433.  Clear<y>? yes

Entry 'ubuntu_theme.desktop' in .../screensavers (196618) has deleted/unused inode 132494.  Clear<y>? yes

Entry 'electricsheep.desktop' in .../screensavers (196618) has deleted/unused inode 137117.  Clear<y>? yes

Entry 'automatix.py' in .../general-hooks (204810) has deleted/unused inode 137107.  Clear<y>? yes

Entry 'automatix.pyc' in .../general-hooks (204810) has deleted/unused inode 131424.  Clear<y>? yes

Entry 'checkbox.py' in .../general-hooks (204810) has deleted/unused inode 132602.  Clear<y>? yes

Entry 'generic.pyc' in .../general-hooks (204810) has deleted/unused inode 132111.  Clear<y>? yes

Entry 'generic.py' in .../general-hooks (204810) has deleted/unused inode 137096.  Clear<y>? yes

Entry 'ubuntu.pyc' in .../general-hooks (204810) has deleted/unused inode 136380.  Clear<y>? yes

Entry 'parse_segv.py' in .../general-hooks (204810) has deleted/unused inode 137093.  Clear<y>? yes

Entry 'parse_segv.pyc' in .../general-hooks (204810) has deleted/unused inode 132254.  Clear<y>? yes

Entry 'ubuntu.py' in .../general-hooks (204810) has deleted/unused inode 137094.  Clear<y>? yes

Entry 'checkbox.pyc' in .../general-hooks (204810) has deleted/unused inode 137203.  Clear<y>? yes

Entry 'medibuntu.py' in .../general-hooks (204810) has deleted/unused inode 133868.  Clear<y>? yes


```

You get the picture.

---

### Post by JSeymour on 2010-02-20
> **myk02k said:**
> You get the picture.Yeah.  You're probably not going to end up with a bootable/usable system.  But you *might*, end up with something that's mountable and readable, from which you can recover your data.

Personally, I'm surprised you're getting as far as you are.

Jim

---

### Post by myk02k on 2010-02-20
Well, good news & bad news.

Good news: the filesystem is now mountable.
Bad news:  this is its directory

```
ubuntu@ubuntu:/media/2ff8c953-ed18-4dc6-aab9-58330cbcd4f2$ ls
cdrom  initrd.img  initrd.img.old  lib64  lost+found  vmlinuz  vmlinuz.old
```
and this 

```
ubuntu@ubuntu:/media/2ff8c953-ed18-4dc6-aab9-58330cbcd4f2$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
/dev/sda1: clean, 271000/29786112 files, 83556643/119123975 blocks
```

Is there anything I can do to recover what's not on the filesystem contents?  Testdisk?  chk

---

### Post by The Real Dave on 2010-02-20
For testdisk, you want an Intel partition. However, accessing that partition, all those filesystem checks, might well have overwritten whatever data was left in the sectors. Still, you may be able to recover some of it.

---

### Post by JSeymour on 2010-02-20
> **myk02k said:**
> Is there anything I can do to recover what's not on the filesystem contents?  Testdisk?  chkAny particular file will be spread-out across several blocks on the disk.  It is directory and inode information that tells the OS where those blocks are for each file.  The problem is that all the directory and inode information has been overwritten, so there's nothing to point to the files and directories anymore.  All your data is still out there, most likely, but the pointers to it are all gone.  

Research it--I certainly wouldn't give up yet, but I suspect you're done :(.

Btw: Is there anything in lost+found?

Jim

---

### Post by JSeymour on 2010-02-20
> **The Real Dave said:**
> For testdisk, you want an Intel partition. However, accessing that partition, all those filesystem checks, might well have overwritten whatever data was left in the sectors. Still, you may be able to recover some of it.No.  All fsck does is fixup directory and inode inconsistencies.

Jim

---

### Post by myk02k on 2010-02-20
> **JSeymour said:**
> Any particular file will be spread-out across several blocks on the disk.  It is directory and inode information that tells the OS where those blocks are for each file.  The problem is that all the directory and inode information has been overwritten, so there's nothing to point to the files and directories anymore.  All your data is still out there, most likely, but the pointers to it are all gone.  

Research it--I certainly wouldn't give up yet, but I suspect you're done :(.

Btw: Is there anything in lost+found?

Jim

Who said I'm done?  I'm not giving up until maybe Sunday night.  There are numerous files in lost+found, but it is by far too short to be everything I'm looking for.

---

### Post by JSeymour on 2010-02-20
> **myk02k said:**
> Who said I'm done?  I'm not giving up until maybe Sunday night.That's the spirit! :)

> **myk02k said:**
> There are numerous files in lost+found, but it is by far too short to be everything I'm looking for.They're all numbers, right?  Those'll be inode numbers for inodes that pointed somewhere, but for which there appeared to be no allocations.  Some of those, perhaps many of them, may point to some of your data files.

I have recovered files from inode data in lost+found, but it's been a long, long time since I've done that.

Here's a good explanation of Unix inodes: [Inode pointer structure]("http://en.wikipedia.org/wiki/Inode_pointer_structure").

Jim

---

### Post by theozzlives on 2010-02-20
Well I haven't read the whole thread but all I can say is BACKUP OFTEN. I leaned the hard way, as you are now, back in 1992. BACKUP YOUR DATA something will go wrong!

---

### Post by myk02k on 2010-02-21
> **JSeymour said:**
> That's the spirit! :)

They're all numbers, right?  Those'll be inode numbers for inodes that pointed somewhere, but for which there appeared to be no allocations.  Some of those, perhaps many of them, may point to some of your data files.

I have recovered files from inode data in lost+found, but it's been a long, long time since I've done that.

Here's a good explanation of Unix inodes: [Inode pointer structure]("http://en.wikipedia.org/wiki/Inode_pointer_structure").

Jim

Yup, the files are all numbers in the lost+found folder.  Any further advice?

If this helps, GParted sees the hard drive as "unallocated", yet the drive is mounted and I can see a few files.

I just bought a new USB flash drive so that I can rely upon something other than the hard drive for school until I get my files back.  After its formatted, I'll try testdisk again and another utility called extundelete, which came up after a few Google searches.

Thanks for the help!
-Mike

---

### Post by GSF1200S on 2010-02-21
> **myk02k said:**
> Yup, the files are all numbers in the lost+found folder.  Any further advice?

If this helps, GParted sees the hard drive as "unallocated", yet the drive is mounted and I can see a few files.

I just bought a new USB flash drive so that I can rely upon something other than the hard drive for school until I get my files back.  After its formatted, I'll try testdisk again and another utility called extundelete, which came up after a few Google searches.

Thanks for the help!
-Mike

Any issue Ive had with filesystems has been fixed by fsck, so I apologize for not being able to help you more. Depending on how many files you have and their size and assuming you have another computer that you can put the files on (like a desktop or another laptop), you could setup an FTP server (assuming too that you dont have an enclosure for the drive) on the other machine and transfer the numbered folders and files to that machine utilizing a liveCD. If you dont have another computer, perhaps a friend would be willing to help?

Thats prolly not what you were looking for as help- I understand you mean to recover the filenames, etc. But as another poster on here said, if dd overwrote the journal, I dont think youd be able to get all that information back without taking it in and having some really expensive software scan the drive. Even then you might not get the fileinfo. You might have to go through them one by one- man I hope if thats the case there isnt too many files. At least you HAVE the files.

Good luck man.. it sucks and I wish I could do more to help you. Maybe someone else or a former poster will come up with a far better solution.

---

### Post by J V on 2010-02-21
> **myk02k said:**
> Hey guys.  Long story short, I was trying to mount an iso but was unable to because it was a raw CD.  Someone on the forums posted to use a command "dd" and set it at /dev/sdb1.  I know, it should've been set to a USB stick or clear partition, but the post was unspecific on and I inadvertently wiped my whole hard drive clean.

If there is SOMEBODY out there that can tell me how to recover everything before the DD, at the very least recover my files, please contact me.  My AIM screen name is "myk02k" if you can IM me over posting here, but any advice will be appreciated.

Thanks!dd requires an if, so there shoulden't be any way to recover the data sorry... mounting an iso doesn't require dd, methinks you should hunt him down and kill (report post) him for malicious commands?

---

### Post by northrup on 2010-02-21
If only the first 600 MB were overwritten, then the remaining however many GBs should still exist.  If you can find, say, a hex editor that allows you to view the data on a hard drive, there's the possibility of having that extra step in retrieving the raw data.  Then, if you can somehow split up that raw data into files, you're golden.

Hope this helps.  I know how you feel.  I've accidentally erased drives before with Linux (i.e. trying to install Damn Small Linux on a desktop from a USB drive and, instead of specifying the hard drive, specifying the USB drive and reformatting it).  I wish you the best of luck :)

---

### Post by jenaniston on 2010-02-21
> **JSeymour said:**
> . . .  The problem is that all the directory and inode information has been overwritten, so there's nothing to point to the files and directories anymore. 
 All your data is still out there, most likely, but the pointers to it are all gone.  
. . .


I have read all this and this sounds  right - and I also agree don't give up totally just yet.

to check if data exists there, try running hexdump on the partition . . .  the  output dumped to the screen (use ctrl-c to stop of course) can show that data IS in fact there. 

But even then  . . . "there's nothing to point to the files and directories anymore. All your data is still out there, most likely, but the pointers to it are all gone."

```
hexdump -C /dev/sda1
```

---

### Post by myk02k on 2010-02-21
After browsing through lost+found with Nautilus, I realized that there are many, MANY files in this folder than I thought.  Each folder (designated with an inode #?) has multiple files stored within.  If this is everything, it could be a long, long time before I can sort everything from my home folder back in order.  Nevertheless, it seems like more files than I expected was found by e2fsck.

The issue at hand now is that Nautilus keeps freezing up when trying to display the contents of this folder.

> **jenaniston said:**
> I have read all this and this sounds  right - and I also agree don't give up totally just yet.

to check if data exists there, try running hexdump on the partition . . .  the  output dumped to the screen (use ctrl-c to stop of course) can show that data IS in fact there. 

But even then  . . . "there's nothing to point to the files and directories anymore. All your data is still out there, most likely, but the pointers to it are all gone."

```
hexdump -C /dev/sda1
```

I honestly have no idea how to read the hexdump output.  I'll have to educate myself a little bit before I can figure what all those numbers mean.  I've never taken a computer course in my entire life (believe it or not).

---

### Post by jenaniston on 2010-02-21
> **myk02k said:**
> . . . I realized that there are many, MANY files in this folder than I thought.  Each folder (designated with an inode #?) has multiple files stored within. 
. . .
The issue at hand now is that Nautilus keeps freezing up when trying to display the contents of this folder.

I honestly have no idea how to read the hexdump output.  I'll have to educate myself a little bit before I can figure what all those numbers mean.  I've never taken a computer course in my entire life (believe it or not).

Ohh no, no desire to *read *the hexdump output . . .
 I only suggested to run hexdump to show that there is in fact data there - a trick from the linuxquestions forum . . .

you did NOT get all 0 's - that is ***all ***it was to reveal . . . 

and you also found the files in lost+found . . . so good -
must be that the "pointers" are there too ?  (a single file can have it's data  in all sorts of different locations)

---

### Post by myk02k on 2010-02-21
OK I just ran an interesting program called extundelete.  I used the "--restore-all" option.

```


--restore-inode ino[,ino,...]

Restore the file(s) with known inode number 'ino'.  The restored files are created in ./RESTORED_FILES with their inode number as extension (ie, inode.12345).

--restore-file 'path'  Will restore file 'path'. 'path' is relative to root of the partition and does not start with a '/' (it must be one of the paths returned by --dump-names).  The restored file is created in the current directory as 'RECOVERED_FILES/path'.

--restore-files 'path' Will restore files which are listed in the file 'path'.  Each filename should be in the same format as an option to --restore-file, and there should be one per line.

--restore-all Attempts to restore everything.

```

extundelete also can show the contents of the journal, Show process entries "on or before/after 'dtime'", show info on inode, show info on block, etc.

Here's what some of the output looked like, if it's of any use...

```
Restored inode 395627 to file RECOVERED_FILES/lost+found/#483390/E33FD061d01
Restored inode 395666 to file RECOVERED_FILES/lost+found/#483390/BB638EB1d01
Restored inode 395683 to file RECOVERED_FILES/lost+found/#483390/F4050140d01
Restored inode 395706 to file RECOVERED_FILES/lost+found/#483390/6E25EEE0d01
Failed to restore inode 581694 to file RECOVERED_FILES/lost+found/#581693/2007 - Live The Light It Up Tour:Inode does not correspond to a regular file.

```

I'm still having a rough time looking at the LOST+FOUND folder with Nautilus, as it keeps locking up.  Should I move these files around to different folders so that I can sort through them?

By using Properties in Nautilus, the contents indicate 273,222 items totalling 319.7 GB, which sounds equal to the amount of data I had before I destroyed everything.  Is there any easier way of sorting out LOST+FOUND rather than doing it by hand?

---

### Post by JSeymour on 2010-02-21
> **myk02k said:**
> Should I move these files around to different folders so that I can sort through them?**NO!**  Absolutely not!  You _must not_ write to that drive _**at all**_!

As I tried to explain earlier: All those inode numbers are in lost+found because fsck thought they were inodes for stuff that didn't exist anymore.  This is because you wiped-out a goodly portion of Linux' file structure with that dd command you executed.  Now Linux thinks that the blocks all those "lost" inodes point to are free.  Any writing to that disk may over-write valid, but "lost" data on it.

You **should** be mounting that corrupted filesystem read-only from this point on.

> **myk02k said:**
> By using Properties in Nautilus, the contents indicate 273,222 items ...Yeah, well, Nautilus probably wasn't designed with the idea of cataloging 273,222 directory items in one go.

> **myk02k said:**
> Is there any easier way of sorting out LOST+FOUND rather than doing it by hand?I'm not sure what you would suggest.  How could any utility possibly divine what those inodes point to?

I'm wondering: Those URLs I pointed to earlier: Did you read them?  You need to, so you'll understand just what you're dealing with.

Here's another that *might* be of use to you.  I found it by just entering "restore file from inode number lost+found": [HOWTO recover deleted files on an ext3 filesystem]("http://www.xs4all.nl/%7Ecarlo17/howto/undelete_ext3.html")

I suggest you slow down and do some research and learning before you lose the one possible chance you have to recover your data.

Jim

---

### Post by myk02k on 2010-02-22
I appreciate the advice, especially because this is all unfamiliar territory for me.  Unfortunately, before you mentioned to mount the disk as ro, it will no longer mount after I ran extundelete.  I've tried to repair it using 'e2fsck -y /dev/sda1', but it continually hangs when attempting to fix multiply-claimed blocks.

I should've simply found and backed up my lecture notes when I had the chance.  :(  So now I'm back on square one.  If I can't get the disk to mount again by tonight, I'm afraid I'll have to cut my losses.  Although I found someone an hour away that can store an image of my disk for me, there's no point if I can't even mount the filesystem anymore.

This is what I get when trying to mount:

```
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg | tail

```
[ 6291.045095] EXT4-fs (sda1): ext4_check_descriptors: Checksum for group 1 failed (61452!=60400)
[ 6291.045110] EXT4-fs (sda1): group descriptors corrupted!

```

EDIT:

Right now, I'm using an alternate superblock (the last one on my partition) and things are looking promising thus far.

---

### Post by myk02k on 2010-02-22
OK, I'm finished with trying to fix this corrupt filesystem.  For whatever reason, e2fsck and fsck hangs when attempting to clone multiple-used blocks.  What I'm going to do is dd this hard drive over to my friends external hard drive to see if it can finish the filesystem scan on a larger partition.  Maybe it's getting stuck because the disk is full?

Either way, you guys have been a great help.  At the very least, I can recover my lecture notes using photorec.  After I have all of my document files recovered, I'll simply search through its contents to determine if they are current class notes.

I guess there's a greater lesson learned here, and that's ALWAYS back your stuff up.  I got too overconfident when I switched over to Linux, thinking that nothing malicious will ever destroy my data.

Lesson learned.  Thanks again for the tremendous support.

---

### Post by JSeymour on 2010-02-22
> **myk02k said:**
> I appreciate the advice, especially because this is all unfamiliar territory for me.  Unfortunately, before you mentioned to mount the disk as ro, it will no longer mount after I ran extundelete.Gah! :( I should've told you that right after you told us about all those entries in lost+found.  I suppose it was too obvious to me, so I didn't think of it in time.  I apologize.

Jim

---

### Post by justanotherjoe on 2010-02-22
im in the same boat(but worse) I installed ubuntu 9.10 on to a drive that was a storage drive and just used the "use entire disk" option when setting up the partitions. It was a tb drive and now it says theres around 16 gigs used and 982 free. Its prolly all gone right

---

### Post by myk02k on 2010-02-22
> **JSeymour said:**
> Gah! :( I should've told you that right after you told us about all those entries in lost+found.  I suppose it was too obvious to me, so I didn't think of it in time.  I apologize.

Jim

I'm still confused over what went wrong.  e2fsck comes up with 2800 conflicts on multiple-claimed blocks and just locks up somewhere through cloning the blocks.  I have no idea why this wasn't the case after the first e2fsck scan that enabled me to search through LOST+FOUND.

I'm running photorec right now to recover all Office documents.  Crossing my fingers, because I have an exam in "Corporation, Bankruptcy, & Takeover" at RU the following Monday.

---

### Post by JSeymour on 2010-02-23
> **justanotherjoe said:**
> im in the same boat(but worse) I installed ubuntu 9.10 on to a drive that was a storage drive and just used the "use entire disk" option when setting up the partitions. It was a tb drive and now it says theres around 16 gigs used and 982 free. Its prolly all gone right
Yes and no.  Unless you did a low-level format: It's probably still out there.  Or most of it.  But, as with the OP, there's no longer anything pointing to it, so finding the pieces and putting them back together again would be a heck of an exercise.

Jim

---

### Post by JSeymour on 2010-02-23
> **myk02k said:**
> I'm still confused over what went wrong. 
Hard to say.  I don't know exactly how extundelete goes about doing what it does, but, since it has to operate on an unmounted filesystem, I can take some guesses.  I don't think it was designed for quite the use you put it to.  Deleting a object or two or a few on a filesystem is one thing.  Mangling a system's file structure like you did is quite another.  I'm guessing extundelete did what it thought was right, and managled what fsck was able to more-or-less salvage.

Jim

---

### Post by myk02k on 2010-02-26
UPDATE.  I dd'ed the hard drive over to a new one so that I can use my laptop as normal.  I don't know how, but the drive is mountable & the LOST+FOUND folder is back after running e2fsck yet again.  Now the question is, where do I go from here?

---

### Post by PhoHammer on 2010-02-26
> **myk02k said:**
>  At the very least, I can recover my lecture notes using photorec.  After I have all of my document files recovered, I'll simply search through its contents to determine if they are current class notes.

I guess there's a greater lesson learned here, and that's ALWAYS back your stuff up.  I got too overconfident when I switched over to Linux, thinking that nothing malicious will ever destroy my data.

Lesson learned.  Thanks again for the tremendous support.

Speaking of lecture notes and backing up your data in the future, 
I use [dropbox]("http://www.dropbox.com"). For small files (2 GB for free with dropbox), it's
 a perfect backup. And since I have multiple machines, my 
important class lecture notes end up on 6 partitions on 2 
machines and an external HDD, not to mention dropbox's cloud 
storage. 

Since class notes/homework are not too security sensitive, this 
is a great backup solution.

My house could burn down and my backpack could be destroyed and I
 would still have my notes :).

I know it doesn't help what you have lost, but just my two cents for future considerations...

---

### Post by egalvan on 2010-02-26
What you are attempting to do is more properly called "data carving".
You are no longer trying (or able) to recover files by their name or inode data,
you are trying to recover files based on their structure, or what "type" of file they are...
document, text, OO, jpeg, png, etc, etc,

Data carving software reads the headers (and more) and tries to determine the "type".


here are some links to carving/recovery oriented distros...
try one, try them all...
also try "data carving" under google


[http://ubuntu-rescue-remix.org/node/195](http://ubuntu-rescue-remix.org/node/195)

[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

[http://www.deftlinux.net/](http://www.deftlinux.net/)


good luck, perseverance plays a BIG role in this endeavor.
"there is no try. do, or do not"

---

### Post by PhoHammer on 2010-02-26
> **egalvan said:**
> 
"there is no try. do, or do not"

"Only a Sith deals in absolutes..."
[IMG]http://i153.photobucket.com/albums/s224/Tycho911/Smilies/thLightsaberFightSmileys.gif[/IMG]

---

### Post by egalvan on 2010-02-27
> **PhoHammer said:**
> "Only a Sith deals in absolutes..."

An absolute admits of no option.
Therefore, an option is not an absolute.


"do" is an absolute
"do not" is an absolute
"do ***or*** do not" is an option, thus **NOT** an absolute.

---

### Post by myk02k on 2010-02-27
> **egalvan said:**
> What you are attempting to do is more properly called "data carving".
You are no longer trying (or able) to recover files by their name or inode data,
you are trying to recover files based on their structure, or what "type" of file they are...
document, text, OO, jpeg, png, etc, etc,

Data carving software reads the headers (and more) and tries to determine the "type".


here are some links to carving/recovery oriented distros...
try one, try them all...
also try "data carving" under google


[http://ubuntu-rescue-remix.org/node/195](http://ubuntu-rescue-remix.org/node/195)

[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

[http://www.deftlinux.net/](http://www.deftlinux.net/)


good luck, perseverance plays a BIG role in this endeavor.
"there is no try. do, or do not"

I was hoping that there was a way to recover file names, because organizing everything would be a very tedious job.  Photorec is able to recover the documents from what it looks like.  I can give a clearer answer once it completes its job.  I'm guessing there is no backup of the journal anywhere that would make this job much easier?

---

### Post by myk02k on 2010-02-27
Photorec seemed to do an adequate job recovering data, but many files are mislabeled and/or corrupt, especially video files.  Other files like *.txt are pdf's or odt's.  Not only do I have to re-sort all of the recovered files to folders by attribute and size, but I'll need a better way to judge what the true filetype is for many files.

Bear in mind, photorec recovered 85,000+ files  #-o

---

### Post by PhoHammer on 2010-02-28
> **egalvan said:**
> An absolute admits of no option.
Therefore, an option is not an absolute.


"do" is an absolute
"do not" is an absolute
"do ***or*** do not" is an option, thus **NOT** an absolute.

Only a Sith deals in absolute**S**.

"do" and "do not" are absolutes, with the option being choosing 
between the two. Just because you put black and white together as
 an "option" does not mean that they are not absolutes any 
longer.

It's sort of an oxymoron type statement, anyways, with the word 
"only" signifying an absolute itself... I was just joshing you! :P

---

### Post by myk02k on 2010-03-02
OK quick update.  Photorec didn't do such a good job recovering my documents in .odt, .pdf, or .doc format. 

What did work for recovering my lecture notes saved in .odt format, was a program called "scalpel".  It did a very exceptional job.  [This HOWTO]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1378119") is what I followed to successfully recover OpenOffice documents with scalpel.

---

### Post by myk02k on 2010-03-02
I want to write a quick how-to for anyone who needs to recover data on ext3/ext4 filesystems with basic steps for any beginner to work with.  I am basing this off of my own steps I needed to take with a notebook computer that had no immediate access to the hard drive, and the steps I took to transfer the data off my native disc to another, then experiment with various software for file recovery.

1- My first issue was that my computer failed to boot at GRUB, since the filesystem did not recognize any data on the disc.  This step may be skipped if you are recovering a hard disc that is not your primary partition.

To bypass this issue without reinstalling Ubuntu on the disc (since that would overwrite valuable data) was to boot the computer from a live CD.  Simply burn a copy of Ubuntu to a CD (with another computer) & run a live session by clicking on "Try Ubuntu without any change to your computer".

2- The second step was that I used e2fsck on the device so that the disc would mount properly.  This step should be skipped if the disc is mountable.

```
sudo e2fsck [device]
```

DO NOT let it repair any inode corruption, as that may overwrite data on the disc.

3- Third, once the disc was mountable, I remounted the device as read-only.

```
sudo mount -o remount, ro [device]
```

4- Next step was that I needed to reinstall Ubuntu on the native hard drive without losing any files.  Because I am working on a notebook computer that does not give immediate access to the drive bay, rather than replacing the hard drive with a new one, I made an image of the device to a new hard-drive.  This step may be skipped if you will not need to re-use the corrupt disc for your current install.  If you have an external hard-drive with sufficient space, you may create a partition on the external drive for this step.  What I personally did to save on money was I bought a desktop hard-drive that matched the size of my notebook drive and purchased a SATA to USB adapter on Ebay for a few dollars.  This cheap little adapter has came to valuable use many, MANY times.

Now that you have a space to store the data from the damaged filesystem, you may make an image of that disc with this command.  Be very careful, as it could overwrite and damage filesystems if used improperly.  I highly recommend you read up on this from other sources so that you fully understand how dd works.

```
sudo dd if=[input device] of=[output device]
```

This may take a while.  For me, transferring 500 GB from my internal hard drive to external USB-connected hard drive took 28 hours to perform.  [This HOWTO]("http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html") will allow you to check the progress of the dd transfer to insure that everything is going well while you wait.

5- Repeat step 3 to mount the newly cloned image of your previous partition.  Now that you have a perfect copy of your previous partition, you may reinstall Ubuntu to your native hard-drive.  

6- Now that we have an operable computer with a fresh install and a cloned image of your previous disc, we may now move onto "data carving" to recover files from your damaged partition.  There are various data recovery software, which I tried and will give my 2 cents on.

extundelete - this program was unsuccessful in recovering data where no journal was found.  If you did not destroy your disc as badly as I did, maybe you'll have better luck with it than me.

photorec - this software is available in the repositories along with a partition recovery system called testdisk.  It may be installed by the following command:

```
sudo apt-get install testdisk
```

Although photorec did a good job recovering pictures, it did not recover my OpenOffice documents.

scalpel - also available in the repositories

```
sudo apt-get install scalpel
```

You will need to add configuration lines in order for it to discover OpenOffice documents.  Detailed information on this may be found [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1378119").

This program was highly successful in recovering OpenOffice documents, where photorec failed.  It seems to have capabilities with other filetypes, which I will look into very soon.

Cheers :guitar:

---

### Post by MSich on 2010-03-02
First of all, sorry this happened, I'm sure it was quite stressful.  
 
But, thank you for sticking with it and posting all of your findings.  This has been educational for me and a good example of the "think tank" at work.
 
Good luck!

---

### Post by anselm on 2010-03-02
Make this a sticky in the tips section

---

### Post by myk02k on 2010-03-02
> **anselm said:**
> Make this a sticky in the tips section

I'll probably post this in the tips section when I have enough information on the recovery software.  Photorec didn't find any pictures that was in my /home/$USER/Pictures folder.  The videos are all corrupt as well.

---

