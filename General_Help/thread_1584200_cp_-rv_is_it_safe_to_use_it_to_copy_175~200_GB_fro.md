---
title: "cp -rv: is it safe to use it to copy 175~200 GB from one external hdd 2 another ?"
date: 2010-09-28
forum: General Help
---

### Post by astrobob.tk on 2010-09-28
Hey there,

I have to 500Gb Transcend external HDD's. One of them seems to have a problem (turn on & off randomly if not working) due to my old laptop's usb problem. Anyways, my issue is that I need to copy my files (175 ~ 200 GB of music, vids, images, doc's, mag's & books ....) to my new Transcend hdd. I was trying to archive them as .tar.bz2  & then transfer them so as not to loose any files on the way. Apparently this turned out to be a pain to do & took too long & used my cpu in full & put the fan on full rotation during the copying.

I was wondering if I could do one command from the terminal & copy all my data from one disk to another. I think cp -rv would do it right ? Would there be any error or loss of data in the process ?

what is the safest method I could use ?

you help is appreciated.

thanks

---

### Post by coolman98 on 2010-09-28
probably not.

---

### Post by SeijiSensei on 2010-09-28
> **astrobob.tk said:**
> I was trying to archive them as .tar.bz2  & then transfer them so as not to loose any files on the way. Apparently this turned out to be a pain to do & took too long & used my cpu in full & put the fan on full rotation during the copying.

Well, that is rather what you'd expect to happen. Copying 200GB of data and compressing it with bzip2 is going to take a while and push your CPU.

We need a bit more information.  Is the target filesystem also a Linux-compatible filesystem like ext3/ext4/ReiserFS/etc. or is it formatted as NTFS?  If the latter, you won't be able to preserve the array of permissions and other data that are intrinsic to *nix filesystems.  You could create a compressed tarball and store that on the NTFS drive, but you won't be able to mirror a *nix directory structure to NTFS.

Here are a couple of options:

1) tar cjpf mybackup.tar.bz2 /path/to/source

Creates a bzip2-compressed tarball and stores it as mybackup.tar.bz2. Can be written to any type of filesystem since it's just a file.

2) cd /path/to/source; tar cpf - . | (cd /path/to/target; tar xvf -)

Creates a complete image of the files in /path/to/source in /path/to/target.

3) cd /path/to/source; rsync -av . /path/to/target

Like (2), but uses the [rsync]("http://rsync.samba.org/") program.  You might need to install rsync from the repositories.

Both (2) and (3) require that the target filesystem be Unix-compatible.

---

### Post by psusi on 2010-09-28
I usually use cp -a to preserve permissions and ownership, but yes, cp -rv will work as well.  Also using gzip instead of bzip2 to compress will use less cpu.

---

### Post by astrobob.tk on 2010-09-28
> **SeijiSensei said:**
> Well, that is rather what you'd expect to happen. Copying 200GB of data and compressing it with bzip2 is going to take a while and push your CPU.

We need a bit more information.  Is the target filesystem also a Linux-compatible filesystem like ext3/ext4/ReiserFS/etc. or is it formatted as NTFS?  If the latter, you won't be able to preserve the array of permissions and other data that are intrinsic to *nix filesystems.  You could create a compressed tarball and store that on the NTFS drive, but you won't be able to mirror a *nix directory structure to NTFS.

The external hard disks am using are as is. They are still as I bought them. So they are NTFS i suppose.

> Here are a couple of options:

1) tar cjpf mybackup.tar.bz2 /path/to/source

Creates a bzip2-compressed tarball and stores it as mybackup.tar.bz2. Can be written to any type of filesystem since it's just a file.

2) cd /path/to/source; tar cpf - . | (cd /path/to/target; tar xvf -)

Creates a complete image of the files in /path/to/source in /path/to/target.

3) cd /path/to/source; rsync -av . /path/to/target

Like (2), but uses the [rsync]("http://rsync.samba.org/") program.  You might need to install rsync from the repositories.

Both (2) and (3) require that the target filesystem be Unix-compatible.How does this differ from wht I did ? though I should not that when copying the .tar.bz2 files I often get error msg's that the files are too large. this often happens with files above 3 GB.

