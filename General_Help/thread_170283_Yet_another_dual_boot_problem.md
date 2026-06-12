---
title: "Yet another dual boot problem"
date: 2006-05-04
forum: General Help
---

### Post by oskar.hermansson on 2006-05-04
Hello!

I have been using Ubuntu and Windows XP with dual boot before without problem, but this time it seems I've complicated things a bit.

I ran Ubuntu and Windows XP on two partitions on the same disk, booting with GRUB (probably installed in MBR). It worked fine.

Then I plugged in another disk (as slave, for what it matters) and installed Windows XP on one partition on the new disk. I was still booting with GRUB, but when i chosed Windows XP, it seemed as NTLDR was loaded, and then I could choose which of my two XP partitions to boot. It worked fine.

Then I installed Ubuntu on another partition on the new disk. Still booting with GRUB with another Ubuntu added to the list. Even this worked very well. I was able to boot all of my four systems.

Now for the tricky part. I decided to remove the first disk (master) and changed the new disk from slave to master. Now, still booting with GRUB, i was (of course) not able to boot my old Ubuntu system, but the new one worked fine. When trying to boot Windows XP the system finds no NTLDR and fails.

From this I figure GRUB is installed in MBR (am I right?) and the NTLDR was located somewhere on the old disk (?).

I have tried to add something like this to my menu.lst
```
title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
```
without success.

Any thoughts on how I should take it from here? I don't want my XP partition back at **any** cost, I still want GRUB to be my boot loader and my Ubuntu system to work :)

---

