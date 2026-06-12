---
title: "Triple Boot 9.10, XP and 7?"
date: 2010-01-19
forum: General Help
---

### Post by Norami on 2010-01-19
I need some hints, tips and help with my new adventure. I've decided to triple boot on my system, but I want to make sure it's feasible. I'm an intermediate Linux user, and still learning a lot, so any help is welcome!

Here's my set-up: I've got two 500GB hard drives, and a good amount of power to handle the OS's. I want to set-up Ubuntu as my main OS on a single hard drive. Then, I want to put XP and 7 on the second hard drive, side-by-side. Obviously, I would then want a bootloader to display an option at system start to pick either one. The reason I want all these is for gaming mainly, and Netflix. I've got old games that only work on XP, and some newer games are coming out that I'm sure will run better on Windows 7 (Starcraft 2 is going to be amazing!).

I found this documentation: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It's obviously for dual booting Windows and Ubuntu. My question is, can I triple boot Ubuntu, Windows XP and Windows 7? If so (and I'm positive I can) are there any good resources for the process?

---

### Post by wkulecz on 2010-01-19
Its pretty easy to set up grub to boot multiple Linux systems and a windows system, but dual booting different windows versions is a bit more problematic.

My advice: setup your dual boot windows first then if everything works right (the grub2 in 9.10 seems to be having lots of dual boot problems, use the search) install Linux last and you should end up with a dual boot to Linux or Windows and if you choose windows you should get the windows dual boot prompt for XP/Win7.

I set this up with 9.04 Kubuntu and Win7 RC1 32-bit and 64-bit, but 9.04 broke my windows boot, so I had to reinstall the 64-bit version, which of course broke the 9.04 boot which I then had to fix with the live CD and a grub re-install.  But since then its been fine, I didn't like Kbuntu but Kdenlive was stable enough to actually use, whereas it had been crash-o-matic on 8.04, 8.10, and 9.04 Ubuntu.  I liked 64-bit Windows7 well enough I bought it and upgraded to the 64-bit version of Vegas video editor (dedicated video editing machine).

Grub2 appears to make this much more difficult as everthing I knew about grub is now wrong.  In theory grub2 has an "osfinder" feature that automates multiboot when it works, but also found old systems I specifically didn't want to boot (kept the old partations around for their files until I was sure I'd moved everything I needed) on my 9.10 test install.  Grub2 also was broke for me initially but is was one of the easiest to fix issues where it didn't honor my BIOS's boot drive ordering.

--wally.

---

### Post by Jose Catre-Vandis on 2010-01-19
Install XP first, then Windows 7, then Ubuntu

Windows 7 will put its bootloader files on the XP partition, and show XP as an option in its bootloader (so at the end you should only get two options in Grub2, Ubuntu and Windows 7, then when you choose Windows 7 you get a choice of Windows 7 or XP. (You can always add a manual entry for XP in Grub2 if you wish)

Not sure how Grub2 copes with multiple HDDs, search the forum for help on this if things don't happen automagically.

---

### Post by oldfred on 2010-01-19
Windows combines boot into the one with the boot flag, so from windows you can choose which to boot. If you want to directly boot from grub there is a workaround.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Norami on 2010-01-19
Awesome!

Thanks for the suggestions. I'm going to start crackin on it soon!

---

### Post by n0dix on 2010-01-19
Remember that you can also have 4 primary partitions.;) Study well the proportion for each system and their sizes.

---

