---
title: "File corruption after system crash"
date: 2012-06-10
forum: General Help
---

### Post by vintermann on 2012-06-10
Hi,

I'm having a problem with sporadic crashes when my system does graphics-intensive operations (= games). I'm guessing it's the NVidia driver, but the crashes are so bad they don't respond to REISUB, and they leave no trace in the logs that I can find. 

However, that's not the worst of it. The worst is that if a program has open files in my home catalog, they are corrupted. It's not possible to open them for reading or writing at all, even cp fails with 

```
cp: cannot open `level.dat' for reading: Input/output error

```

Looking in the logs after that, I find this:

```
Jun 10 08:48:29 harald-W860CU kernel: [  840.778314] Valid eCryptfs headers not found in file header region or xattr region, inode 8913002
Jun 10 08:48:29 harald-W860CU kernel: [  840.778319] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```

It may be that it only happens if the crash happens exactly when writing to disk, but I don't think so. I've had savestates from emulators get corrupted, and they aren't usually written to except when saved, are they?

So my main question: Are these files recoverable? Is there some trick you can do with ecryptfs to get them back?

I'm also interested in hints to how to diagnose the cause of the crashes, when there's nothing in the logs and SysRq keys don't work.

---

### Post by lingophile on 2012-07-22
I have been having similar crashes (hard lockup, no mouse,keyboard or REISUB) ever since I got my new laptop (HP Pavilion dv4, intel gfx, not NVIDIA) and they appear to be in periods of heavy graphic work, or possibly it's with high memory usage. 
Very hard to diagnose as logs are gone on reboot.  Same issue of disk corruption with same message.  Ubuntu 11.04 (sticking with Gnome 2!)

---

### Post by vintermann on 2012-08-26
I found out that the apparently corrupted files were indeed caused by the zero-length file in ecryptfs-bug. Minecraft wrote 0-length files when the system crashed.

But I still haven't solved the sporadic Nvidia crashes problem.

---

