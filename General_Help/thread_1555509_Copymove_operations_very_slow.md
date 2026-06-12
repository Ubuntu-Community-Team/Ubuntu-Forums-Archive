---
title: "Copy/move operations very slow"
date: 2010-08-18
forum: General Help
---

### Post by x-shaney-x on 2010-08-18
I have always noticed copying or moving large files takes along time, I thought it was pretty normal.
However, over the past couple of days I have been moving a lot of large video files (500mb to 1.7gb).

Doing this in nautilus is VERY slow, not so much via terminal but it really hit home when I was copying some from within windows 7.

Copying 5 different files (one at a time) took between 1 and 5 minutes each in nautilus.
Copying the exact same files in windows explorer, the smallest video took just 20 seconds and largest approximately 30 seconds.

Is this normal?

---

### Post by Ugluk on 2010-08-18
Of course, Ubuntu has a free NTFS driver version, which is junk.

---

### Post by x-shaney-x on 2010-08-18
I meant when copying/moving on the same filesystem.
On lucid it's ext3 but it is just as slow on maverick ext4

---

### Post by mcduck on 2010-08-18
> **x-shaney-x said:**
> I have always noticed copying or moving large files takes along time, I thought it was pretty normal.
However, over the past couple of days I have been moving a lot of large video files (500mb to 1.7gb).

Doing this in nautilus is VERY slow, not so much via terminal but it really hit home when I was copying some from within windows 7.

Copying 5 different files (one at a time) took between 1 and 5 minutes each in nautilus.
Copying the exact same files in windows explorer, the smallest video took just 20 seconds and largest approximately 30 seconds.

Is this normal?

It depends, if you only have a one Windows partition, then copying/moving files inside it doesn't actually copy/move anything, the file stays where it is on the disk and only the information about where it shows in your file system hierarchy is changed.

Same goes for copying /moving file inside single partition in Ubuntu.

On the other hand if you copy something *between* different disks/partitions the file really has to be copied to the new location. And that of course takes a lot more time.

Also moving files that are on different partitions of the same disk takes longer than moving files from one disk to another, as the drive needs to seek between different locations of the same disk to read and write.

That being said, the NTFS support on Linux obviously isn't as good as it's on Windows. NTFS is Microsoft's proprietary file system and they sure haven't helped in making it usable on anything else than their own OS. Actually you are lucky to be able to use it at all...

---

### Post by satish_j on 2010-08-18
Check whether Assistive Technologies is enabled from system-->Preferences.If enabled,Disable it..
I faced similar issue which was solved after disabling AT..

---

### Post by Lilonius on 2010-12-21
This is a major drawback for me. I am forced to use xp at my work on my notebook for various reasons. Actually this is making me seriously think about having Win7 and turning my back to linux once and for good. I had to copy 220 mb of small file 500kb to 5mb from my NTFS partition to ext4 on my Ubuntu 10.10 partition. It was asking for 20 min in the beginning and dropping to 45- to 2 hours after short time. I tried to copy it to USB drive, thinking it is the same HDD and that will slow down the process. Nothing improved! I mean i have 4gb of ram, the OS could easily read those 220mb and pass them to RAM and write them on ext4 in seconds. I don't know how copying is done, but this is one crappy implementation that seriously destroys the image of Ubuntu. at least don't advertise it that it works with NTFS so users don't count on it.

---

### Post by gabak on 2011-03-28
i had the same problem , it was the sata data cable that was a little loose. then wow !! everything changed !!
if you solve ur problem plz let's know.
and change the status of this post to SOLVED

> **x-shaney-x said:**
> I have always noticed copying or moving large files takes along time, I thought it was pretty normal.
However, over the past couple of days I have been moving a lot of large video files (500mb to 1.7gb).

Doing this in nautilus is VERY slow, not so much via terminal but it really hit home when I was copying some from within windows 7.

Copying 5 different files (one at a time) took between 1 and 5 minutes each in nautilus.
Copying the exact same files in windows explorer, the smallest video took just 20 seconds and largest approximately 30 seconds.

Is this normal?

---

### Post by gabak on 2011-03-28
i had the same problem , it was the sata data cable that was a little loose. then wow !! everything changed !!
if you solve ur problem plz let's know.
and change the status of this post to SOLVED



> **x-shaney-x said:**
> I have always noticed copying or moving large files takes along time, I thought it was pretty normal.
However, over the past couple of days I have been moving a lot of large video files (500mb to 1.7gb).

Doing this in nautilus is VERY slow, not so much via terminal but it really hit home when I was copying some from within windows 7.

Copying 5 different files (one at a time) took between 1 and 5 minutes each in nautilus.
Copying the exact same files in windows explorer, the smallest video took just 20 seconds and largest approximately 30 seconds.

Is this normal?

---

