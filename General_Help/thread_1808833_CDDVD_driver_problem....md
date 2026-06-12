---
title: "CD/DVD driver problem...?"
date: 2011-07-20
forum: General Help
---

### Post by ajr893 on 2011-07-20
Hey, all, I'm relatively new to ubuntu. I had a computer running ubuntu that crashed about ten months ago. I got a newer computer for free - an HP dc7100 SFF - and threw Ubuntu on to it a few weeks ago, but I've hit one snag.

The CDRW/DVD drive does not work. It shows that it has power, opens, closes, blinks the green light to show that it is reading the CD or DVD, but the operating system is completely unaware that it exists. I cannot see the CD drive in my places, and it does not come up with anything useful when I ask it to give me the name of the CD drive using this command:

dmesg | grep cd

The computer can see the floppy drive just fine. I pulled out some old diskettes to test it, and it works just fine.

I've been tinkering with this for about a week, now. I've tried looking for drivers... my second guess at what the problem is that maybe the operating system just never mounted the drive. I haven't seen anyone else on the forums with the same problem, at this point. If anyone could offer any advice or assistance, I would really appreciate it.

Tech specs on the computer:
2.8 ghz Intel Pentium 4 CPU
Integrated GPU
1.5 GB of RAM
40 GB HDD
CDRW/DVD Drive 
3.5" Floppy Drive

Nothing impressive, but it's something to get the job done. :)

Have a sizzlin' day,
AJ

EDIT:
I'm sorry, I should have mentioned that I am using Ubuntu 11.04 Natty Narwhal Desktop Edition.

---

### Post by MG&amp;TL on 2011-07-20
Hmmm. Is that the original cd drive that came with the pc? You might want to check for loose cables. Best suggestion at the moment I'm afraid. :(

I love it when people say their computer has a floppy drive. It makes me feel slightly less outdated. :)

---

### Post by raja.genupula on 2011-07-20
[http://ubuntuforums.org/showthread.php?t=1468035](http://ubuntuforums.org/showthread.php?t=1468035)

---

### Post by wildmanne39 on 2011-07-21
Hi, make sure that you have a readable disk in then look in places and see if it is there. If not it may not be getting mounted.

Open disk utility and see if it is there and try to mount it.

---

