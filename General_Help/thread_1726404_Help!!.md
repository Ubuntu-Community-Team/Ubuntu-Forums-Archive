---
title: "Help!!"
date: 2011-04-11
forum: General Help
---

### Post by chuning on 2011-04-11
I recently installed Ubuntu 10.10 on a new Windows 7 laptop - I use Ubuntu out of preference, but need to keep Windows for one bit of software that I use.  Then I started messing around with Ubuntu Studio, but then wanted to go back to just Windows and Ubuntu 10.10.  As it's a new computer with nothing of any consequence stored on it, I used the restore discs that I made when I first set up the computer.  Everything loaded apparently without problem, but now when I start up the computer it comes up with "error: no such partition. grub rescue"

Can anyone tell me how to sort this out?

Thank you 

Chris

---

### Post by deathadder on 2011-04-11
Sorry is that error when you select an option from the grub menu? Or is it just shown?

If the former, have a look here: [http://ubuntuforums.org/showthread.php?t=1359802](http://ubuntuforums.org/showthread.php?t=1359802)

If the later, as I expect it is, it sounds like the rescue tried rewriting the MBR and failed. You can restore grub by using the [Recovering Ubuntu after Windows install]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") wiki page.

---

### Post by chuning on 2011-04-11
Yes, it was the latter

I've followed that link, and now everything is working!

Many thanks!

Chris

---

