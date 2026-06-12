---
title: "Recovering my UBUNTU JJ after Windows reinstall"
date: 2009-07-30
forum: General Help
---

### Post by qwertyx7ts on 2009-07-30
Hi there,

Im pretty new to linux (about 2 years of experience) and Ive got a really serious problem.
- using UBUNTU 9.04 Jaunty Jackalope 32bit stable relase

I had 2 OS in my computer. 1. Winshit XP and 2. UBUNTU
Then, i have to reinstall windows xp to windows 2000. I know that win had rewrited my MBR. So im gonna recover grub. I boot up from 9.04 LIVECD and tried to recover grub using this method ::

reinstall Ubuntu with live CD, marking the same partition as "/" without formatting

Everything went right, but when i got to partition manager, it shows that there isnt any partition (got 1 40GB disk , 10GB NTFS WIN and 30GB EXT4 Linux), just free disk.

Ok then. I had booted up again from live CD and tried to mount NTFS partition. Everything ok. :D
Then, i try to mount my EX4 Partition. Nothing. :(

So i went to terminal and tried to mount it manually using commands ::

sudo mkdir /mnt/root

sudo mount -t ext4 /dev/sda2 /mnt/root

and it shows error :( ::
wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error
 
What should i do???  :confused: :confused:

(sorry for my bad english, im from slovakia so...)

---

### Post by merlinus on 2009-07-30
Reinstalling grub does not require reinstalling ubuntu.  Perhaps the problem occurred when you selected not to format / on the reinstall.

At this point, if you have no important data in linux, it might be best to reinstall it into the sampe partition, and this time format /.

---

### Post by qwertyx7ts on 2009-07-30
i didnt reinstall it after all because the installation didnt find my ntfs partition and my linux partition. And, i have important files on linux.

---