Regarding what you suggested, these files I am transferring are files i use on a daily basis, that is i very regularly access the files on the external hdd which is my main storage device. I dont store large data on my internal disc. So basically what I am looking for is a way to transfer these files to the new hdd, preferably as they are. In the case of what I was doing, I had to untar the files again to fold out all my files as they were.

I hope i am explaining my situation clearly, coz i feel I am not. maybe i need some sleep hehe

?? Why can't the command cp be safe ? & what is its file size limit ? Moreover why is the copy past on the desktop limited to 3~4 GB ?

---

### Post by CharlesA on 2010-09-28
It would be easier to use cp -a or rsync -a to preserve permissions and whatnot.

Personally I'd use rsync, but I'm a fan of it. ;)

If you compress them into a tarball, you won't be able to access them without extracting said tarball.

Note: rsync can work on NTFS partitions too.

---

### Post by astrobob.tk on 2010-09-28
> **psusi said:**
> I usually use cp -a to preserve permissions and ownership, but yes, cp -rv will work as well.  Also using gzip instead of bzip2 to compress will use less cpu.

The main concern besides the permissions & ownership is that how safe is it to do it this way without losing any files. Moreover, what if i lost files on the way, how can I check the integrity of the copy, noting that even if i use the option "verbose", it wold be impossible to check all details with thousands of files being copied.

P.S.: maybe i didnt mention it, but take it easy with me, as am not an advanced user, specially when it comes to the terminal, though I have been learning quite some lately. ;)

---

### Post by CharlesA on 2010-09-28
rsync checks each file and compares it to make sure it exists and is the same size/timestamp.

If you do use rsync, you can run it again after it finishes and see if it copies anything, if not, you are good to go.

I haven't "lost" any files when using rsync. :)

---

### Post by 3Miro on 2010-09-28
Why the concern with permissions, it seems that both disks are NTFS and even if they were extX the permissions would be the same on both anyway (you are not sharing those between different machines with different OS or whatever).

You should be able to just plug the two devices, open Nautilus, select all and then drag and drop into the second drive. It will take some time, but it shouldn't be a problem. I have done one time transfers of files like that (>100GB) over home lan NFS as well as 20-50GB internal HDD to external HDD. I never had anything lost (and if something goes wrong, nautilus should tell you).

---

### Post by psusi on 2010-09-28
Are you talking about a single file that is 3gb in size?  Or total?  IIRC, fat32 can not handle a single file over 2gb in size, so if the disk is using that, and you are talking about a single file, that would explain it.

---

### Post by CharlesA on 2010-09-28
> **3Miro said:**
> Why the concern with permissions, it seems that both disks are NTFS and even if they were extX the permissions would be the same on both anyway (you are not sharing those between different machines with different OS or whatever).

You should be able to just plug the two devices, open Nautilus, select all and then drag and drop into the second drive. It will take some time, but it shouldn't be a problem. I have done one time transfers of files like that (>100GB) over home lan NFS as well as 20-50GB internal HDD to external HDD. I never had anything lost (and if something goes wrong, nautilus should tell you).

+1 to that. I just prefer the command-line, I guess. :P

> **psusi said:**
> Are you talking about a single file that is 3gb in size?  Or total?  IIRC, fat32 can not handle a single file over 2gb in size, so if the disk is using that, and you are talking about a single file, that would explain it.

Both external drives are NTFS, so there won't be a problem with file size.

---

### Post by SeijiSensei on 2010-09-28
> **astrobob.tk said:**
> The external hard disks am using are as is. They are still as I bought them. So they are NTFS i suppose.

Then you're limited to writing tarballs.  You might consider reformatting them to ext4 if you don't intend to use them with Windows.

> How does this differ from wht I did ? though I should not that when copying the .tar.bz2 files I often get error msg's that the files are too large. this often happens with files above 3 GB.

Actually it sounds like the disks are formatted with FAT32, the older Microsoft DOS filesystem that was used through Win98.  It's pretty common for disks to come from the factory with FAT32 filesystems as they can be mounted on almost any OS from the past decade or so.  However FAT32 has severe limitations about the size of the files they can store.

