---
title: "File copying to usb stalls little before finish."
date: 2010-06-23
forum: General Help
---

### Post by supergrav on 2010-06-23
Hello, i am using ubuntu 10.04 x86_64. I'm having a certain problem while copying from my internal HDD (ext4) to usb stick (filesystem fat32). At first I get a good speed for the first half of the file (approx. 1.5 GB) and then it slows down but not significantly... 
The actual problem and my question is that when file transfer window informs me that 1.5GB/1.5GB have been transfered and 0 seconds remain, the window remains there for about 30 seconds. System is fully functional during this 30 sec but it seems to me that a task is being done that won't let me safely remove my usb stick when i try to. 
Any help or information would be helpful! Thanks!


I just realized that when copying multiple files, copying is stalled after each file being copied...

---

### Post by supergrav on 2010-06-23
Anyone? I'm just wondering if it's normal, hardware problem or configuration issue.

---

### Post by dcstar on 2010-06-24
> **supergrav said:**
> Hello, i am using ubuntu 10.04 x86_64. I'm having a certain problem while copying from my internal HDD (ext4) to usb stick (filesystem fat32). At first I get a good speed for the first half of the file (approx. 1.5 GB) and then it slows down but not significantly... 
The actual problem and my question is that when file transfer window informs me that 1.5GB/1.5GB have been transfered and 0 seconds remain, the window remains there for about 30 seconds. System is fully functional during this 30 sec but it seems to me that a task is being done that won't let me safely remove my usb stick when i try to. 
Any help or information would be helpful! Thanks!


I just realized that when copying multiple files, copying is stalled after each file being copied...

"Copying" is first done to your system cache and then the real copying is done to the device in the background.

What you are seeing is the cache being filled up quickly and then the real job of writing to the device happening at the actual write speed once the cache is full.

---

### Post by supergrav on 2010-06-24
Thanks for your answer! It's certainly logical what you say but I never noticed before such behavior while copying to same usb flash drives from my system running older ubuntu releases. It's just odd, it seems like OS is verifying written data...
Thanks again for your interest!

---

### Post by lumpy211 on 2010-06-26
I'm having this problem as well. Isn't the behavior you've described a little undesired? Other operating systems show the time until completion (i.e. the data is actually written to the disk), not the time until a buffer is filled up. Are there any tweaks that can be applied to show time until the process is actually completed instead?

---

### Post by mr_guy99493 on 2010-06-29
Same problem. Annoying isnt it. I want a fix too.

---

### Post by supergrav on 2010-06-29
I haven't came across anything usefull yet... Some people believe it's normal due caching. OK, and why I didn't encounter same behaviour in older releases? Why all of a sudden systems decides to inform me about the "imaginary" (caching) time and not the actual one as it did before? I think it has to do with mount options but I can't figure out what.

---

### Post by philinux on 2010-06-29
Is the problem the same as this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174)

If so feel free to click the affects me too, or add a comment.

---

### Post by supergrav on 2010-06-29
> **philinux said:**
> Is the problem the same as this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174)

If so feel free to click the affects me too, or add a comment.

It's more like this bug: [https://bugs.launchpad.net/ubuntu/+bug/599755]("https://bugs.launchpad.net/ubuntu/+bug/599755")
Actually it's not the same as the one you mention because it seems that write speed is quite fair (15-20 MB/s) constantly. Although I had the same issue as yours, after a kernel upgrade it went away.

---

