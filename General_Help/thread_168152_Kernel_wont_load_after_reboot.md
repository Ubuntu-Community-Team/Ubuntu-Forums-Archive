---
title: "Kernel wont load after reboot"
date: 2006-04-29
forum: General Help
---

### Post by chapium on 2006-04-29
Sorry for cross-posting this, but the last topic I had for this got buried, and was probably in the wrong forum anyways. Here's the issue:


I get the following error every single time i reboot and choose ubuntu from Grub:

```

Uncompressing Linux...
     crc error
--system halted

```

This doesnt happen if I cold boot.  How can I fix this?] (*,)

---

### Post by yager on 2006-04-30
A google search turned up some scary info.  All 4 articles I read stated that the problem was most likely a hardware problem with a bad sector.  In one article, the writer confirmed that the disk was in the process of failing.  The only other option offered was that the install got botched or the kernel became corrupted and therefore needed to be replaced.  Since you can cold boot, the corrupted kernel can't be the problem.  Get thee to the local computer store and pick out a bigger hard drive fast.

When you say cold boot, how cold are you talking about?  1st start of the day after spending the night turned off?

---

### Post by chapium on 2006-05-01
By cold boot I mean turning the power off and turning it back on.  

Fortunately I've got a spare hd nearby and ready.  

It might be worth noting, I also have Slackware installed and I do not get these errors.  I think Ubuntu has been doing this ever since it was installed.  I've tried reinstalling the kernel (which really freaked grub's graphics out upon the next boot), but that didnt seem to make much difference.

---

### Post by yager on 2006-05-02
[QUOTE=chapium]I also have Slackware installed and I do not get these errors.  I think Ubuntu has been doing this ever since it was installed.  I've tried reinstalling the kernel (which really freaked grub's graphics out upon the next boot), but that didnt seem to make much difference.[/QUOTE]

Look at this thread to see some info on fsck.  This may be what you need to solve your issues.  The key is to not mount your partition before checking the drive.

[http://www.ubuntuforums.org/showthread.php?t=165750&highlight=fsck](http://www.ubuntuforums.org/showthread.php?t=165750&highlight=fsck)

fsck may detect some bad sectors on your drive that sit directly underneath the kernel file.  If so, you could mark out those bad sectors and then reload the kernel onto the drive.  You may need an install disk if you have to go into a recovery mode so have that handy before you start.

As a note, I am not an expert with fsck.  More experienced users will need to help out here.

---

### Post by wylfing on 2006-05-02
Another potential reason to get this kind of problem is bad memory. I have seen that before, especially when you've purchased the cheap memory (we all do it, but you get a bad stick now and then). 

Get yourself a Live CD, boot on it, and run the memory tester. It's not the same as your BIOS "memory test" -- it's a quite thorough regimen that puts your memory through a lot of paces. 

After that you'll know if your memory needs replacing or your hard drive is failing.

---

