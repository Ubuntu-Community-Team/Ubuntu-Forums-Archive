---
title: "Won't boot with CD-ROM installed"
date: 2011-01-08
forum: General Help
---

### Post by leifjonny on 2011-01-08
I have two IDE HDDs installed, and I'm trying to add an IDE CR-ROM drive. They all appear in the BIOS and their master/slave settings are OK, I've tried all possible configurations anyway.

Problem is when I plug in the CD-ROM drive and power on. Grub appears as normal. Then after the screen goes black for a while it jumps into an initramfs shell, complaining that the root partition could not be found. I have tried booting a live-cd from the CD-ROM, and it works.

The worst is that it has worked before, but when I moved to a new case I had too short cables so I left the CD-ROM drive unplugged. When I received my new cables it didn't work.

---

### Post by gordintoronto on 2011-01-08
It sounds like your CD-ROM is set to master and the hard drive is set to slave.

---

### Post by leifjonny on 2011-01-08
Right now I have it set to master on the secondary IDE bus alone. But really, I've moved it around and tried every viable combination. At first I connected the IDE cable upside down. I don't think this has damaged it though since I was able to start a Ubuntu live CD session.

---

