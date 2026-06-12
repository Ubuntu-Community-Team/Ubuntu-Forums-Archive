---
title: "Creating Really Big Volumes &amp; Backups"
date: 2010-10-24
forum: General Help
---

### Post by jkounis on 2010-10-24
First Question:

I have a very big volume (20+TB). When I try formatting it as ext4, I get the error message:
> mke2fs 1.41.12 (17-May-2010)
mkfs.ext4: Size of device /dev/sdc1 too big to be expressed in 32 bits
	using a blocksize of 4096.
I understand that ext4 has a limit of 1EB (about a million terabytes), but a 32-bit limitation in e2fsprogs prevents me from creating a partition > 16TB.

Until e2fsprogs is updated to use 48-bit block addressing, it appears my choices are:
[LIST=1]
[*]Break up the volume into smaller volumes < 16TB, or
[*]Use xfs or zfs (I have already created a test xfs partition, and it works fine).
[/LIST]

Does anyone have any opinions about which option is preferable? I have never used xfs before. Is it as robust as ext4? Is it as well supported by Ubuntu? What about zfs? Is it worth downloading from the ppa?

Second Question:

I now have a huge amount of data to back up. 

In the old days, I remember making a full backup of a "big" 10 MB hard drive by taking a stack of floppies and inserting them one at a time into my floppy drive while my backup program split the backup into 1.4 MB chunks small enough to fit on a floppy.

I now have the same problem, but at a different scale. I need to back up 20+TB onto a stack of external 2TB drives.

Is there any software package that can fragment a backup in this way?

---

### Post by IMSargon on 2010-10-24
Are you running 64-bit Ubuntu? Somebody can correct me if I'm wrong, but you might need to be. 

I've been pleasantly surprised by the speed and ease provided by fuse-zfs. 

As far as splitting up backups, this is the problem the "tar" command was born to solve. You just use the --multi-volume option. Read the man page carefully to ensure that you are using all the options that you need. Also, the split command can split big files for you.

---

### Post by jkounis on 2010-10-24
Yes, I am using 64-bit Ubuntu.

Thanks! I'll look into the multi-volume feature of tar.

---

### Post by IMSargon on 2010-10-24
I've just check around and the latest info seems to say that e2fsprogs has not yet been released in full 64-bit. You can get a 64-bit version from their git repository, but I don't recommend that if you care at all about any of that 20TB.

---

### Post by jkounis on 2010-10-25
I kind of do care for the 20TB data, even if they're just ones and zeros. Furthermore, some types of bugs such as a slow data corruption would be devastating, since I may end up backing up corrupted data before I discover the problem.

I think I'll wait until the stable 48-bit (or 64-bit) versions of e2fsprogs are released.

Thanks.

---

### Post by srs5694 on 2010-10-26
My understanding is that XFS is quite stable. I use it on a ~1.2TB logical volume on my MythTV box, which runs Ubuntu. That system has been in service for a couple of years with no filesystem problems. As the volume in question holds my recordings, it sees a fair amount of action.

Unless you're desperate for ZFS-specific features, I don't see the point of using it instead of XFS. As a FUSE filesystem, it's starting with a set of disadvantages, such as speed issues and extra complexity. Btrfs will eventually be a better choice on Linux, and in fact Btrfs might be a better choice today; however, Btrfs's tool set isn't yet complete, and I get the impression that some of its more advanced features aren't yet as reliable as they should be. It's worth keeping your eyes on for the future, but for now, leave it for experimental systems.

---

### Post by IMSargon on 2010-10-26
Although I haven't used it myself, XFS is a tried and true filesystem and will suit your needs well. 

I don't recommend BtrFS at this time. While I hope at some time in the future it will be on par with ZFS, I would consider it in an early debugging stage and it is not yet feature-complete. 

While FUSE does add another layer to your filesystem stack, it has proven itself to be both fast and reliable over the past several years, in my experience. I chose ZFS over XFS for its block-level checksums (the filesystem can detect and repair silent data corruption), RAID-Z (this is RAID-5 without the write hole by using Copy-On-Write semantics), and snapshots (these are created instantly and allow you to roll back the filesystem to a previous time. They only take up as much space as the files that have been modified or deleted since the timepoint). I was also able to remove the LVM layer as ZFS also performs this function. If speed is critical (ie multiple simultaneous users) or if you have no need for the features I've listed above, then XFS is probably a better choice for you.

In any case, don't forget backups. This means separate disks in a separate location.

---

### Post by psusi on 2010-10-26
> **IMSargon said:**
> I've just check around and the latest info seems to say that e2fsprogs has not yet been released in full 64-bit. You can get a 64-bit version from their git repository, but I don't recommend that if you care at all about any of that 20TB.

No, source code is just text; it is neither 32 nor 64 bit.  You compile source into a binary program which is either.  If you are running the 64 bit build of Ubuntu then you have the 64 bit build of e2fsprogs.  The problem is that ext4 still uses 32 bit block numbers, and so is limited to 16tb.  It has space to expand to 48 bit block addressing, but this feature has not been implemented/enabled yet.

It is a shame that you are hitting the ext4 limit, because I think you would be a perfect case for using dump rather than tar, but dump only works on ext[234].

Though I suppose that with the right trickery with the tar incremental backups, you can get it to do the tower of Hanoi backup sequence too.

---

### Post by IMSargon on 2010-10-26
> No, source code is just text; it is neither 32 nor 64 bit.

Sorry, let me rephrase:

Improved source code for e2fsprogs exists that removes this limitation, but has not been released as stable. The limitation is not in ext4, but in e2fsprogs. It is possible to download and compile a version of e2fsprogs that does not have this limitation. I don't know when this version will be considered stable, however.

There are a number of changes one makes in writing code that allows it to run most efficiently on either a 64-bit or 32-bit processor, but I guess you could correctly say that the code itself is not inherently 64-bit or 32-bit. Furthermore, in some programming languages there may be no differences whatsoever.

---

### Post by srs5694 on 2010-10-26
> **psusi said:**
> It is a shame that you are hitting the ext4 limit, because I think you would be a perfect case for using dump rather than tar, but dump only works on ext[234].

By its nature, dump is filesystem-specific. The Linux "dump" command is, as you say, specific to ext2/3/4; however, there is an "xfsdump" utility that does more-or-less the same thing for XFS. If you make a backup with dump you won't be able to restore it on XFS, though, and if you make a backup with xfsdump, you won't be able to restore it on ext2/3/4. Tarballs, by contrast, are filesystem-independent, although they do support most or all of the Unix/Linux-style filesystem metadata and file types, such as permissions, ownership, symbolic links, etc.

---

### Post by psusi on 2010-10-26
> **srs5694 said:**
> If you make a backup with dump you won't be able to restore it on XFS, though, and if you make a backup with xfsdump, you won't be able to restore it on ext2/3/4.

That is not true: restore does not know or care what filesystem you are using.

---

### Post by srs5694 on 2010-10-26
> **psusi said:**
> That is not true: restore does not know or care what filesystem you are using.

I stand corrected. I just checked, and I was able to restore a dump file made from ext3fs on an XFS partition. I haven't tried using xfsrestore to restore an xfsdump file on another filesystem, though.

---

