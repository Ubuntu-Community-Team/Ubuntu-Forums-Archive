---
title: "Init not found error when booting from CD"
date: 2011-09-24
forum: General Help
---

### Post by mao3 on 2011-09-24
Hey, so I was upgrading Ubuntu from 10.1 to 11.4, and everything seemed to be going well, I left my computer for a few hours, and then I could no longer boot into Ubuntu, I'm not sure it finished installing at all.  

Anyway, I was cool with it, thinking I could just log onto windows, delete the ubuntu volume, and install ubuntu again.  So, I had to go after my blank CD failed to properly burn the disk image, so I put my computer on hibernate, not realizing this would prevent me from ever getting to log back into windows because it tries to boot from the grub menu, which no longer exists since I deleted the volume it was on.

 The solution seems to involve booting from a Ubuntu Live CD, which I didn't have and could not download, not being able to access my Windows 7 OS and all.  So I had a friend burn a live CD for me, and I booted from it, and ended up getting the init not found error...what should I do?  People who posted on this forum about the init not found error did not get this from trying to boot from a Live CD and they were all told the solution was to boot from a live CD, so what do I do when the error occurs when booting from a CD?

---

### Post by ajgreeny on 2011-09-24
Are you sure the CD your friend burned is a good one;  was the iso file good to start with and did it burn properly to the CD?

---

### Post by mao3 on 2011-09-24
I'm going to assume it was not a good one, I fixed my problem by using a windows partitioning wizard pro cd I had, it gives you the option to rebuild MBR, and it worked.  I am now installing ubuntu 11.04, but I'm worried because when I boot from CD, I get a bad lun, bad target number error, so I think I'm going to resort to installing an earlier version, especially since trying to update from an earlier version last time went so horribly wrong.

---

