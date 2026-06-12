---
title: "Freeze After Switching Video Mode During Boot"
date: 2010-10-08
forum: General Help
---

### Post by franziskaner on 2010-10-08
Hi Guys,
I just bought an Asus TS mini server. It has an Atom CPU (N280), and an Intel 945 chipset.

I installed Ubuntu Server Edition 10.04, that went smooth. 

But on first boot, I see it hanging just after it mounts the swap. Now I don't think it has anything to do with that, the problem seems to me that at that point, it also switches the video mode. I guess that's where the problem is caused. It just freezes, no kernel panic, no reaction to the keyboard.

I searched the forums, but don't get a clue.

The system is dual boot, and the other OS is Windows Home Server. I put an ext fs driver there, and tried to read the logs, but don't get a clue from there. In particular, syslog doesn't even exist. Also no X log.

Please help, I am clueless at this point...

Thanks...

---

### Post by franziskaner on 2010-10-10
The solution is to add 'i915.modeset=0' to the kernel parameters.

So for the novices: press 'e' when you're in your boot manager, and then find the words "splash quiet". Both of them are not what you want when you install a server, so purge them. Instead, add 'i915.modeset=0'.

Note that this fix applies only to system with an Intel chipset with integrated graphics.

---

