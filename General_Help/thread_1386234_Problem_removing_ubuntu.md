---
title: "Problem removing ubuntu"
date: 2010-01-20
forum: General Help
---

### Post by kawakaze on 2010-01-20
Hi all,

Sorry for the title, I love ubuntu and it is staying on our two computers! Our daughter is taking our old laptop for school and compatibility with windows at 90% isnt good enough.

The problem is we forgot the password for the install, no problem I thought, just install windows over it. Wrong, Now both the windows installer and the ubuntu live cd (tried to format the disc on both methods) complain about a read only filesystem and bomb out. Windows will format but at 1% in 24 hours. We dont have 4 months to get this done!

I already tried most of the things I read on here, and now to make things worse the BIOS screen is giving a predicted smart failure, probably due to the failed formats and mangled drive contents, as far as i know the drive was working fine till i try to remove ubuntu

thanks in advance for any help.

---

### Post by synapsys on 2010-01-20
You can completely wipe the hard drive with dban.

[http://www.dban.org/](http://www.dban.org/)

Then install windows.

---

### Post by mk1w86 on 2010-01-20
Like the above poster said try DBAN first but if you still get SMART errors in the BIOS you could have a faulty hard drive.

---

### Post by HermanAB on 2010-01-20
Howdy,

You just need to zap the first bit of the disk to get rid of the partition tables and schtuff:
$ sudo dd if=/dev/zero of=/dev/sda bs=1M count=10

After that, Windows will think that it is a new blank disk and will install like normal.

PS: Google proved that SMART doesn't actually work, so turn it off.

---

### Post by PartsMan on 2010-01-20
Have you tried the Gparted live CD?

---

### Post by flabdablet on 2010-01-21
*PS: Google proved that SMART doesn't actually work, so turn it off.*

This isn't really right. SMART does indeed fail to predict certain disk failures, but if it shows that your drive has lots of reallocated sectors, or sectors pending reallocation, or has been run very hot in the past, you should certainly be looking to replace that drive.

---

