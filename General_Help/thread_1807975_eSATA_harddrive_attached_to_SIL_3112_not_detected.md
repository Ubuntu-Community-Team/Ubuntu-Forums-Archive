---
title: "eSATA harddrive attached to SIL 3112 not detected"
date: 2011-07-19
forum: General Help
---

### Post by malfist on 2011-07-19
Hello,

I have an eSATA harddrive in an dock/enclosure attached to my laptop via a PCIMCIA eSata card.

This is the card: [SYBA SD-PCB-SATA SATA PCMCIA Card 2 x SATA]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815124012")
Which is a Silicon Image 3112 chipset. The chipset is supposidly supported by linux, and their website has SuSE drivers.

However, I cannot get the drive attached to it to be detected.
The hard drive is a 2TB Western Digital fully utilized by a single NTFS partition. Reformatting (if it would fix the issue) isn't a problem.  

How can I get my hard drive to be detected?

---

### Post by psusi on 2011-07-19
Does the controller show up in the disk utility?

---

### Post by malfist on 2011-07-19
No. But the SATA Host Adapter for the PCMCIA card shows up. The Harddrive Dock has USB and eSATA, when I use USB, everything works.

---

### Post by malfist on 2011-07-19
It seems that my enclosure is defective, and that monoprice (the resaler/manufacturer) is RMA a lot of these. So I guess that's solved.

---