So let's start from scratch.  Attach one of the drives to the Linux box but don't do anything when Ubuntu informs you that it's attached.  Now open a terminal and type "sudo dmesg".  You'll probably see an entry for "sdb" which will correspond to the external drive.  (If you have other drives besides the boot disk in your machine, the external drive will appear as "sdc", "sdd", etc., depending on the number of drives you have installed.)  Let's assume it appears as "sdb".  Now you can reformat the drive to be Linux-compatible by running "sudo fdisk /dev/sdb" from a Terminal. You'll see some text, then a command prompt.  Type "p" and you'll see a list of the partitions on the external drive.  It'll probably be identified as a FAT32 partition.  Type "d" then "1" (if necessary) to delete the partition.  Now type "n" to create a new partition, then "(p)rimary" and accept the default start and end blocks by hitting Enter.  fdisk will create a new partition that fills the disk and is marked for use by Linux.  Type "w" to write your changes to the drive, then "q" to quit.

You're halfway done now.  You have an empty, Linux-compatible partition, but it doesn't have a filesystem on it.  Now type "sudo mkfs -j /dev/sdb1" to make an ext4 filesystem in the single partition on sdb, sdb1.

Now you should be able to use something like rsync to create a mirror of the files on the Linux box that you want to back up.

---

### Post by CharlesA on 2010-09-28
> **SeijiSensei said:**
> Then you're limited to writing tarballs.  You might consider reformatting them to ext4 if you don't intend to use them with Windows.

You can write files to NTFS (and FAT32) just fine from Ubuntu.

It would be easier to see what file system the drive was formatted as by running this command in a terminal after attaching the drive:

```
sudo fdisk -l
```

---

### Post by SeijiSensei on 2010-09-28
> **CharlesA said:**
> You can write files to NTFS (and FAT32) just fine from Ubuntu.

With all UIDs, GIDs, permissions, symlinks, etc., preserved?  FAT32 has no concept of permissions or symlinks, and NTFS last I heard isn't compatible with *nix filesystem concepts either.  

Sure he can write a tarball onto an NTFS filesystem, but can he do:

rsync -av /path/to/source /path/to/NTFS/target

then mount the target and have it look to Linux just like the source?  I'd like to believe you're right, but I have to admit to being dubious.

---

### Post by CharlesA on 2010-09-28
It won't preserve the permissions and whatnot, but if they are copying NTFS to NTFS, that shouldn't be a problem.

---

### Post by SeijiSensei on 2010-09-28
I guess I missed that he was copying from NTFS to NTFS.  I thought the source filesystem was *nix.   Sorry if I added unnecessary confusion to this discussion.  I'll go away now ....

---

### Post by CharlesA on 2010-09-28
> **SeijiSensei said:**
> I guess I missed that he was copying from NTFS to NTFS.  I thought the source filesystem was *nix.   Sorry if I added unnecessary confusion to this discussion.  I'll go away now ....

It's fine. I'm not even 100% sure they are NTFS, but most external drives come preformatted as NTFS. :)

fdisk would confirm or deny that.

---

### Post by astrobob.tk on 2010-09-28
> **psusi said:**
> Are you talking about a single file that is 3gb in size?  Or total?  IIRC, fat32 can not handle a single file over 2gb in size, so if the disk is using that, and you are talking about a single file, that would explain it.

Indeed. I ran fdisk -l & it shows ```
System: W95 FAT32 (LBA)
```What do you suggest I do ? I am mainly a linux user but on very rare occasions I need to access my files under Win.

The 3GB file i was mentioned is one of the tarballs (.tar.bz2) i was creating of my files (tarballs under 4 GB) as mentioned in the previous post.

Just for better info: the hdd's i am using are both Transcend StoreJet. One is a [**StoreJet 25C**]("http://www.transcendusa.com/products/ModDetail.asp?ModNo=211&LangNo=0&Func1No=&Func2No=") (the old one I am copying from) & another [**StoreJet 25M**]("http://www.transcendusa.com/products/ModDetail.asp?ModNo=198&SpNo=1&LangNo=0") (the one I want the files on). I thought buying Transcend was a good thing as they say that its Linux compatible. Apparently it seems just like any other disk, nothing added.

---

### Post by CharlesA on 2010-09-28
Yeah, FAT32 is the hangup. If you use Windows, I would suggest formatting it to NTFS, as ext4 has very iffy support (as of now at least) in Windows. ext3 is good to go tho.

It's really up to you what you want to format it as; rsync will copy the files regardless of the format of the drive.

---

