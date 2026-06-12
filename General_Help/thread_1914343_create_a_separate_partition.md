---
title: "create a separate partition"
date: 2012-01-23
forum: General Help
---

### Post by coldjeanz on 2012-01-23
Sorry to thread hijack but I have a question. When you select "Install side by side with Windows" did you create a separate partition before that? Or does that Ubuntu option automatically do it for you?

I'm just asking because I'm using the Wubi install right now and was wanting to switch to the real dual boot.

---

### Post by nipunshakya on 2012-01-24
> **coldjeanz said:**
> Sorry to thread hijack but I have a question. When you select "Install side by side with Windows" did you create a separate partition before that? Or does that Ubuntu option automatically do it for you?

I'm just asking because I'm using the Wubi install right now and was wanting to switch to the real dual boot.

Hi there. selecting "Install side by side with Windows"will create seperate partition automatically provided that you have free spaces in your hard disk. However, if you wish to use ubuntu as dual-boot and migrate from wubi stuff, i suggest you do manual partitions. **Its better for you to start a new thread that would include question about dual boot confusions. If you don't know how to partition, i would suggest you post an image of your current partition scheme so that we could help you out with partitions.**

Regards,WinuxUser

---

### Post by overdrank on 2012-01-24
> **coldjeanz said:**
> Sorry to thread hijack but I have a question. 

Moved your post to it's own thread. :)

---

### Post by Mark Phelps on 2012-01-24
If your Windows version is Vista or Win7, it's best NOT to use the slider to resize the Windows partition.  Doing so can lead to filesystem corruption, and if that happens, you will no longer be able to boot back into Vista or Win7.

In those cases, it is better to use the Windows Disk Management tool to shrink the OS partition.  It's primitive -- but it doesn't result in any filesystem damage.  And, after you do that, reboot into Vista/Win7 a couple of times to let the filesystem make any needed adjustments.

---

