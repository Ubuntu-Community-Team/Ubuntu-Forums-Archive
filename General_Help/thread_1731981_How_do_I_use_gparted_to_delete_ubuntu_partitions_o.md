---
title: "How do I use gparted to delete ubuntu partitions on my EHD?"
date: 2011-04-17
forum: General Help
---

### Post by TacticalApe on 2011-04-17
So, I've been having a difficult time with ubuntu on my external hard drive, and i want to wipe my ehd and get my 1tb back. I've heard I can use gparted to delete the partitions, but I have no idea how to do that. I don't even have gparted anyway. And when I try to use .exe's in ubuntu, it opens them and shows files, and doesn't run them. Help?

---

### Post by TeoBigusGeekus on 2011-04-17
If you still want to accept advice from me after last thread's mess:

Boot up with a live cd, open terminal
```
sudo apt-get install gparted
```
Then
```
gksu gparted
```
Select your drive, right click it and format it to whatever file system you want.

---

### Post by TacticalApe on 2011-04-17
OK, i'm in gparted and it says this when I try to delete the partitions:
```
Unable to delete!:
please unmount any logical partitions having a number higher than 5
```
and here's a screenshot just in case it might help:
[http://img508.imageshack.us/img508/8458/screenshotmux.png](http://img508.imageshack.us/img508/8458/screenshotmux.png)
And btw, you did help me alot in the last thread, so thanks.

---

### Post by skynet2060 on 2011-04-17
Read this blog. 

[http://www.linux.com/myblog-admin/uninstalling-a-linux-os-from-your-hard-drive.html](http://www.linux.com/myblog-admin/uninstalling-a-linux-os-from-your-hard-drive.html)

---

### Post by supergrav on 2011-04-17
Probably you're not using gparted from a live cd.

---

### Post by TeoBigusGeekus on 2011-04-17
Right click the 2 partitions (/dev/sdf1 and 2) and unmount them.
Gparted can't operate on them if they're mounted.

---

### Post by TacticalApe on 2011-04-17
I can't. I can't select Unmount. But i messed around further and deleted theall the partitions except /dev/sdf1, and stretched it out all the way so it filled up all the unallocated space. Did I do it right?
here's a screenshot of what I ended up with:
[http://img651.imageshack.us/img651/8844/screenshot1hd.png](http://img651.imageshack.us/img651/8844/screenshot1hd.png)

---

### Post by TeoBigusGeekus on 2011-04-17
Yes, you did.

---

### Post by oldfred on 2011-04-17
If you are booted into the install on the external you will not be able to unmount nor delete them. 

Suggest liveCD and even then you often have to unmount the swap partition with swapoff as liveCDs like to automount swaps to speed things up.

---

### Post by TacticalApe on 2011-04-17
So when it says the operations are still pending, does that mean I still have to wait?

---

### Post by TeoBigusGeekus on 2011-04-17
You have to click the green "V" button for the operations to take place.

---

