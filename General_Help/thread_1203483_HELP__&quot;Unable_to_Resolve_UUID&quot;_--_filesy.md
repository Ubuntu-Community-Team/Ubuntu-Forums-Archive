---
title: "HELP : &quot;Unable to Resolve UUID&quot; -- filesystem /home disappeared!"
date: 2009-07-03
forum: General Help
---

### Post by DWRZ on 2009-07-03
Yesterday I increased the size of my Windows partition using a Windows partitioning program. I took off 10GB from my /home to put on the Windows partition. It wasn't straightforward and I had to shift things around a lot-- I had to play around with resizing the swap space too. I'm on an Asus Eee PC 901, SSD drive.

When I start up Kubuntu, after the check of the root file system starts, I eventually get:
```
fsck.ext4: Unable to resolve 'UUID=257f710f-afc2-4207-b255-8288bca1b586'
fsck died with exit status 8
```

It then goes to a shell.

Here is my fdisk -l:
```

/dev/sda1 * 1 3856 30973288+ 7 HPFS/NTFS
/dev/sda2 3857 5072 9767520 83 Linux
/dev/sda3 5073 7303 17920507+ 83 Linux
/dev/sda4 7304 7854 4425907+ 5 Extended
/dev/sda5 7304 7854 4425876 82 Linux swap / Solaris

```

(I also have an SDB on the system, a 4GB FAT32, but no problems with it, so leaving all info out.)

My blkdid:
```

/dev/sda1: UUID="5244FCC144FCA93D" TYPE="ntfs"
/dev/sda2: UUID="6506849a-21f2-473b-b56f-3041a5fd3f56" TYPE="ext4"
/dev/sda5: TYPE="swap"

```

My fstab:
```

#/ was on /dev/sda2 during installation
UUID=6506849a-21f2-473b-b56f-3041a5fd3f56 / ext4 relatime,errors=remount-ro 0 1
#/home was on /dev/sda3 during installation
UUID=257f710f-afc2-4207-b255-8288bca1b586 /home ext4 relatime 0 2
#swap was on /dev/sda4 during installation
UUID=66fe7d86-2858-40be-9db8-98ee6cc5a875 none swap sw 0 0

```

ls -o /dev/disk/by-uuid/ yields:
```

total 0
lrwxrwxrwx 1 root 10 Jul 3 16:11 5244FCC144FCA93D -> ../../sda1
lrwxrwxrwx 1 root 10 Jul 3 16:11 6506849a-21f2-473b-b56f-3041a5fd3f56 -> ../../sda2

```

I can ignore the prompt and continue booting, which leads me to the KDE login screen. If I try to login, I get some error about /home.

Both the Windows partitioning program and GParted (run from Puppy Linux) showed all partitions present with data present.

