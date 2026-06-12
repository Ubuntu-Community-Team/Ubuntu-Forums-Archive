---
title: "Stale NFS file handle on USB pendrive"
date: 2009-09-13
forum: General Help
---

### Post by Rhapsody on 2009-09-13
This problem is now getting increasingly frustrating now that I've been at this several days and seem no closer to figuring out any solution.

I have a USB pendrive here that I bought expressly for the purpose of easily and securely transferring files between two computers I have here. The pendrive works with absolutely no problems on one PC using Ubuntu 9.04. It is automatically mounted, I have read and write access, and it unmounts correctly.

But on the PC I have here (using Kubuntu 9.04) it doesn't work as well. It mounts correctly at /media/disk, I can read files on the pendrive, and I can delete files on it. But I can't write anything to it. Attempting to do so using a 'sudo cp' command (eliminating permissions from the equation) results in this:

```
cp: accessing `/media/disk/moe 44168 ogino_chihiro spirited_away (1024).png': Stale NFS file handle
```

I have rebooted the PC twice since first encountering this problem, yet it persists. The drive is formatted as ext2 and has been confirmed as working on the other PC. As I recall, I could read and write to this pendrive under Kubuntu 8.04, though I was unable to unmount the drive back then.

I have files I would very much like to transfer from this PC to the other now, can anyone help make this happen?

---

