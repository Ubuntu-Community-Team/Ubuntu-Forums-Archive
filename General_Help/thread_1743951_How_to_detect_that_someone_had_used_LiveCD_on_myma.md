---
title: "How to detect that someone had used LiveCD on mymachine?"
date: 2011-04-29
forum: General Help
---

### Post by lemta2000 on 2011-04-29
Hello,
Is can be detect that someone had used a LiveCD on my machine if even they don't make any change on my hard disk?

Thanks!

---

### Post by Timmer1240 on 2011-04-29
I dont think you could tell because it doesnt touch the hard drive.

---

### Post by Thewhistlingwind on 2011-04-29
Only if they were sloppy and didn't change the boot order back.;) (As far as I know, anyway.)

---

### Post by srs5694 on 2011-04-29
I can think of two ways you *might* be able to detect this:


[list]
[*]If your system is kept up at all times and not shut down, then shutting down to use a live CD will change your uptime value. (Type "uptime" to see this.) This would obviously be useless if you shut your computer down and come back to it hours or days later and wonder if it's been booted in the meantime.
[*]The Ubuntu live CD accesses your swap space. If you suspected the computer had been used with such a CD, you could in theory boot with something that *doesn't* use the swap space and examine the swap partition for evidence that it had been used with the live CD. This would, however, require an in-depth knowledge of what might end up in the swap space from a live CD boot vs. a normal boot, and in fact I'm not even sure there are such "fingerprints." (I lack this level of knowledge myself.) Also, the evidence would be wiped out if you were to boot normally, unless perhaps you set aside a swap partition that your system doesn't normally use as a sort of "trap" for the live CD.
[/list]


If you're concerned about somebody using your computer without authorization, there are tools you can employ to add security, such as setting BIOS and GRUB passwords and installing case locks. No level of security is perfect, of course. Governments spend countless dollars (and Euros and Yen and whatnot) securing their sensitive computers, and they still suffer from leaks and espionage.

---

### Post by bergfly on 2011-04-30
Time for some good old analogue detective work. Is the keyboard or chair moved. Is the mouse moved. Greasy fingerprints, warm drives when you left it off, etc.

If they accessed or changed files while they were on it, you might be able to see that in the file timestamps. 
But basically, if they were really careful, it would be hard to prove anything.

---

### Post by bergfly on 2011-04-30
Just occurred to me if you are in a networked environment, especially a corporate one, there is a lot of checking you can do on the devices the machine would have hit in order to get up and running (DHCP leases, DNS queries, hitting the firewall) If you have a period you are suspicious of and access to these logs, there is proof it was on, but not who used it. If you are on a home network, and use OpenDNS or a router with logging or the like, you also have a trail there. When you think about it, it is really hard to run a computer undetected on a network

---

### Post by lemta2000 on 2011-04-30
Thanks everyone,
I also have a another question, if I use liveCD and then install lvm2 to mount a partition (linux lvm2 system file) on internal hard disk. so is this installation does not make any change on internal hard disk, too?

Thanks!

---

### Post by fdrake on 2011-04-30
.

---

