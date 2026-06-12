---
title: "Wine 'C' drive not big enough"
date: 2009-10-05
forum: General Help
---

### Post by McChubs on 2009-10-05
I've been downloading/installing WoW via Wine and had to stop at 89% or so to restart my PC. Now the WoW installer informs me I don't have enough space to continue. Is there any way to increase Wine's share of the disk space?

---

### Post by CatKiller on 2009-10-05
That really rather depends on how you've got your partitions set up. Wine applications are stored in your Home directory, in ~/.wine. If you've got a separate /home partition, you could make that bigger. If you're just using a single filesystem for Ubuntu, you could make that bigger by taking some space from another partition. You can do either of those from a live cd. If you've used Wubi, then you've created a file on an existing partition to use as a filesystem for Ubuntu and you should have made it bigger - I have no idea how to correct for that since I've never used Wubi. If you've got another partition somewhere else you can symlink your ~/.wine to somewhere on that other partition.

Those are all the options I can think of at the moment.

---

### Post by McChubs on 2009-10-05
I did it through Wubi as Ubuntu wouldn't recognise my disc drive. I can't actually remember what I set Ubuntu's partition at, though it is on a 160GB partition of its own. What's annoying is, the installer obviously does fit, but instead of checking over the files and continuing on to download the last bit needed, it's whining about not enough disk space.

---

### Post by XCan on 2009-10-05
I thought Wubi was limited to 10GB.

---

