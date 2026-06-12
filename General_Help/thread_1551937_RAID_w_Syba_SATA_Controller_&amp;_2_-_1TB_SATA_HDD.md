---
title: "RAID w/ Syba SATA Controller &amp; 2 - 1TB SATA HDDs"
date: 2010-08-13
forum: General Help
---

### Post by mfdc1969 on 2010-08-13
So I have this plan to add a Syba RAID card to my machine and am hoping someone has advice to offer before I embark on this adventure??

I have a 6 year old [MSI MoBo that has NVIDIA RAID]("http://www3.telus.net/nature/MSIK8NNeo4.pdf") support, which I [understand to be FAKEraid]("https://help.ubuntu.com/community/FakeRaidHowto").

My understanding, from reading too many Google searches, is that using a Linux software RAID is good, but may put a demand on my CPU and hardware - I only have an Athlon +4000 2.40GHz single core, but 64bit processor.

So I thought I would maintain my OS on a SATA HDD plugged into the MoBo but add a [Syba PCIe card with RAID controller]("http://www.syba.com/index.php?controller=Product&action=Info&Id=5"). I would like to add 2 - 1TB SATA I HDDs to this controller and make them accessible through a mount in my home folder, using Level RAID 1.

Meaning that I would have my main SATA HDD partitioned for / and for /home/michael and then mounting the RAID in my /home/michael as something like /home/michael/files

Any suggestions or opinions would be greatly appreciated!

Thanks.

---

