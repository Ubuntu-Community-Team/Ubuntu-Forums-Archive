---
title: "[Q] A filesystem within a dynamic allocated file inside another filesystem"
date: 2011-07-23
forum: General Help
---

### Post by arathorn2nd on 2011-07-23
Turns out what I was looking for was **sparse** files to be used as filesystems; heh, nothing beats knowing the name of things :)

```
arathorn2nd@ubuntu:~$ dd if=/dev/zero of=sparse bs=1024k count=0 seek=20k
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000318931 s, 0.0 kB/s

arathorn2nd@ubuntu:~$ mkfs.ext4 sparse 
mke2fs 1.41.11 (14-Mar-2010)
sparse is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
(...)

arathorn2nd@ubuntu:~$ ls -lh sparse 
-rwxrwxrwx 1 root root 20G 2011-07-25 17:09 sparse

arathorn2nd@ubuntu:~$ du -h sparse 
4.9M	sparse

```
> Hello folks,

I've come back to Ubuntu as my main operating system as I found 10.04 will behave with my ati gpu.

Now I'm researching filesystem, as I need to create some temporary ones, and expected to find something along the lines of VirtualBox's VDI files that can contain a whole filesystem but are dynamically allocated.

Can Ubuntu do this natively, create a file inside a filesystem containing a whole filesystem but that's not completely allocated on the harddisk? I don't want to create a bunch of 30Gb files on my laptop, even with the 250Gb hard disk.

Thanks a lot.

---

### Post by dino99 on 2011-07-23
Thats the way linux follow with log files.

---

### Post by 2F4U on 2011-07-23
If I understand you right, then LVM could be what you want. It allows you, for example, to create a 30 GB /home partition. And if you need more space and if there is still space available within the LVM volume, you can increase the /home partition.

---

### Post by arathorn2nd on 2011-07-23
It seems I couldn't explain myself correctly; what I've done in the past was create a file filling it with zeroes and make a filesystem of it by:

$ dd if=/dev/zero of=/storage/temp.fs bs=1M count=20480
$ mkfs.ext4 /storage/temp.fs

The problem with this approach is that I have to create a 20Gb file everytime I need one of these filesystems, and I need half a dozen of them for my work most of the time.

Is it possible to create an empty zero byte file and create a 20Gb filesystem inside without fully allocating it?

---