:(

I have no idea what to do. Any help is much appreciated! :(

---

### Post by drs305 on 2009-07-03
This is a common error message after reparitioning gets messed up. Your fstab lists a separate /home partition with a uuid of UUID=257f710f-afc2-4207-b255-8288bca1b586 but the system may not be seeing that partition.

The system no longer sees your /home partition. Notice that blkid only shows 3 partitions: probably your Windows partition, a single ext4 partition ( / ) and the swap partition. The /home partition no longer exists (according to the system), so when you boot and the system looks for it the system complains. Fdisk and blkid don't agree. Fdisk says there is another ext4 partition but blkid doesn't see it.

You can run this to get the latest information, avoiding outdated information which might have been cached:
```
sudo blkid -c /dev/null

```

When you run "fdisk" do you get any errors?

---

### Post by michy99 on 2009-07-03
Your home partition is still there, you just need to figure out the new UUID and edit fstab.

---

### Post by DWRZ on 2009-07-03
Thanks a lot for the help.

I did not get any errors on fdisk -l, should I try just running fdisk?

For blkid -c /dev/null I get the same thing as plain blkid.

From the little I know I also figure that /sda2 needs a new UUID, but how do I get that? :(

---

### Post by michy99 on 2009-07-03
Actually, sda2 is your / partition, sda3 is /home. What do you get from```
blkid /dev/sda3
```

---

### Post by decoherence on 2009-07-03
It'd be good to get the UUID stuff working again, but in case it doesn't, this change to your /etc/fstab might help.

```
#/home was on /dev/sda3 during installation
UUID=257f710f-afc2-4207-b255-8288bca1b586 /home ext4 relatime 0 2
```

change the above to

```
#/home was on /dev/sda3 during installation
/dev/sda3 /home ext4 relatime 0 2

```

That said, better to figure out why sda3 isn't showing up in blkid.

---

### Post by DWRZ on 2009-07-03
Sorry- that's what I meant-- sda3.

blkid /dev/sda3 returns nothing. :(

Should I go ahead and edit fstab now, or try some other things first?

Again, thanks so much for your help.

---

### Post by decoherence on 2009-07-03
Strange that it shows up in fdisk -l and not blkid. I'm afraid I don't know enough about blkid or UUIDs to speculate why that might be. Out of curiosity, could you run the following?

```
cat /proc/partitions
```

I wonder if /dev/sda3 shows up there...

Anyway, might as well try the fstab edit unless drs305 or  michy99 can suggest something else. It won't mess anything up worse than it already is! Maybe just copy the line with the UUID, change it to /dev/sda3 and comment out the original like so

```
#/home was on /dev/sda3 during installation
#UUID=257f710f-afc2-4207-b255-8288bca1b586 /home ext4 relatime 0 2
/dev/sda3 /home ext4 relatime 0 2
```

Just make sure whatever program you use to edit /etc/fstab isn't going to try to wrap lines. That WILL mess things up worse than they are!

---

### Post by DWRZ on 2009-07-03
cat /proc/partitions:
```

8 0 63094784 sda
8 1 30973288 sda1
8 2 99767520 sda2
8 3 17920507 sda3
8 4 1 sda4
8 5 4425876 sda5

```

I'm using nano to edit, going to give it a shot now. :-?

---

### Post by drs305 on 2009-07-03
You could also try "ls -l /dev/disk/by-uuid" but I'd give /dev/sda3 a shot to see if it works since it's such a simple (temporary at least) solution.

If it doesn't work or you don't get results from the above command I think my next step would be booting a LiveCd and installing Testdisk.

---

### Post by DWRZ on 2009-07-03
What a mess. :(

I made the change. This time, fsck gave:
```

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4.

```

So I unmounted /dev/sda2 and ran fsck. /dev/sda2 resulted clean.

Then I got:
```

e2fsck 1.41.4 927-Jan-2009)
fsck.ext4: Group descriptors look bad... trying to backup blocks...
Resize inode not valid. Recreate(y)?

```
I hit y, then I got:
```

Group 0's inode table at 6 conflicts with some other fs block. Relocate (y)?

```

I hit yes, and it continued the same thing for a while, except the second number would change for a while, and then the Group number would change. This went on for some time.

I then started getting things like:
```

Inode 5793 is in use, but has dtime set. Fix<y>? yes
Inode 5793, i_blocks is 1605999 should be 0. Fix<y>? yes

```

This went on, and on. I went up to Inode 1610, when I suddenly realized that this might be deleting my data... :( Is it? What next? :'(

---

### Post by michy99 on 2009-07-03
Sounds like it's time to try testdisk. Boot from a Live CD and install testdisk and see if it can fix it.

---

### Post by DWRZ on 2009-07-03
I'm on the Kubuntu Live CD right now, but can't I just run testdisk from my Windows partition?

I don't really know what to do here. What am I supposed to do with testdisk?

---

### Post by michy99 on 2009-07-03
I've never used it myself, but here is a web page I found:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by drs305 on 2009-07-03
That's the link I usually give out for Testdisk. The other one is:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Start a little over half way down - the first half is for ntfs.
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by philpem on 2009-07-03
OK, your problem at the moment is that sda3 has been damaged in some way that prevents it from being mounted. That's what mount meant by "Unexpected inconsistency".

FSCK is the Linux filesystem checker. If you've used Windows (or at least the older versions of Windows), it's a bit like ScanDisk. Its sole purpose in life is to check disk partitions for damage, and do as good a job as it can of repairing said damage.

It's highly unlikely that what fsck is doing is "deleting your data" as you put it.

When your machine booted, if the filesystem check fails, you're usually dumped at a root shell. If that's the case, typing
```
fsck -f -y /dev/sda3
```
should repair the partition, and not ask you for confirmation all the time. The "-y" stops FSCK asking for confirmation, the "-f" forces it to check the partition (even if it's marked "clean").

Personally, in this situation, I'd take a backup of the drive or partition onto another drive (either as a full-blown partition or a disk file on a working partition -- Linux allows you to mount a file as if it were a partition using a process called "loopback mounting"), then work on the backup.

Hopefully this should get you on the road to recovery.

EDIT: I figured I might as well explain some of the FSCK alerts you got:

```
Inode 5793 is in use, but has dtime set. Fix<y>? yes
```

Inodes are blocks of data -- files, directories, etc. -- on the disk. This particular one has been marked as "in use", i.e. it's part of a file, but has its Deleted Time set to something other than "not deleted". Pretty minor.

```
Inode 5793, i_blocks is 1605999 should be 0. Fix<y>? yes
```

A bit more serious, but normal after (e.g.) a power failure during a disk write. The number of disk blocks in an inode is set to what FSCK thinks is a silly or incorrect value. "Should be 0" means it's probably found a subdirectory inode that has a nonzero length...

---

### Post by DWRZ on 2009-07-03
Thanks, I just looked through it. I'm a bit confused though, this seems to be to restore lost partitions, and unless I screwed things up by running fsck, don't I have my partition still there, but just not recognized? Any idea where I can look for help from here on? :( I'm at a point where I don't mind just reinstalling Kubuntu-- but I _need_ that data on/home. :( I tried mounting the partition from a LiveCD but it wouldn't mount. :(

Philpem-- I'll give it a try. How do I backup the partition? Really appreciate the help!

---

### Post by philpem on 2009-07-03
> **DWRZ said:**
> Thanks, I just looked through it. I'm a bit confused though, this seems to be to restore lost partitions, and unless I screwed things up by running fsck, don't I have my partition still there, but just not recognized? Any idea where I can look for help from here on? :( 

Yes, exactly right. Your machine knows that you have a partition, it knows where it is, and it knows *what* it is (some form of Linux partition -- in this case, fsck can tell that it's Ext4).

The first 64 sectors of the hard disc are dedicated to system information -- usually only the first sector is actually used, and it contains the partition table.

Note that what I said applies to PCs. It's different on Sun, Apple and SGI boxen :)

> **DWRZ said:**
> I'm at a point where I don't mind just reinstalling Kubuntu-- but I _need_ that data on/home. :( I tried mounting the partition from a LiveCD but it wouldn't mount. :(

You probably won't need to reinstall Kubuntu. Your root partition stores the operating system; all that's inaccessible at the moment is your home directory (or home directories if there are other users on that machine besides yourself).

> **DWRZ said:**
> Philpem-- I'll give it a try. How do I backup the partition? Really appreciate the help!

What I'd do is put in a second hard drive of the same size or larger with a single Ext2 partition on it. Then I'd power down, and connect the "target" drive (the one you're putting the backup on) to a spare IDE/SATA channel.

Boot off an Ubuntu, Kubuntu or similar install CD, then drop into the Live CD environment. First create somewhere you can mount the second drive:
```
sudo mkdir /mnt/target
```
Now find out what device name has been assigned to the new drive:
```
ls /dev/sd*
```
You'll probably see "sda1" thru "sda4", and just a single "sdb1". In that case, 'sdb' is your second drive, and sda the first.

Now mount sdb1:
```
sudo mount -t ext2 /dev/sdb1 /mnt/target
```

And copy the contents of the damaged partition (sda3) into a file on sdb1:
```
sudo dd if=/dev/sda3 of=/mnt/target/BACKUP_01.hdi bs=100M
```

This does a block-by-block copy from the damaged partition to a file on the "target" drive, in units of 100 MBytes. If you've got more RAM you can increase this, but 100MB is usually a good starting point.

After this finishes (it WILL take a few hours on a large hard drive), you'll have a file on /mnt/target that contains every single sector of the damaged partition. Now you can work on the damaged partition with fsck (or whatever) safe in the knowledge that if Something Bad Happens (tm), you can restore the image back to the drive. To do that, the command you want is:
```
sudo dd if=/mnt/target/BACKUP_01.hdi of=/dev/sda3 bs=100M
```

Like I said, this is a slow operation -- a typical HDD will be able to read/write at about 70 megabytes per second. If sda3 is 250GB in size (250,000 MB) then you're looking at a wait of about 3600 seconds, or just shy of an hour...

The advantage is that you can then point fsck at the file instead:
```
sudo fsck.ext4 -y /mnt/target/BACKUP_01.hdi
```

Or mount the filesystem in Loopback mode:
```
sudo mount -o loop,ro -t ext4 /mnt/target/BACKUP_01.hdi /mnt/foo
```

(This of course assumes that /mnt/foo exists and is an empty directory; also note the ",ro" option, which mounts the file in read-only mode)

This is pretty complex stuff... I usually just jump in and run fsck, and I can't recall a single incident where fsck has actually damaged data on a partition. I think I've only seen one situation where it's actually given up on repairing a damaged disk, and that was probably more down to the disk being absolutely covered in bad sectors...

Seriously though, what happened here -- did you shut down your PC in the middle of a disk write? This type of disk damage isn't easy to cause; you pretty much have to be very, VERY unlucky, or want to do it deliberately... :confused:

EDIT: I'd be tempted to work on the partition instead, and keep the .rdi file as a "recovery plan". If something bad happens, restore the .rdi onto the partition (sda3) and have another go... Like I said -- it's pretty slow to backup/restore entire HDDs block-wise. And don't worry about FSCK's error messages -- some of them are pretty scary-sounding, but 99% of them you can just say "yes, fix it" to and it'll fix the partition correctly.

EDIT2: There is one warning I really should have passed on. Do NOT, EVER, FOR ANY REASON run fsck on a mounted file system. You're just about guaranteed to obliterate the FS and all the data on it. This is why I said to boot off a Live CD -- nothing will be mounted except the Live CD itself (which is read-only anyway).

---

### Post by DWRZ on 2009-07-03
Philpem-- thanks again for the excellent, detailed advice. Even the stuff that doesn't fix the issue helps me gain a better understanding of what is going on. Again, thanks.

I decided to just go ahead and run fsck since I have to go at 2130 UTC and won't be back to fixing this until 0030 UTC (I'm out from 1730-2030 EDT). The data on the partition is _really_ important to me, so I know this was stupid/risky. I'm glad to hear that usually fsck doesn't mess things up, and I've always made sure to unmount everything.

In any case:
It went on for ages, then got stuck in a loop.
```

Error allocating 511 contiguous block(s) in block group 1 from inode table: Could not allocate block in ext2 filesystem
Error allocating 511 contiguous block(s) in block group 81 for inode table: Could notnot allocate block in ext2 filyststem
Restarting e2fsck from the beginning...

```

It then goes through a list of things for Group 1 and Group 81 that looks like this:
```

Group 81's inode table at 2654723 conflicts with some other fs block. Realocate? yes

```

As to how it happened... I needed more space on my Windows partition since the 20GB I'd assigned to it left me with only about 500MB of space once I installed the programs I needed. I had plenty of extra space from my /home partition, so I figured I could just move that space from there to the Windows partition. I vaguely recalled having done it in the past without any problems.

My partitions were, approximately:
sda1: Windows Partition 20GB
sda2: / Partition 10GB
sda3: /home Partition 30GB
sda4: swap 4 GB

My memory is a bit vague, but this is what I think I did.
I tried using a Windows partitioning program to reduce the /home partition and create some free space, but it seemed incapable of doing anything to ext4 (or ext partitions in general?).
So I started off by using the LiveCD text install to resize the ext4 partition. It left off a chunk of unallocated space, about 10GB.
Then I went back to Windows and tried to "move" this space to the Windows partition, but it also wouldn't budge.
I went back to the LiveCD text install and deleted the swap space. I now had ~14GB at the end of the disk.
I went back into Windows and told it to "Redistribute Free Space" in such a way so as to give the Windows partition an extra 10GB.
It did some operations, restarted, and before booting Windows it began moving all the data. As far as I recall, there were no problems, though I left the roomm when it had 2min left and came back only after it was done moving the data. If there was an error in those couple of minutes, I missed them.
I started the Partition program again and created the swap space for Linux. Not sure why it created an extended instead of primary partition.
I booted into Linux, and go the error. :(

When I get back later I will copy all the data to a separate disk. After that, what do I do though? It was a tremendous failure on my part not to back up before doing all this partition work, although I remember doing similar things in the past and never having any problems. This caught me at a really bad time. I just moved all my email archives to this disk-- I was going to back them up _this weekend_ to an external. That and a few other files on the disk are a huge source of anxiety for this problem. :(

---

### Post by bab1 on 2009-07-03
I realize that I am coming into this thread kind of late.  But I would like to contribute some information re: UUID identification for those users that may have UUID problems in the future.

Recently I repartitioned a drive and had exactly the same problem as the OP.  I found that the information for UUID is held in```
/etc/blkid.tab
```This information needs to be deleted (delete the file) and then you can run ```
sudo blkid
```

When I did the above procedure I was able to mount my new/modified partitions with UUID via fstab.

For more information on this see [[COLOR="Blue"]_https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/316322_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/316322")

Read the whole thread.

I realize this may not help the OP if fsck has damaged the partition in question.  Maybe it will help others who have UUID questions and find this thread

---

### Post by DWRZ on 2009-07-03
I just tried bab1's suggestion, blkid still does not list anything for /sda3. 

Anybody have any ideas as to what the problem could be with fsck? Or what to do next? :(

---

### Post by bab1 on 2009-07-03
At this point what partitions are listed with```
sudo fdisk -l
```

---

### Post by DWRZ on 2009-07-03
Thanks, bab1. I just ran it and it gave me the same exact output as before. :(

I just don't understand why fsck is looping, and most of all why this partition is there, apparently with some data on it (corrupted or not) but it still is not being detected. Arg! ](*,)

---

### Post by bab1 on 2009-07-03
> I just ran it and it gave me the same exact output as before. 

So then I assume that it is still listed.  Is this correct?  Part of your problem is that you used the Windows partition software on a Linux partition.  Let's not cry over that spilled milk though.

Have you removed the /etc/blkid.tab file and issued the blkid -c /dev/null command?

---

### Post by DWRZ on 2009-07-03
Using a Windows program was an idiot move. I've learned a lot of lessons... the hard way. :(

Yes, the actual  /dev/sda3 it is still listed. As for blkid-- I deleted the file and ran the command, and got the same output as before-- it displays everything but the /home partition.

---

### Post by bab1 on 2009-07-03
The same is ok!  Try mounting the partition manually from the CLI

Edit: That would be either```
sudo mount /dev/sda3 <your mount point>
```or ```
sudo mount UUID <your mount point>
```

What do you get?

---

### Post by bab1 on 2009-07-03
> ...it displays everything but the /home partition.

What do you mean by this?

---

### Post by DWRZ on 2009-07-03
I did just "sudo mount /dev/sda3" and got:
```

[ 31.808947] ext4: No journal on filesystem on sda3
mount: wrong fs type, bad option, bad superblock on /dev/sda3
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

```

Should I go back and try:
```

sudo mount /dev/sda3 /home

```
?

Thanks again.

---

### Post by DWRZ on 2009-07-03
> **bab1 said:**
> What do you mean by this?

This is what I get:
```

/dev/sda1: UUID="5244FCC144FCA93D" TYPE="ntfs"
/dev/sda2: UUID="6506849a-21f2-473b-b56f-3041a5fd3f56" TYPE="ext4"
/dev/sda5: TYPE="swap"

```

No /dev/sda3, which is my /home partition. :(

Also, question-- my Windows partitioning program is not capable of ext4. If I used it to move/resize my /home partition and it treated that partition as ext3, would that cause any problem?

---

### Post by bab1 on 2009-07-03
Is your mount point /home  ?  Do you have a directory /home on /sda2 ?
The expression is "mount <block device> at <your mount point>"

> No /dev/sda3, which is my /home partition
As I see it /dev/sda3 is not available to mount anywhere. 

> ...my Windows partitioning program is not capable of ext4. If I used it to move/resize my /home partition and it treated that partition as ext3, would that cause any problem

I don't believe Windows understands ext partitions at all, be they ext2 or 3 or 4.

Bottom line is that the windows partitioner destroyed the partition identifications on the first "super block" (SB).  I have never user the duplicate 'super blocks" but I know they are there.  I would look for information on mounting/using the alternate SB.

I will look also.

Edit: Here is how to do it [http://www.cyberciti.biz/tips/mounting-with-an-alternative-superblock.html]("http://www.cyberciti.biz/tips/mounting-with-an-alternative-superblock.html")

Now all we need is to find out what your alternates are.

And that would be here!  [http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html]("http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html")

---

### Post by DWRZ on 2009-07-03
Ok-- I'm going to give a shot with those commands-- trying to find the alternate and then running fsck with it.

---

### Post by bab1 on 2009-07-03
No fsck!!!

This is for you to mount the partition and remove the data only!!!

Edit:  My mistake, i see the e2fsck line now.  Yes let us follow the guide.

Sorry 'bout that.

---

### Post by DWRZ on 2009-07-03
Hahaha, that scared the **** out of me for a second.

Thanks so much again for all the help, bab1.

I ran it, it listed quite a few alternates. I ran two, and it gave me the same old story: 

First, it gave errors like these:
```

group descriptor 1 checksum is invalid. Fix(y)? yes
group descriptor 3 checksum is invalid. Fix(y)? yes
group descriptor 5 checksum is invalid. Fix(y)? yes
group descriptor 7 checksum is invalid. Fix(y)? yes
group descriptor 9 checksum is invalid. Fix(y)? yes
group descriptor 25 checksum is invalid. Fix(y)? yes

```

And so on...

Then it went back to the same old loop:
```

Group 81's inode table at 2654723 conflicts with some other fs block. Realocate? yes

```

It does this for several numbers for both Group 1 and Group 81.

After a while, it gives this output, then repeats:
```

Error allocating 511 contiguous block(s) in block group 1 from inode table: Could not allocate block in ext2 filesystem
Error allocating 511 contiguous block(s) in block group 81 for inode table: Could not allocate block in ext2 filyststem
Restarting e2fsck from the beginning...

```

:\

---

### Post by bab1 on 2009-07-03
It's 20:31 here in So Cal.  I have plenty of time.  Does it appear to be working?

---

### Post by bab1 on 2009-07-03
> Restarting e2fsck from the beginning...

This is not good.  It appears that some of the actual data was corrupted, see ```
Error allocating 511 contiguous block(s) in block group 1 from inode table: Could not allocate block in ext2 filesystem
Error allocating 511 contiguous block(s) in block group 81 for inode table: Could not allocate block in ext2 filyststem

```

I think the next and maybe that last try should be to try and mount the dirty partition as it is; using an alternate SB.  This is just a guess.  I don't think we will be able to fix this with fsck.  Sorry :-(

---

### Post by DWRZ on 2009-07-03
Roger. How do I do a "dirty mount"?

Is there any software I can use to try to restore data? I'm really just concerned with email and a few files. The rest-- KDE settings, all that stuff, I don't mind losing at all. :(

---

### Post by bab1 on 2009-07-03
Go back to the first guide and try and mount using their command at your alt SB.

---

### Post by drs305 on 2009-07-04
> **DWRZ said:**
> Roger. How do I do a "dirty mount"?

Is there any software I can use to try to restore data? I'm really just concerned with email and a few files. The rest-- KDE settings, all that stuff, I don't mind losing at all. :(

You can try to recover files with PhotoRec. It is part of TestDisk. It can recover files although it assigns odd names to the recovered files and you will have to figure out what they are. Here is the link:
> [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Since it's part of testdisk, I would still let testdisk take a look at your partitions first. When you run it there is an option to view the files on a partition - maybe it will be able to see them. Testdisk was linked to earlier.

---

### Post by DWRZ on 2009-07-06
I ran photorec. I got was a bunch of text files with strange names. One had a bunch of 0's in it, the other had something about LVM.ENCRYPTED or something of the sort. I got a few other files-- a video file that doesn't play, and a couple of web files that are fragments of emails. Does this mean anything? Also-- if I had encrypted the partition... which I don't remember... would that mess anything up?

I'm looking at FOSS DataRecovery stuff right now... the commercial service I contacted charges anywhere from $300-1400. :( I might just save this disk or a backup of it for the future, but right now no way can I afford that.

I want to thank you all again for the help, at least I got a chance to give this a shot.

---

### Post by michy99 on 2009-07-06
I have had success recovering files with ext3grep. It is in the repositories for Jaunty; I don't know about earlier versions. It is a little technical, but reading the man page helps. Basically you run the --dumpnames option to see what files it can recover and then either use --recoverall option to try to recover them all, or else recover individual files by name.

---

### Post by nickkontos on 2009-07-12
Hello, I've had excactlly the same problem!! I want to find a solution - fast! I've done this in a friend's computer...

```


e2fsck 1.41.4 (27-Jan-2009)

Group descriptor 1 checksum is invalid.  Fix? yes

Group descriptor 2 checksum is invalid.  Fix? yes

Group descriptor 3 checksum is invalid.  Fix? yes

Group descriptor 4 checksum is invalid.  Fix? yes

```

etc etc

```

/dev/sda2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 536's inode table at 17305632 conflicts with some other fs block.
Relocate? yes

Group 536's inode bitmap at 17301536 conflicts with some other fs block.
Relocate? yes

Group 537's inode table at 17306144 conflicts with some other fs block.
Relocate? yes

```

etc etc

```

Root inode is not a directory.  Clear? yesError allocating 512 contiguous block(s) in block group 515 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 516 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 517 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 518 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 519 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 520 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 521 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 522 for inode table: Could not allocate block in ext2 filesystem
Error allocating 512 contiguous block(s) in block group 523 for inode table: Could not allocate block in ext2 filesystem

```

etc etc


and all over again.. ahh..:cry:

```

Restarting e2fsck from the beginning...
fsck.ext4: Group descriptors look bad... trying backup blocks...

```

```

peter@turbo-x:~$ sudo dumpe2fs /dev/sda2
dumpe2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          7b2e138c-8651-4e95-b830-f70f009060a8
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              13115392
Block count:              52458249
Reserved block count:     2622910
Free blocks:              15559091
Free inodes:              12809464
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1011
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              32733
Flex block group size:    16
Filesystem created:       Thu Jul  9 22:18:23 2009
Last mount time:          Sat Jul 11 17:33:14 2009
Last write time:          Mon Jul 13 04:54:32 2009
Mount count:              16
Maximum mount count:      32
Last checked:             Fri Jul 10 18:02:59 2009
Check interval:           15552000 (6 months)
Next check after:         Wed Jan  6 17:02:59 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Default directory hash:   half_md4
Directory Hash Seed:      78af0d9e-69ef-4cdc-97b2-e5c08d223b6c
Journal backup:           inode blocks

^C
peter@turbo-x:~$ 

```


the partition i want to restore was a ext4 /home on an ubuntu 64bit 9.04 system... I've searched the Internet for a solution for 4 days now... the best i accomplished was to rescue my files in a folder on my external hard drive BUT without their original filenames... (did this with photorec)

Now.. what did happen..
The pc has an 320 gb hard drive (sda). I resized the 320gb ntfs(sda1) partition that vista was using in order to install ubuntu. I created a swap partition of 3gb (sda4) in the end of the drive, an ext4 partition before that for the / file-system (sda3) and an ext4 partition before that for the /home directory [COLOR="Red"](sda2)[/COLOR].

while I was migrating files from the ntfs partition to the /home partition I performed several resizes on both of them until the ntfs was left with 60gb (sda1) and the /home had 200gb (sda2) (/ (sda3) had 40gb from the beginning).

I then installed winxp in the ntfs (sda1) partition and restored grub.

Till then everything was going well.. And then it started : kernel panics! the one after the other... that means several no-other-choice hard resets:(

after the last crash-reboot the system couldn't read from the /home partition (sda2) and thus it complained and left me in a root console for problem-solving i guess... I could startx, gnome etc, in fact i had all of my / intact except /home :( ... 

but i didn't care about the / (sda3)- I only care for the /home (sda2) which contains over 110gb of personal data... 

I've installed a new copy of ubuntu 32bit 9.04 on sda3 now with ext3 this time (I've learned my lesson...) just for setting up the tools to rescue the personal files from sda2 ex- /home partition...

I've tried a lot of software : fsck testdisk photorec grescue magicrescue and other which i can't recall right now.. I din't test ext3grep and e3fsck because i'm not sure that they are compatible with ext4...

thank you for reading all this... hope someone can help me... I haven't slept 2 days now - I have to deliver this pc to my friend in 1 and a half day...

---

### Post by nickkontos on 2009-07-12
oh, and some more info:

```

peter@turbo-x:~$ sudo fdisk -l /dev/sda
[sudo] password for peter: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x770b143b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7808    62717728+   7  HPFS/NTFS
/dev/sda2            7809       33931   209832997+  83  Linux
/dev/sda3           33932       38499    36692460   83  Linux
/dev/sda4           38500       38913     3325455   82  Linux swap / Solaris

```

```

peter@turbo-x:~$ ls -o /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root 10 2009-07-12 22:14 43200137-99aa-4560-bfa8-290420bb4123 -> ../../sda4
lrwxrwxrwx 1 root 10 2009-07-12 22:14 D2C0B16AC0B15587 -> ../../sda1
lrwxrwxrwx 1 root 10 2009-07-12 22:14 e305d8fa-1be8-4493-ad89-8afdbcca25c5 -> ../../sda3

```

```
peter@turbo-x:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D2C0B16AC0B15587" TYPE="ntfs" 
/dev/sda3: UUID="e305d8fa-1be8-4493-ad89-8afdbcca25c5" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="43200137-99aa-4560-bfa8-290420bb4123" 
peter@turbo-x:~$ blkid /dev/sda2
peter@turbo-x:~$ blkid /dev/sda2
peter@turbo-x:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  312571224 sda
   8        1   62717728 sda1
   8        2  209832997 sda2
   8        3   36692460 sda3
   8        4    3325455 sda4

```

as you can see blkid doesn't see sda2..

that's all, if you need any further info just ask me but please, tell me how can I find info because I'm pretty new in linux...

And thanks again for reading

---

