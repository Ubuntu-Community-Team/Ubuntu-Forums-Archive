---
title: "cannot delete partition, initramfs problems"
date: 2011-08-06
forum: General Help
---

### Post by KFwLsKvVAs on 2011-08-06
Hello, I am having trouble accessing my computer after abruptly shutting it down because it was booting off of a live CD and I just wanted it to boot of the HDD.  

When I try to boot up from the normal HDD I used to get a lot of errors about /dev/sda being not found, and then it went to an (initramfs) prompt, from which I could do pretty much nothing.  I booted into a live CD, and basically I didn't need any of my data so I wanted to just get rid of the problem partition and reinstall.  I attempted to delete the partition, but that didn't work, saying something about /dev/sda being busy (even though I had booted from a live CD and had not mounted the partition).  Anyhow, now when I try to boot from the HDD I get "error: no such partition.  grub rescue>"

Basically what I'm trying to do is just get rid of this partition and reinstall, but I keep getting errors about it being busy and not being able to delete the partition.  Is there someone with a way to allow me to just blast this partition and reinstall?  I've got a windows 7 partition on the same HDD and I'd really like to leave that one alone, but the ext4 and swap partition can just go.

---

### Post by wildmanne39 on 2011-08-06
Hi, from the livecd you should be able to use disk utility or gparted to unmount the partitions, then it should work.

I imagine you have bad sectors on your drive.

---

### Post by KFwLsKvVAs on 2011-08-06
Nevermind, I found a somewhat not elegant solution to my problem.  I put in a Windows 7 install DVD, tried to install (so that it would format and then I could just cancel it midway), but it failed.  Anyhow I put in the Ubuntu 10.10 live CD and it did not say that it was busy anymore, and I was able to install with no problem.

---

### Post by wildmanne39 on 2011-08-06
Hi, that good,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by slc1185 on 2011-08-09
1. For all intensive purposes we can assume I'm completely new to Linux based OSes

2. I'm also new to this Ubuntu Forum and am really sorry if i'm posting in the wrong place

3. My issue: I was trying to clean up my Dell Inspiron 1545 (getting rid of my Kubuntu and Windows partition, reinstalling Windows). I was using GParted to do the job and had just finished wiping Windows and Kubuntu and reformatting. Was ready to exit and reinstall Windows when curiosity got the best of me and I started wondering what would happen if I deleted the 100mb system reserved partition. Well, that was a bad idea.

4. I can no longer access BIOS, I can't boot off of my Windows7 install. disc, most of these actions result in a terminal-like environment:

error: no such partition.
grub rescue>

My GParted disc, however, is still entirely useful...?

5. I'm a tad confused and would be very appreciative of a solution, or at the least, an explanation.

Thank You.

---

