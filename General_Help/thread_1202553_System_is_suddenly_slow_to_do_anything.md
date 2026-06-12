---
title: "System is suddenly slow to do anything"
date: 2009-07-02
forum: General Help
---

### Post by ham213 on 2009-07-02
Hello all.

I am running Ubuntu 9.04, whiuch was upgraded from 8.10.

About a week ago, my system started running very slow compared to previous speeds.

It loads the desktop slow (about 40 or so seconds as opposed to about 5 before).

It also is slow to launch applications; some longer in time than others.

It is slow to save files from my email attachments in both Evolution and Thunderbird, and is slow in saving files when they are edited.

I am also noticing a significant slowing in opening the Computer window in Places, and other windows to view the other drives in my system (both ext3 and NTFS volumes)

I also seem to have lost the use of my USB ports for some reason.

All of these work fine when I boot into M$ Winblows XP, so I am starting to believe that the hardware is not faulty.

I love Ubuntu, and have been using it since the 6.04 release. I have NEVER run into this kind of problem before and was hoping that one of you could help point me in the right direction to correct the issue.

Thank you in advance.

---

### Post by decoherence on 2009-07-02
Does the speed temporarily improve after a reboot?

---

### Post by ham213 on 2009-07-02
No, it certainly doesn't.

Neither rebooting or start-up from cold affects the slowness of the system.

---

### Post by Hangwire on 2009-07-02
Check out the System Monitor - which processes use most RAM.

---

### Post by ham213 on 2009-07-02
> **Hangwire said:**
> Check out the System Monitor - which processes use most RAM.

Here's the information in the System Monitor:

Release 9.04 (jaunty)
Kernel Linux 2.6.28-13-generic
GNOME 2.26.1

Memory:       1.5GiB
Processor 0:  AMD Athlon (tm) 64 X2 Dual Core Processor 3800+
Processor 1:  AMD Athlon (tm) 64 X2 Dual Core Processor 3800+

System Status: Available disk space: 37.8 GiB


Processes:

Firefox          46.2 MiB
Nautilus         15.7 MiB
gnome-panel      15.0 MiB
python           10.8 MiB
python           7.5 MiB
trackerd         6.2 MiB
tracker-indexer  6.2 MiB
gnome-monitor    6.1 MiB



Everything else is using less than 6 MiB

---

### Post by decoherence on 2009-07-02
Do you see an improvement if you kill trackerd and tracker-indexer?

I've seen tracker-indexer get hung up and kill performance. Don't know about a fix -- I just junked it.

---

### Post by reeseslover531 on 2009-07-02
yea tracker has a ton of issues in Jaunty, also is there any chance that the hard drive might have had an error of some sort? Sometimes if the hard drives is messed up the OS will just thrash it before it will skip the sector, try running fsck on it.

---

### Post by ham213 on 2009-07-02
> **reeseslover531 said:**
>  . . . try running fsck on it.

I ran it and there are no problems detected in any of the passes.

I'm still at a loss as to why things are so slow.

Any other ideas?

---

### Post by ham213 on 2009-07-06
> **decoherence said:**
> Do you see an improvement if you kill trackerd and tracker-indexer?

I've seen tracker-indexer get hung up and kill performance. Don't know about a fix -- I just junked it.

Killing both of those has not made a difference.

Nothing that I have tried has made any difference.

I also tested the memory (1.5GB PC3200) both on this machine with Memtest86 and on a known-good motherboard.

Both test came out satisfactory.

As I mentioned before, all the hardware works fine with Winblows.

I am also still unable to use the USB ports in Ubuntu.

Anyone have another idea?

---

### Post by ham213 on 2009-07-07
Okay, found issues with two of the four drives in my system (not the filesystem drive)

They were both NTFS drives that were automatically mounted every time I logged in.

Once they were removed from the auto mount, the system recovered quite nicely.

Thank you for all of the ideas.

---

