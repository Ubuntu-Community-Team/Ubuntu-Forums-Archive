---
title: "some solution for slow starting of grub2 in 9.10"
date: 2009-12-10
forum: General Help
---

### Post by roozbeh on 2009-12-10
I was having this issue that when i restarted my computer, loading grub... took 6-7 seconds to finish then the graphical screen to choose operating systems started to show up.

I also did a search on this and i find out that some other peaple are having this.As far as i know, i found no solution for this.

This is what i find out for my configuration, maybe if you have the same configuration, it might help.

I have grub installed on my sda1 (first hard drive or hda1).
Linux root and home and swap are on other hard driver(sda2 or hda2).
(The reason is obviously that i am dual booting with another operating system, my case is windows xp)

well grub did took long time to start, but what i did was to run "sudo grub-setup /dev/sdb" which also installs grub on sdb1 meaning without the first drive attached to computer you can also start linux.

don't know why, but now grub starts immediately.

Hopefully if you have same config, this helps you.

---

