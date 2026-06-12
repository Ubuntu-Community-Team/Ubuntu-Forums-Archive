---
title: "rm -r file recovery on ntfs partition?"
date: 2010-01-29
forum: General Help
---

### Post by BrutalSpoon on 2010-01-29
Hi guys,

I've just been a total and utter idiot.

I was copying a bunch of files between hard drives. For some reason I have permissions issues, but I was able to copy the data using cp in the terminal (I know I can sort out permissions, but that's something for another thread).

So, I start copying files just fine, but cp doesn't have any sort of progress indication. So, I started up another two terminal windows, cd'd to the source and destination folders, and ls -l'd each to compare the folders.

At this point, I realised that I'd forgot to add -r to the cp command, so cancelled it. I decided it'd be better to start again and add -r in, and repeat the command. So, I went to the folder, went up a level, then rm -r'd the folder I was just in. It wasn't until I'd gone through with the command that I realised I was actually in the source folder ](*,)

So, putting aside all the obvious things like 'You dope, you shouldn't have been messing around with rm -r, let alone sudo' and 'With great power comes great responsibility' and 'This never would have happened if you'd just sorted out your permissions and used Nautilus', is there any way I can recover the data? I know it's possible in ext2, but not in ext3, but it's on an NTFS partition. Is it possible to recover files from this?

It's not life and death, but it'll save me hours of time and a bucket load of bandwidth. Any help will be incredibly useful and gratefully received.

Thanks in advance (as always),

BrutalSpoon

---

### Post by audiomick on 2010-01-29
Hi.
I've no direct experience, only read stuff.
First thing is, don't write anything to the drive until you are ready to start a recovery attempt.

There is some documentation here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Hope that helps.

---

### Post by n0dix on 2010-01-29
Use this: [http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

---

### Post by BrutalSpoon on 2010-01-29
Well, I'm trying out ntfsundelete. It's found a bucketload of files, which is encouraging, but I'm not sure what to do next. I don't know how to recover the files (which are almost exclusively .mkv files, with a few .avis). I'd attempt to recover them all, but keep getting

```
ERROR: NO inode(s) AND NO match-regex specified!

```

I don't know what the deal is with inodes. Could anybody help me with that? I'll give you any information you need, but I don't even know where to start.

---

### Post by n0dix on 2010-01-29
> **BrutalSpoon said:**
> Well, I'm trying out ntfsundelete. It's found a bucketload of files, which is encouraging, but I'm not sure what to do next. I don't know how to recover the files (which are almost exclusively .mkv files, with a few .avis). I'd attempt to recover them all, but keep getting

```
ERROR: NO inode(s) AND NO match-regex specified!

```

I don't know what the deal is with inodes. Could anybody help me with that? I'll give you any information you need, but I don't even know where to start.

See this please. [http://docs.sun.com/app/docs/doc/819-2240/ntfsundelete-1m?a=view](http://docs.sun.com/app/docs/doc/819-2240/ntfsundelete-1m?a=view)

---

### Post by doas777 on 2010-01-29
perhaps using testdisk to try to recover the entire partition is best. I ahve to assume it will work with ntfs as well as with extx

---

