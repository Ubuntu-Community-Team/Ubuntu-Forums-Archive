---
title: "First Installation"
date: 2010-06-29
forum: General Help
---

### Post by Ziton on 2010-06-29
I have a new  320gb sata II drive that I'm going to install win-xp-home & Ubuntu.
I also have Linux XP 2010 that I will install.
I'm going to use Gparted.
My question is , What's the best partition plan for multiple OSes?
320 GBs  is plenty of room to work with.
I'll have to use windows for my TV tuner cards till I get drivers for  linux.
What would be a good partition arrangement?
Thanks

---

### Post by Bucky Ball on 2010-06-29
All the OSs first, starting with Windows, data partition(s) next, Linux /swap last (your two Linux installs should be able to use the same /swap partition).

There is a wealth of info in my HOWTO: [HERE.]("http://ubuntuforums.org/showthread.php?p=7922209#post7922209")

---

### Post by Ziton on 2010-06-29
Thanks  bucky I'll look in HOWTO

---

### Post by Serpher on 2010-06-29
In simple terms, Linux can read Linux and Windows partitions while Windows can only read Windows partition. The format Windows uses is called NTFS. I have a 30G partition for Windows 7, a 80G partition for Ubuntu (EXT4 format), and the rest of the 500G drive is NTFS with no OS on it. This is because Windows breaks on account of it being garbage and requires it's partition to be wiped clean. I keep all my music, windows applications, movies, and pretty much EVERYTHING on the OSless NTFS partition. When I install an application on Windows, I do a custom install and make the instillation path 'D:\Apps\Google Chrome' for example. I suggest you do the same but XP is much smaller than 7 so 20G will do you fine. The extra space is just breathing room for your Desktop.

EDIT: Also I forgot, make a Linux Swap partition depending on how much RAM you have. It's just space on the hardrive your computer will treat like RAM if your RAM is all used up. I have 2GB and have another 2GB of swap space. IMO just subtract your RAM from 4 and the rest is your swap. Another under 0, don't make a swap partition.

---

### Post by Bucky Ball on 2010-06-29
I'd dual-boot myself, forgetting about the Linux-XP. Just dive in; you always have the XP install to fall back on as you make the transition. They are different ways of thinking about computing but achieving similar ends. Enjoy the learning curve! It's all about what suits, you might always have a Windows install handy for something, depending on your needs. Not better or worse, just what suits the purpose. ;)

And another good point in that last post. Windows will not see EXT3 or EXT4 partitions (Linux) so if you want to 'share' data between the two OSs (they can both access the partition) make those data partitions NTFS or FAT32. Linux can see both.

---

### Post by Abu Azzubair on 2010-06-29
[http://www.youtube.com/watch?v=PUZqF5fyrJo](http://www.youtube.com/watch?v=PUZqF5fyrJo)

I hope that link helps you

Just today (on another computer that I own) I got past all the stages to getting Windows XP ready to accept/make space for Linux Ubuntu 10.04

But when I came to boot from my mem stick, the computer was too old and never accepted/recognized the bootable mem stick Lol

It only knows how to boot Linux from a bootable CD...etc

I hope that helped a little : )

---

