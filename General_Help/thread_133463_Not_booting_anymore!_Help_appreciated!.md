---
title: "Not booting anymore! Help appreciated!"
date: 2006-02-20
forum: General Help
---

### Post by fladd on 2006-02-20
Hello,

my Breezy is not booting anymore.
It always stucks at "Mounting root file system". When trying to boot in Recovery Mode (which also fails) it says additionally "EX3-fs: hda7: ohrphan cleaning on read only file system".
I have absolutely no idea what this is about. I didn't install, change or whatever anything. Last thing I did was to test the Dapper Flight 4 Live CD, but that cannot be the reason I guess. I also didn't boot the last 2 days, but just used suspend to disk. And now when I had to reboot, since it didn't recognize any usb sticks anymore, I got this error and cannot proceed.
So, if anyone has an idea, PLEASE answer!

Thank you
fladd

---

### Post by fladd on 2006-02-20
Really no ideas???
Anyone? Maybe?

fladd

---

### Post by fladd on 2006-02-20
I just bootet into Windows and checked the filesystem with PartitionMagic8.

It says: Error #1201; Ext2 superblock contains illegal information.

This is trange since it first recognizes the filesystem as EXT3...which it actually is...

Any ideas how to fix this from Windows? Partitionmagic can not fix errors.

Thanks
fladd

---

### Post by fladd on 2006-02-20
No one else having this problem?

fladd

---

### Post by rowanparker on 2006-02-20
i know your fustrated, but don't post 4 times in 2 hours.

back up all info using live cd, then reinstall.

---

### Post by fladd on 2006-02-20
Well, the reason I do a post here is that I don't want to reinstall.
I needed plenty of time to configurate my system. I don't want to do this again.
I hope there is another way.
Sorry for posting that often, but I really don't know what to do. I am in my semester abroad in Italy and I need my computer. (By the way, I just posted 3 times :-) )

Regards
fladd

---

### Post by az on 2006-02-20
It sounds like a hardware problem.  Sorry.


If you can, you can try to make an image of the partition for data recovery.


can you 
dd if=/dev/hda7 of=file 
where file is on a large enough harddrive?

---

### Post by fladd on 2006-02-21
I could fix the problem using fsck from the Livecd.
It is, however, strange, that Breezy didn't try to fix it on bootup itself.
Anyway, thanks for your answers.

Regards
fladd

---

