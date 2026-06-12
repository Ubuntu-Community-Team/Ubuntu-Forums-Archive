---
title: "System unreponsive during disk activity (9.10)"
date: 2010-03-15
forum: General Help
---

### Post by fwiffo on 2010-03-15
I have Karmic installed on three different computers (work, home and laptop), but on my home desktop there is a strange performance problem. During disk activity it sometimes becomes completely unresponsive. The mouse cursor doesn't even move. It actually seems fine when it first boots up, but it gradually gets worse as I use the computer for a while until it eventually becomes completely unusable. I'm only having trouble on the one system.

The drive in the system is SATA, and I already checked to make sure DMA was on. It is a x86_64 kernel. I tried adding noapic to the kernel boot line after some googling, but it seemed to have no effect.

Is there anything else I should try? Information I should post here to help diagnose it?

---

### Post by rsay on 2010-03-15
This recent post might help get you started.

[Disk IO causes computer to become extremely unresponsive]("http://ubuntuforums.org/showthread.php?t=1425875&highlight=Disk+IO+computer+extremely+unresponsive")

---

### Post by moongia on 2010-03-15
I had a issue like this this last week.I ran the memtest and every  thing was ok.So i just i did a fresh install,but the problem was still there.I have 2gb of RAM 512X4,I took out all of it and installed one and ran it,I did that for each one.Turns out one was bad.I hope this helps.

---

### Post by fwiffo on 2010-03-15
I'm running SMART tests right now, but is it possible that it could be hard-drive temperature related? I noticed I had a case fan that wasn't spinning (bearings seem to be shot - I'm about to get a replacement). The CPU and case temperature seem fine, but perhaps the hard drive is overheating. Would it produce these kinds of symptoms?

---

### Post by moongia on 2010-03-17
> **fwiffo said:**
> I'm running SMART tests right now, but is it possible that it could be hard-drive temperature related? I noticed I had a case fan that wasn't spinning (bearings seem to be shot - I'm about to get a replacement). The CPU and case temperature seem fine, but perhaps the hard drive is overheating. Would it produce these kinds of symptoms?

Not to sure about that one,my case is small with crapy air flow,and i have 2 hardrive mounted on top of each other,they do get hot but never had a over heating prob.but i did have a old hard drive go out on me,it would lock up with a squeal and a click sound from the drive.maybe try a spare drive to see if that works.

---

