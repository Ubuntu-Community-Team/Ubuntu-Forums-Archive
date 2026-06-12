---
title: "Swap file weirdness....."
date: 2011-08-23
forum: General Help
---

### Post by monkeypigs on 2011-08-23
Hi all, bit of a strange thing going on here that I don't quite understand but replicated on different machines. 

3Ghz Intel 4 processor (Single core) 2GB RAM are the basics of my main machine. 

Fresh install of 11.04, ] installed, [PHP]vm.swapiness = 10[/PHP] and fstab has [PHP]data=writeback[/PHP] added to the entry for the sole drive in the system. This was done a while ago with a good few reboots inbetween, 

The installation gave me a 2Gb swap

Ubuntu being as fantastic as it is, was being a little chuggy in places but not being CPU intensive nor using any of the swap.

Created an additional 2GB swap file to total 4GB, ubuntu is speedy and zipping along!

So, two things I guess really! First of all, if swap wasn't being used before or after, WHY did adding another 2Gb of swap make a jot of difference?

Secondly, (apart from the writeback and power outage issue) are there any downsides to the above tweaks applied and are there any more that you would recommend!

Many thanks
Iain

---

