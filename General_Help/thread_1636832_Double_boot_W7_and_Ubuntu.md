---
title: "Double boot W7 and Ubuntu"
date: 2010-12-03
forum: General Help
---

### Post by arashiko28 on 2010-12-03
I'm trying to install W7 and ubuntu on a double boot, but for more than I try, w7 keeps self assigning the larger partition, when I want quite the opposite, how do I turn that around to make windows not to be that greedy? I need it for a minimum number of operations that can't be done not even virtualizing, so I had to install. I want it to bee at 30gb and Ubuntu partition into 2, 20gb for filesystem and the rest for /home. The ubuntu part, I hope I can do it as usual, the windows part is the one that worries me.

---

### Post by Mark Phelps on 2010-12-03
Win7 will not try to install to partitions that are not formatted NTFS.

So, if you really have a dual-boot, the "other" partition should be formatted for a Linux filesystem -- Ext2/3/4.

In my experience, when you install Win7 to a drive that already has an empty NTFS partition, you can tell Win7 to use THAT partition -- and it does so without problems.

Of course, if you already have Ubuntu installed, and you have a single physical drive, Win7 will overwrite the GRUB in your MBR and you will have to fix that later using an Ubuntu LiveCD.

---

### Post by Lordluen on 2010-12-03
Hi there. I'm new to this forum so I would not take my reply as complete truth. Anyway, I have found that if you install w7 first. Then install ubuntu, you can tell ubuntu to take as much as it wants. It will steal that from w7. So I would start by installing w7, giving it all the space. Then install ubuntu as a dual boot, and during installation choose the advanced option for splitting up your hdd. Then give it the space you want. I hope this helps and I have not completely missed the point! :p

---

### Post by arashiko28 on 2010-12-03
That is true, but in my case, I can't choose to make two partitions, more important, I'm already on the ubuntu install and guess what?? MY KEYBORAD DOES NOT WORK!!!!!! how on earth I am supposed to fix this on middle of an install?? naturally, I'm writting this from another computer.

but how I am to input my username and password with a completely useless keyboard?

---

### Post by arashiko28 on 2010-12-03
PLEASE!!! THIS IS A TRUE EMERGENCY!!! how do I get my keyboard back to work?? the install is hanging just waiting for my inputs!

---

### Post by oldfred on 2010-12-03
When I put a new motherboard in a couple of years ago, I had the same issue only just in Grub. It was a BIOS setting to enable USB keyboard & mouse.

Also for name you cannot have Capitals or special characters that will prevent it from letting you continue. That may be the issue also.

---

### Post by Lordluen on 2010-12-03
well now that is a unique problem. Is this a desktop or laptop? if it is a desktop, i would say try plugging in another keyboard, or just unplug the keyboard and put it back in. I can't imagine what would make the keyboard not work like that... 
If it is a laptop, then i don't even have advice. I imagine even if you plugged in a new keyboard, it might still try to use the built in native one. I guess I plead to more experienced users for advice on this...

---

### Post by arashiko28 on 2010-12-04
It is a laptop, I risked it all and just shut down the whole thing and then had to reinstall Ubuntu again, luckily it gave me than chance to do something I couldn't do the first time, that was making two separated partitions for ubuntu. Thanks for the concerns.

---

