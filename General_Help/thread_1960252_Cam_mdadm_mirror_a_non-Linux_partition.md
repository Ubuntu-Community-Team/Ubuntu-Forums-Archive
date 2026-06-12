---
title: "Cam mdadm mirror a non-Linux partition?"
date: 2012-04-17
forum: General Help
---

### Post by ladasky on 2012-04-17
Hello again,

A few minutes ago, I _[posted about the failure of a RAID1 setup]("http://ubuntuforums.org/showthread.php?t=1960251")_ I built, using my AMD motherboard's BIOS-based RAID controller.  I did this because I needed Windows.  On the Linux side, I used **dmraid**.  It worked for several months.  I have reason to believe that I can't put Humpty Dumpty back together again.

Now, even though I would like my Windows partition to be mirrored in real time, when I'm booted into Windows, I can possibly live without it.  I have used **mdadm** in the past, with success.  Would it be possible to get Linux to mirror my Windows partition?  I could still have a crash from within Windows, and lose data there, but I boot into Linux far more frequently anyway.  My mirror would never be that far behind.

Thanks for any advice!

---

### Post by ladasky on 2012-04-17
One bump for the daytime readers...

---

### Post by SeijiSensei on 2012-04-17
You can use mdadm to bind the partitions together, then install an NTFS filesystem on top of the array.  However I don't know if you could boot XP from the array.  In principle, it might be possible if the array is started by grub before XP is booted, but I think this is a question that you can only answer empirically.

I think you might find it easier to have just have a matching partition on a secondary hard drive that's formatted with NTFS and then use rsync from Linux to update the backup at boot.

---

### Post by ladasky on 2012-04-17
Thanks for your reply, SeijiSensei.

Over in _[another thread of mine]("http://ubuntuforums.org/showthread.php?t=1960251")_ (I broke my comments into parts when no one seemed to answer my _[earlier, longer post]("http://ubuntuforums.org/showthread.php?t=1958874")_), I just learned the about virtualbox, an open-source virtual machine for Linux.  I think that another way for me to solve my problem might be to reinstall Vista as a guest OS on top of Oneiric, and just let Linux handle the physical disk operations.

---

