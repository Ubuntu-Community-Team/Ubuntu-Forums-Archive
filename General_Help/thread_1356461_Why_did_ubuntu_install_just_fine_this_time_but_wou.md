---
title: "Why did ubuntu install just fine this time but wouldn't 8 months ago?"
date: 2009-12-16
forum: General Help
---

### Post by bomber991 on 2009-12-16
Well, last time I tried to install Ubuntu, I couldn't even get the live cd to actually boot up.  I couldn't get knoppix to load.  Couldn't get Suse to load. This was back in April with Intrepid Ibex.

I was able to get older distros to load at an earlier time.  The only hardware change I made since then was switching from an ide cd drive to an sata cd drive.

Anyways I just downloaded, burned, and successfully booted up into 9.10.  I then installed it and am typing this message on it right now.  So what changed between 8.10 and 9.10 that allowed ubuntu to load up properly?  I'm not too sure how linux works, but I guess one of those kernel updates probably fixed that problem I was having?

Here's the link to my old issue that seems to have just disappeared with 9.10:
[http://ubuntuforums.org/showthread.php?t=1123114](http://ubuntuforums.org/showthread.php?t=1123114)

Thoughts?  Comments?

---

### Post by zaphod777 on 2009-12-16
Just a guess but maybe it didn't have your SATA drivers.

---

### Post by Muflon on 2009-12-16
> **bomber991 said:**
> The only hardware change I made since then was switching from an ide cd drive to an sata cd drive.


You may have answered your own question.  If the only change made is that you use a different CD drive, then that may have been the problem.  It would be interesting to try one of the CD versions that failed previously with the new drive and see if that works.

Muflon

---

### Post by KeLa on 2009-12-16
I have on my windows box intel motherboard that has ide chip set version that won't work on linux. When i tried booting with linux live cd it didn't start until i put an SATA drive in there and used that.
The IDE chip was made by Marwell if i remember right. Anyway that chip is not supported by any linux distro.

---

### Post by bomber991 on 2009-12-16
> **Muflon said:**
> You may have answered your own question.  If the only change made is that you use a different CD drive, then that may have been the problem.  It would be interesting to try one of the CD versions that failed previously with the new drive and see if that works.

Muflon

Heh I think you misunderstood, or I'm so tired I typed it out wrong.

A long long time ago I tried to install 6.06 and it worked just fine.  I had an IDE cd drive then.  I tried to use ubuntu for about a month and then just gave up.  Anyways, fast forward to 8.10.  All my hardware was the same except for the sata cd drive instead of ide cd drive.  Couldn't get that one to work at all, or any other linux distros for that matter.  Now fast forward again to 9.10.  Hardware was the same as what I had when I tried to install 8.10, but it installed just fine with 9.10.

Anyways I'm happy with this and don't really plan on trying to install any other distros for the time being.

---

### Post by Magnes on 2009-12-16
There was a bug in newer kernels having something to do with SATA and IDE drivers. On some computers you had to wait a minute or moe for the kernel to detect drives and on some the drives didn't work at all. My DVD-ROM didn't work in Ubuntu 8.10 and Ubuntu 9.04. It works fine in Ubuntu 9.10.
The bug is still there for some people, but for most it's gone.

Search for busybox on launchpad.

---

