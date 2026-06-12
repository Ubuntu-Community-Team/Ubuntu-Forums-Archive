---
title: "Errors found while checking disk drive for /"
date: 2010-06-10
forum: General Help
---

### Post by whalogreg on 2010-06-10
I've recently (since upgrading to 10.04) been having errors while starting Lucid. When (usually after running any kind of video, or running firefox, I haven't quite narrowed it down yet) I try to shut down my laptop (Gateway MD7818u), the window with the option to confirm or cancel the shutdown or restart comes up completely blank, no buttons, but if I do hit enter it responds correctly. After this, during the plymouth splash screen I get an error message stating "Errors found while checking disk drive for /" and it gives me an option to manually fix these errors. When I do so it drops me to a root command prompt and says "Root filesystem check failed" and suggests I run fsck, which I do. The errors found are...

Inodes that were part of a corrupt orphan linked list found.
Block bitmap differences.
Free block counts were wrong.
Inode bitmap differences.
Free inodes count wrong.

and after each one, opts to fix each error.

When all is said and done, this seems to boot and operate normally, but  has happened a number of times now. I'm afraid that this might be a hardware failure problem (HD or memory), but am not sure... Any ideas?

---

### Post by whalogreg on 2010-06-12
I'm fairly sure that this problem is caused by totem. This problem usually happens after I've been watching video with totem and the video freezes (can't play, pause, seek.. ect). I've been using VLC to watch video since my last post and haven't seen this problem since. Any ideas why totem might have this effect?

---

### Post by dino99 on 2010-06-12
open synaptic repo and deactivate the cd-rom repo if any

can also clean the system with gconf-cleaner (yes to all)

---

### Post by prodigy_ on 2010-06-12
> **whalogreg said:**
> When all is said and done, this seems to boot and operate normally, but  has happened a number of times now. I'm afraid that this might be a hardware failure problem (HD or memory), but am not sure... Any ideas?

First, just run Disk Utility (System/Administration/Disk Utility) and see if the SMART status of your HDD is ok. Also check Reallocated Sectors Count SMART parameter. Basically that's the new name for what was previously known as "bad sectors". So if this parameter value is higher than zero, your drive isn't reliable anymore.

For a more thorough test, go to your HDD vendor website and and d/l a test utility. (Even if they don't have a version for Linux, usually there's an option to d/l a boot CD image from where you can run the test).

---

### Post by whalogreg on 2010-06-12
> **prodigy_ said:**
> First, just run Disk Utility (System/Administration/Disk Utility) and see if the SMART status of your HDD is ok. Also check Reallocated Sectors Count SMART parameter. Basically that's the new name for what was previously known as "bad sectors". So if this parameter value is higher than zero, your drive isn't reliable anymore.

For a more thorough test, go to your HDD vendor website and and d/l a test utility. (Even if they don't have a version for Linux, usually there's an option to d/l a boot CD image from where you can run the test).

I ran Disk Utility and I got two errors.
First as "Airflow Temperature" and the second was "Current Pending Sector Count". Both had tooltips that said they were a "sign of old age" (laptop is about 1 and a half years old). As far as "Reallocated Secotrs Count" I didn't see anything of that nature, but I did have a "Bad Sectors" section, which has two. I'm assuming it's the two errors I previously mentioned. 

I've read, more than once, that some people have had ext4 problems. I installed in ext4 (by default). I wonder if this has anything to do with my problem.. I have LinuxMint installed on an ext3 partition, and although I rarely use it, I have not met this problem using Mint.. Could the ext4 possibly be the culprit here?

---

### Post by prodigy_ on 2010-06-12
Generally, if an HDD has any bad sectors at all, it's better to replace it immediately.

But re-check your drive first (with a different software) to be sure. Disk Utility sometimes shows false positives and it'd be a bit silly to replace a working drive. Simply install and run GSmartControl for that:

```
sudo apt-get install gsmartcontrol
sudo gsmartcontrol
```

---

