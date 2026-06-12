---
title: "Dual to Single Booting"
date: 2010-09-05
forum: General Help
---

### Post by QuestionsToAsk on 2010-09-05
Hi there,

I installed Ubuntu on my PC, that had Windows Vista before.
However, I wasn't sure wether I'd like it or not, so I decided to go for Dual Booting, and keep the Windows as well.
I'm convinced now that Ubuntu is indeed better, so I want to delete the WIndows as well.
Anyone knows how to do it? the options when I start are

Ubuntu, with linux 2.6.32-24 generic
Ubuntu, with linux 2.6.32-24 generic (repair mode)
Ubuntu, with linux 2.6.32-21 generic
Ubuntu, with linux 2.6.32-21 generic (repair mode)
Memory test (MemTest86+)
Memory test (MemTest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda2)

How can I delete the Vista? Do I need the Ubuntu, with linux 2.6.32-21 generic. If not, how can I delete that as well? thanks :)

---

### Post by Elfy on 2010-09-05
If you are _really_ sure that you wish to remove Vista then you can install gparted and remove the partition and reformat. You could either create a new partition and add it your fstab so it is available on boot for instance.

If you wish to keep vista - just in case - you can stop it appearing in the menu. 

I tend to keep current and previous kernel in my system. You can though if you wish remove kernels, open synaptic from the sys - admin menu and search for linux-image - look for the one you wish to remove and mark it for removal.

---

