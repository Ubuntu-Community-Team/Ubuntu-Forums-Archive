---
title: "Faster Large File Transfers?"
date: 2010-05-19
forum: General Help
---

### Post by TheFu on 2010-05-19
I don't know if I'm asking this correctly, but is there a way to increase the size of used disk buffers from RAM?

I've noticed that moving a file over Samba to my Linux Lucid server that files under 950MB transfer at wire speed (600+Mbps), but any amounts above that really bog down to 1/10th or less the speed.  I assume this is because Linux is buffering the first part in RAM, but once that is full, it stops and slows down for disk writes.

I have plenty of RAM (over 4GB isn't being used at all) and would like to double the current cache/buffer size so **2 GB files transfer at a similar rate to completion**.  I expect the amount of time for dirty buffers may also need to be increased to make this useful.

a) How** is this possible**?  tunefs or /etc/sysctl.conf or some kernel setting?

b) What are the **repercussions** in doing this, if any?

c) Are there **better** **alternatives** that achieve a similar result, perhaps a dynamic buffer solution based on the estimated amount of data to be transfered?

The base OS is **10.04 Server** **x64**.

---

### Post by sedawk on 2010-05-19
Linux manages the memory in equally sized blocks called pages.
All free blocks not used by any process are used for buffers or page cache.
You can view the usage with command line tools like top or vmstat,
or you can do something like "cat /proc/meminfo".

On my ubuntu box that only runs a desktop I can see
that 1.2 GB memory are used and 700 MB are file cache.
If your system looks similar you should have 3.5 GB free
pages for file caching.

What you can try to do is to flush the page cache before
running a big transaction, e.g. before starting the
transaction do this and see if it helps
```

sync
echo 1 > /proc/sys/vm/drop_caches

```
Now there should more free memory and only a small
number of page cache used.

---

### Post by TheFu on 2010-05-19
> **sedawk said:**
> Linux manages the memory in equally sized blocks called pages.
All free blocks not used by any process are used for buffers or page cache.
You can view the usage with command line tools like top or vmstat,
or you can do something like "cat /proc/meminfo".

Thanks. That's a start, but I'm still looking for a way to double the disk buffers. How RAM is used for programs is not an issue at all.
[FONT=Fixedsys]
# more /proc/meminfo

MemTotal:        8187692 kB
MemFree:         4617136 kB
Buffers:          116364 kB
Cached:          2233068 kB[/FONT]

After running 'sync'

MemTotal:        8187692 kB
MemFree:         4616852 kB
Buffers:          116576 kB
Cached:          2233216 kB

As you can see, I have PLENTY of RAM available. Any idea how to specify it be used for disk buffers?  Maybe I'm just a little slow in understanding. This has nothing to do with virtual memory.

I'm using Linux mdadm to manage a 4 disk software array. The FS is JFS, if that matters.

I guess that I could setup a **RAM disk**, share it via NFS/**samba**/sshfs, transfer the files, then automatically move them to the real target directory.

---

### Post by sedawk on 2010-05-21
All the pages in memory not used for processes or
buffers are used for page caching and that
is exactly what you are looking for.

You have to use sync+echo to do a cleanup before
starting your big file transfer - that will
guarantee that all pages used for caching are
freed before your big transactions.

There might be other mechanism that determine
when to write caches to disk, but I'm not sure
it is easy (or recommended) to change them.

You can try to write to the existing ramdisk
at /dev/shm if you really want to speedup the
transfer and afterwards you can then transfer
the file to the real disk.
But keep in mind that you have to make sure
to cleanup /dev/shm yourself!

---

