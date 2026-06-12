---
title: "Installed Windows 7 Pro and Wubi fragments remained. Can I set up Wubi again?"
date: 2010-04-30
forum: General Help
---

### Post by jmacg on 2010-04-30
I had XP with Wubi/Ubuntu 9.10 running on my office desktop. When I upgraded XP to Windows 7 via a clean install, I expected Wubi/Ubuntu to be wiped altogether. I intended to install it again later.

That's not the way it worked out. Some of the Wubi/Ubuntu got wiped, but not all. And the computer still boots up showing the dual boot screen.

I want to install Wubi/Ubuntu again, but is there any danger in doing so when bits of the old installation are still floating around? 

Also, I would be installing Wubi with the newer 10.4 version of Ubuntu - would this cause even more problems?

---

### Post by Ultra_Man on 2010-04-30
What you're seeing is grub, a boot manager for linux. It basically overwrites the windows boot manager when you install a linux distro. To get rid of it, you need to go use your windows cd and use fixmbr.

---

### Post by jmacg on 2010-05-01
> **Ultra_Man said:**
> What you're seeing is grub, a boot manager for linux. It basically overwrites the windows boot manager when you install a linux distro. To get rid of it, you need to go use your windows cd and use fixmbr.

Thanks Ultra_Man. I intend to have Wubi and Ubuntu 10.4 again on the computer, so do I need to get rid of Grub? 

What would happen if I did the following: use the Windows file manager to delete all traces of Ubuntu on my hard drive, then do a new install with Wubi. I'm assuming that getting rid of the old Ubuntu wouldn't cause problems, because it's not as if any of it will be registered in the Windows 7 Registry. I guess the only problem would be if the new Grub installed by Wubi would conflict with the old Grub that is still there - or would it just neatly over-write the old Grub?

---

### Post by Ultra_Man on 2010-05-01
There shouldn't be any traces of ubuntu if you did a clean install, in which you should have reformatted the partition.

And wait...you shoudn't have grub when you use wubi, so you just need to use some software and edit what boots in your computer.

---

### Post by jmacg on 2010-05-01
> **Ultra_Man said:**
> There shouldn't be any traces of ubuntu if you did a clean install, in which you should have reformatted the partition.

And wait...you shouldn't have grub when you use wubi, so you just need to use some software and edit what boots in your computer.

Ultra_Man - I put you wrong. Remembering now what I did with that computer, it wasn't a clean install that would have reformatted the partition. It was an upgrade from the Windows 7 RC1 that was already on it, to final release Windows 7 Pro. According to Microsoft's FUD, this wasn't an option, but I tried it and it worked fine, and continues to work fine after several months.

Because it was done as an upgrade, that explains why at least some of my Ubuntu stayed there - including the Grub dual boot message.

Ideally I'd like to continue having Win7 and Ubuntu on that computer. I could try the utility you said comes with Windows, to get rid of Grub. But why would I want to if I want to continue having a dual boot system, installed with the latest version of Wubi?

But Wubi would be installing a newer version of Ubuntu than was there before. Is this likely to be a problem if I just ran Wubi, or would it be best to first of all use Windows Explorer to find and delete Ubuntu files that remain on the hard drive?

---

### Post by Ultra_Man on 2010-05-01
I'm sorry too, because I said there was a grub when there wasn't. When you use wubi to install ubuntu there is no grub installed. It just adds ubuntu as a boot entry in the windows boot menu.

So, you can install ubuntu using wubi again, but the first entry will still be there. So you need to find an app that can edit boot entries. I used one a while ago, but I don't remember what it was called.

---

### Post by jmacg on 2010-05-01
> **Ultra_Man said:**
> I'm sorry too, because I said there was a grub when there wasn't. When you use wubi to install ubuntu there is no grub installed. It just adds ubuntu as a boot entry in the windows boot menu.

So, you can install ubuntu using wubi again, but the first entry will still be there. So you need to find an app that can edit boot entries. I used one a while ago, but I don't remember what it was called.

I'll look around for such an editor. But do you have any thoughts on my question about whether it would be safe/advisable to delete Ubuntu stuff that's still on the drive before I reinstall with Wubi?

---

### Post by Ultra_Man on 2010-05-01
I don't think it matters. You prolly should I guess, since its going to clutter your harddrive.

---

### Post by radicalbehavioristman on 2010-05-22
I know this is an old message board. However I had a very similar experience. I found that some boot manager was still there. I found a program called Easy BCD. It was a piece of freeware.

---

### Post by bsm1th on 2010-06-06
Best program I've seen to edit boot entries is EasyBCD. It's even free, never seen that in a Windows program before :>

Bob <bsm2th@gmail.com>

---

