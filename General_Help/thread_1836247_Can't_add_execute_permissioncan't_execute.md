---
title: "Can't add execute permission/can't execute"
date: 2011-08-30
forum: General Help
---

### Post by BlueCormorant on 2011-08-30
Hi,

I'm trying to run OpinonFinder on Ubuntu 10.10. With considerable help from someone I managed to get it installed (I think) but it won't run properly. Upon inspection it appears that a number of executables won't execute.

When I look at one of the culprit  executables with ls -l it only has rw permission. I've tried chmod +x,sudo chmod +x, sudo o+x and anything else I can think of but ls -l still shows -rw------. If I right click on it with the file manager thing (sorry, don't know what it's called) it tells me that the file is an executable but I can't select execute on the permissions tab. Oddly it's not greyed out: I can tick the box, but it unticks itself.

What am I missing?

Is this likely to be an ownership issue, something that's gone wrong during the installation, or something else?

Thanks.

---

### Post by searchfgold6789 on 2011-08-30
how about```
sudo chmod a+x
```

---

### Post by CatKiller on 2011-08-30
Windows filesystems can't handle UNIX-style permissions.

---

### Post by Zorgoth on 2011-08-30
> **CatKiller said:**
> Windows filesystems can't handle UNIX-style permissions.

Meaning that if you are using FAT32 or NTFS or similar such a problem may not be fixable.  FAT32 I believe sets permissions on mounting when used in Linux; I don't know whether you can make things executable at time of mounting or not.

If you are using ext2, ext3, or ext4, this behavior is extremely odd.  Can you make other files on the same drive/partition executable?

---

### Post by BlueCormorant on 2011-08-31
Thanks all. I read somewhere before about NTFS and executables but forgot about it. This is a dual-boot machine and the files I was referring to are indeed on the shared storage partition which is NTFS. I should have plenty of room on the Linux partition so will move them there.

Another lesson learned.

---

