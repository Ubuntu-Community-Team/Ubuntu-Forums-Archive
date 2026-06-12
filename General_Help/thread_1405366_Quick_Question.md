---
title: "Quick Question"
date: 2010-02-12
forum: General Help
---

### Post by Captjac91 on 2010-02-12
Hey guys just a quick question for you, right now i'm Dual-operating vista and Ubuntu but i want to turn my computer over completely to ubuntu,and remove vista. how should i go about doing this?

---

### Post by bluelamp999 on 2010-02-12
What I would do is just reinstall Ubuntu (via CD, USB stick, whatever) and select to partition/format the whole hard disk for Ubuntu. A nice clean start...

That's just my $0.02, there may be other options...

---

### Post by Captjac91 on 2010-02-12
Right but by doing that i would lose all my programs that i currently have running on ubuntu, i mean if i must do it that way then i will but i would rather not have to do it that way.

---

### Post by SchizmWolf on 2010-02-12
Well, if you're somewhat experienced with computer know-how, I'd suggest that you download a Gparted livecd. Pop that into your computer and restart, telling it to boot from CD drive. After that's it's fairly intuitive: just tell it to resize/reformat the existing partitions into blank partitions that linux can use (you'll want swap and ext3 formats), then boot Ubuntu from CD, choose manual partitioning, and allocate the various directories to your freshly reformatted partitions :3

Oh, also, if you're trying to keep your programs, I recommend doing a total backup onto an external and perhaps try working with AptOnCD, though that wouldn't truly be preserving your programs, just archiving and retrieving all the programs you currently run. Hope that helps!

---

### Post by Captjac91 on 2010-02-12
well i have gparted currently installed on my computer but how would i install it onto a livecd?

---

### Post by SchizmWolf on 2010-02-12
> **Captjac91 said:**
> well i have gparted currently installed on my computer but how would i install it onto a livecd?

Download the LiveCD iso from the Gparted site, then use a program such as Brasero or K3b to burn the image to disk. That'll make a working LiveCD.

---

### Post by Captjac91 on 2010-02-12
Thanks so much i'll try that

---

### Post by SchizmWolf on 2010-02-12
No problem. If you need any help with the partitioning or have any other questions, feel free to ask!

---

