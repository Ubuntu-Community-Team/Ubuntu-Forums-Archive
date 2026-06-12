---
title: "Understanding of bootstraping process (from bootloader's view)"
date: 2010-10-18
forum: General Help
---

### Post by SkyerSK on 2010-10-18
Hello,
I spent few hours trying to get clear view of how exactly booting process goes, meaning it from bootloader's view (grub in my case).

Please, let me tell you what I know, correct me if I'm wrong. (I'll ignore things that I'm not focusing at).
1. Computer starts, BIOS defines (BIOS's setup at all) which drive or medium will be searched first.
2. On disk, there is (always?) MBR sector, which can specify which system to load, or point to some other place on disk, where other files of bootloader are (more complex bootloader case).
3. After choosing operating system, computer jumps to it's partition (also bootloader's files should be on some partition, mostly same prtn), and boot it.

Is it correct? except grammar mistakes, I'm not speaking English nationally.

Another question: How is it possible to make grub load twice? I mean, for example, if I select SUSE, it shows another grub again. (The one which came with it). Both systems and GRUBs are on same hard drive, while Ubuntu's grub should be in MBR.

(It actually doesn't happen to me, but I heard of it, so I'd like to know why exactly it happens.)


Thanks for answers. Hope it makes any sense, and I didn't make  you too bored. :)

---

