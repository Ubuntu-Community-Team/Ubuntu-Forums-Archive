---
title: "Extremely Slow NTFS write under 11.10 AMD64"
date: 2012-04-20
forum: General Help
---

### Post by systemarpi on 2012-04-20
Hello community!,
I am having big troubles writing files on my NTFS partition, the disk is a SSD (OCZ Vertex 3) which works perfect with EXT4, I can copy a 300 MB file in around ~1sec while the same file takes around ~8sec on NTFS.

Is this horrible performance the expected one?

My fstab is like this:
For EXT4 ext4 commit=240,barrier=0,nodiratime,noatime,nobh,discard,errors=remount-ro
For NTFS ntfs defaults,umask=1000,gid=1000

My Kernel is 3.0.0-12-generic

Thanks in advance

---

### Post by dcstar on 2012-04-20
> **systemarpi said:**
> Hello community!,
I am having big troubles writing files on my NTFS partition, the disk is a SSD (OCZ Vertex 3) which works perfect with EXT4, I can copy a 300 MB file in around ~1sec while the same file takes around ~8sec on NTFS.

Is this horrible performance the expected one?

My fstab is like this:
For EXT4 ext4 commit=240,barrier=0,nodiratime,noatime,nobh,discard,errors=remount-ro
For NTFS ntfs defaults,umask=1000,gid=1000

My Kernel is 3.0.0-12-generic

Thanks in advance

[LIST=1]
[*]There is no TRIM support for NTFS filesystems under Linux, so you will eventually exhaust all the free blocks on your device.
[*]You should be using the ntfs-3g mount type for NTFS.
[/LIST]

---

### Post by systemarpi on 2012-04-20
> **dcstar said:**
> [LIST=1]
[*]There is no TRIM support for NTFS filesystems under Linux, so you will eventually exhaust all the free blocks on your device.
[*]You should be using the ntfs-3g mount type for NTFS.
[/LIST]

Hi,
I see, bad luck, what's the purpose of using ntfs-3g? I thought it was symlinked with ntfs (in this version 11.10)

I tried that before this post, I only changed the fstab from ntfs to ntfs-3g with exactly same result (after restart)

Was that the wrong way?

---