### Post by astrobob.tk on 2010-09-29
> **CharlesA said:**
> Yeah, FAT32 is the hangup. If you use Windows, I would suggest formatting it to NTFS, as ext4 has very iffy support (as of now at least) in Windows. ext3 is good to go tho.

It's really up to you what you want to format it as; rsync will copy the files regardless of the format of the drive.

1) Is ext3 compatible with Windows XP & 7 ?

2) I just formated the disk with "Disc Utility" to NTFS but here is what it shows in the disk utility:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=6788[/IMG]

& here what fdisk -l says:

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)
```What exactly is the situation ? Is it now NTFS ? or still FAT32 ?

---

### Post by CharlesA on 2010-09-29
It's still FAT32.

You have to use a third-party drive to access ext3 partitions on Windows.

If you are going to be using it with Windows, it's better to just use NTFS.

Format it to NTFS using gparted:

Alt+F2:
```
gksu gparted
```

---

### Post by astrobob.tk on 2010-09-29
> **CharlesA said:**
> It's still FAT32.

You have to use a third-party drive to access ext3 partitions on Windows.

If you are going to be using it with Windows, it's better to just use NTFS.

Format it to NTFS using gparted:

Alt+F2:
```
gksu gparted
```

thx. I used it & apparently I had already formatted it to NTFS but repeated the process anyways.

Moreover, I connected both disks, & used ```
cp -rv source directory
``` to copy the files. It took 2 hrs & 40 minutes to copy nearly 167 GB from one disk to another. 

I then checked the copied directory (right click > properties - any terminal command for this ?-) to check the number of files & the total size of the directory compared to the original.
Apparently the number of files is the same, thankfully, though the total size of the directory decreased 0.2 GB.

---

### Post by CharlesA on 2010-09-29
If one is FAT32 and the other is NTFS, NTFS handles larger files better then FAT32.

If you want to run rsync to make sure all the files are there, you can. ;)

---

### Post by astrobob.tk on 2010-09-29
> **CharlesA said:**
> If one is FAT32 and the other is NTFS, NTFS handles larger files better then FAT32.

If you want to run rsync to make sure all the files are there, you can. ;)

could you help in regard of rsync ? I never used it before, but I recently installed Back In Time, which I suppose is based upon it. Any further guides ?

thx

---

### Post by CharlesA on 2010-09-29
> **astrobob.tk said:**
> could you help in regard of rsync ? I never used it before, but I recently installed Back In Time, which I suppose is based upon it. Any further guides ?

thx

Easy to do:

```
rsync -ri /path/to/source /path/to/destination
```

Man pages are a good start:

```
man rsync
```

---

### Post by astrobob.tk on 2010-09-29
> **CharlesA said:**
> Easy to do:

```
rsync -ri /path/to/source /path/to/destination
```Man pages are a good start:

```
man rsync
```

what is the output I should expect in case there's something wrong/missing ?

it might be a silly question, but how can I exit the man of a command while keeping the same terminal open ?

---

### Post by CharlesA on 2010-09-29
You'll get no output if there is nothing transfered. :)

Hit "q" to exit a man page.

---

### Post by astrobob.tk on 2010-09-30
> **CharlesA said:**
> You'll get no output if there is nothing transfered. :)

Hit "q" to exit a man page.


thank you ChasrlesA. that's been very helpful :D

---

### Post by SeijiSensei on 2010-09-30
If you add the "v" switch to the rsync options, you'll get a list of the files being transferred and some summary information as well.

Charles, did you recommend -ri because the target isn't a *nix filesystem?  I usually use -a which preserves symlinks, permissions, etc., but my targets are always other *nix filesystems.

---

### Post by CharlesA on 2010-09-30
> **SeijiSensei said:**
> If you add the "v" switch to the rsync options, you'll get a list of the files being transferred and some summary information as well.

Charles, did you recommend -ri because the target isn't a *nix filesystem?  I usually use -a which preserves symlinks, permissions, etc., but my targets are always other *nix filesystems.

I use -a, but I need to run it with sudo to keep owner/group permissions the same.

If they aren't copying to a *nix file system, that info is pointless. 

Well, that and the OP used cp -r, so I figured rsync -r would work fine as well (both have -a options, which I use as well)

I also use the -i switch to see what it's doing to the files. I think -v does a similar thing, but I like the output of -i.

---

