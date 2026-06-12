---
title: "whole partition occupied by absolutely nothing."
date: 2011-09-11
forum: General Help
---

### Post by Zephemeros on 2011-09-11
Hello, I recently installed ubuntu 11.04 64-bit on my machine, and everything was working great until a few hours ago.
I got a message saying that my hard disk is almost full, even though the os is newly installed and I have only about 1 or 2 GB of personal files on it at the moment.

My first partition on my HD is windows 7 64-bit (215gb), my second is ubuntu 11.04 64-bit (17gb) and my third partition is linux swap space (2gb).

when I open up the disk usage analyser, it tells me my user folder (the one named after my username) is where a MASSIVE 10gb file resides, which I never put there myself.
What's even more odd, is that when I open up my home folder in the file browser, I can find no such insanely large file and everything appears to be the way it should be. Yet I get a message on every startup that I only have 500mb of disk space remaining.

I've included a screenshot of the disk usage analyser and the problem I'm having, after all, a picture's worth a thousand words.

Any ideas? Corrupted partition maybe?

---

### Post by Habitual on 2011-09-11
```
sudo fdisk -l
```

output here please.

---

### Post by Zephemeros on 2011-09-12
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4e8f4e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28113   225814336+   7  HPFS/NTFS
/dev/sda2           28114       30140    16281877+  83  Linux
/dev/sda3           30141       30401     2096482+  82  Linux swap / Solaris


Funny thing is, I recently restarted my system and now everything seems to be working correctly. I have 4.6 GB used and 10.7 GB available space like I should, despite the fact that ubuntu would not start up normally before and I only had a supposed 550 or so MB of disk space left.

weird..

---

### Post by hawthornso23 on 2011-09-12
Are you sure you installed to the partition and didn't do a WUBI install by mistake. 

A WUBI install puts the whole of ubuntu into a file system stored in a file in windows. It is limited to - I think - 12Gb. WUBI is intended to let people try ubuntu before they make big changes to their system, but it is not uncommon for people to choose the wrong option in the installer and get a WUBI installation when they meant to install to a partition.

---

### Post by Zephemeros on 2011-09-12
No, I'm pretty sure it's a normal install as I created an ext4 partition and swap space with gparted and then installed ubuntu on to it by booting into a live cd.
I don't seem to be having the problem anymore anyways for some mysterious reason, Maybe it's a bug of some kind that I experienced?

---

### Post by Wim Sturkenboom on 2011-09-12
I'm pretty sure that there was another thread within the last week or so that reported the same issue; might be on another forum.

---

### Post by CatKiller on 2011-09-12
> **Zephemeros said:**
> when I open up the disk usage analyser, it tells me my user folder (the one named after my username) is where a MASSIVE 10gb file resides, which I never put there myself.

No it doesn't. It says that the entire usage of your Home folder when everything's added up is 10 GB. It's possible that it's one massive file but it could just as easily be lots of smaller files instead. There's no reason to assume that it's the former rather than the latter.

---

### Post by Zephemeros on 2011-09-12
> **CatKiller said:**
> No it doesn't. It says that the entire usage of your Home folder when everything's added up is 10 GB. It's possible that it's one massive file but it could just as easily be lots of smaller files instead. There's no reason to assume that it's the former rather than the latter.

I was simply using one gigantic file as an example, you are completely correct in that if that much space was actually being taken up, it could have been taken up by various smaller files as opposed one large one. It seems to be some sort of glitch anyways, so it does not matter.

---

