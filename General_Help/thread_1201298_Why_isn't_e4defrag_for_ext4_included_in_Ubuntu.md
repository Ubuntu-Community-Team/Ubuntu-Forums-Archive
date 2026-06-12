---
title: "Why isn't e4defrag for ext4 included in Ubuntu?"
date: 2009-07-01
forum: General Help
---

### Post by cdysthe on 2009-07-01
Hi,

I know that defragmentation isn't such a big problem with ext3/4 file systems. However, there is a defragmentation solution developed for the new ext4 file system. It's called e4defrag. There's one situation where a defragger for ext4 could be useful, namely if you convert from ext3 to ext4.I did that following the instructions here:

[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

In this documentation it's recommended to do a defrag after migration to also update file mapping from indirect to direct, so I was wondering why this defrag tool isn't included in Ubuntu?

---

### Post by credobyte on 2009-07-01
Maybe it's because of the fact that the default filesystem is ext3 ? :-\"

---

### Post by cdysthe on 2009-07-01
> **credobyte said:**
> Maybe it's because of the fact that the default filesystem is ext3 ? :-\"

I do not see why that should matter since Ubuntu include tools for other non default file systems like xfs and Reiserfs.The great thing about Linux is the freedom to choose what's not default! :) Am I missing something?

---

### Post by credobyte on 2009-07-01
> **cdysthe said:**
> I do not see why that should matter since Ubuntu include tools for other non default file systems like xfs and Reiserfs.The great thing about Linux is the freedom to choose what's not default! :) Am I missing something?

If you really need it, make a custom CD ( [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) ). If we all would start requesting "default" applications, we would need at least 10 DVD's, not a standart CD-R :p

---

### Post by cdysthe on 2009-07-01
> **credobyte said:**
> If you really need it, make a custom CD ( [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) ). If we all would start requesting "default" applications, we would need at least 10 DVD's, not a standart CD-R :p

It seems to me this is a very useful addition to files system tools offered in Linux. The "ext3/4 doesn't become defragmented" statement has been shown not to be true. I didn't use the term "default". You did! :)

I will create a live CD with a distro which includes e4defrag and get the job done that way. Thank you for the advice!

---

### Post by Nick Rhodes on 2009-09-23
A bit late with the answer, but the reason is because its not finished yet !



> The defragmentation support in ext4 is still a work in progress. The current e4defrag essentially creates a new file that is the same size is the existing file, checks to see if it is less fragmented, and if so, invokes a ioctl which atomically substitutes the blocks from the new file to the new file, while preserving the contents of the file.

It however, doesn't have any concept trying to make the file system better from a global point of view, in terms of (a) making sure the free space is not fragmented so as to avoid the file system becoming fragmented again in the near future, and (b) using a global file system wide strategy to move files aside to "make room" for a large fragmented file. It also hasn't undergone enough testing that it's really a good idea to recommend its use in production settings...
Read the rest: [https://bugs.launchpad.net/ubuntu/+bug/321528](https://bugs.launchpad.net/ubuntu/+bug/321528)

Cheers, Nick

---

### Post by chriswyatt on 2009-10-05
Ah, helpful comment :)

---

### Post by t0p on 2009-10-05
What kind of results can one expect from defragging an ext4 (or ext3) filesystem?  I can see from the results that defragging is a useful operation in Windows filesystems.  How do ext filesystem results match up?

---

### Post by renkinjutsu on 2009-10-05
There's a method of defragmentation for ALL filesystems..


and i find it very fast and very effective..

```
step 1. Move all data onto another storage medium
step 2. Move all data back onto original drive
```

done... and with probably 0.2% fragmentation and the process is probably faster than defragmenting.

---

### Post by jeffus_il on 2009-11-11
Agreed, ```
cp -a
```
is a great defragmenter,
If you have unallocated space on your drive, one copy may suffice,
just update yor fstab file and maybe grub, if it's the root file system that moved.

---

### Post by Ux64 on 2009-11-12
> **Nick Rhodes said:**
> A bit late with the answer, but the reason is because its not finished yet !


I'm sure that someone will bump this thread when it's completed. I have been waiting for it for quite a while. And I would like to be informed when it's ready.

---

### Post by cdysthe on 2009-11-13
> **renkinjutsu said:**
> There's a method of defragmentation for ALL filesystems..


and i find it very fast and very effective..

```
step 1. Move all data onto another storage medium
step 2. Move all data back onto original drive
```

done... and with probably 0.2% fragmentation and the process is probably faster than defragmenting.

I did this with my ext4 partitions. I did actually notice slight improvement. This was on my work laptop which is in use constantly with large file additions, copying and moving going on all the time. 

I wonder if it would be possible to create a script which could be croned to do it once a month or so on machines with enough storage connected?

---

### Post by Nick Rhodes on 2009-11-14
If your interested in such a method, there is a script called pyfragtools: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

I have never used it, so can't comment on effectiveness.



Running ```
sudo e2fsck -nfv /dev/sda1
``` on my machine shows both file and directory fragmentation to be 0.1% with 37% used (160gb hdd) I personally don't think there would be any benefit to defragging my system.

Cheers, Nick

---

### Post by graysky on 2009-11-26
> **cdysthe said:**
> I did this with my ext4 partitions. I did actually notice slight improvement. This was on my work laptop which is in use constantly with large file additions, copying and moving going on all the time. 

I wonder if it would be possible to create a script which could be croned to do it once a month or so on machines with enough storage connected?

No real point unless you're heavily fragmented.  Use fsck -f -v to check the fragmentation on your partition before wasting yer time.  Note that you'll have to do this on an unmounted partition (boot from live cd or usb).

Example:
```
fsck -f -v /dev/sda2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  147752 inodes used (11.53%)
    3289 non-contiguous files (2.2%)
      67 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 140443/260
 1849170 blocks used (36.11%)
       0 bad blocks
       1 large file

  120058 regular files
   20539 directories
      10 character device files
       1 block device file
       2 fifos
    2058 links
    7124 symbolic links (7017 fast symbolic links)
       9 sockets
--------
  149801 files
```

If the "non-contiguous files" is large, say over 10 %, you might wanna do it.  Otherwise, don't waste your time.

---

### Post by graysky on 2010-05-17
> **jeffus_il said:**
> Agreed, ```
cp -a
```
is a great defragmenter,
If you have unallocated space on your drive, one copy may suffice,
just update yor fstab file and maybe grub, if it's the root file system that moved.

You can't really defragment internal fragmentation.  [http://en.wikipedia.org/wiki/Fragmentation_%28computer%29](http://en.wikipedia.org/wiki/Fragmentation_%28computer%29)

---

### Post by JamesKeim on 2010-07-03
I would like to see e4defrag included but I not all that concerned with how much fragmentation ext3 or ext4 exhibit. The reason it would be useful to include is that it is the "suggested" way of implementing [FONT=Lucida Console]extents[/FONT] in a file system that has been converted from ext3 to ext4. (see: [COLOR=Blue][Migrating to Ext4: IBM developerWorks]("http://www.ibm.com/developerworks/linux/library/l-ext4/#N101BE")[/COLOR])
 
I have one laptop that would make this very helpful. 

My concern is that any kernel compiling options that might be needed to run e4defrag haven't been included in the stock Ubuntu kernel. Anyone know?

I realize that copy -a is still an option for achieving a similar result. I had just hoped e4defrag would have been included by now.

---

### Post by Ferroin on 2011-09-25
> **credobyte said:**
> If you really need it, make a custom CD ( [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) ). If we all would start requesting "default" applications, we would need at least 10 DVD's, not a standart CD-R :p

I think the point that is being made is not that e4defrag isn't on the default install, but that it isn't even in the repositories, and therefore you would have to build it yourself.

---

### Post by oldos2er on 2011-09-25
Closed for necromancy.

---

