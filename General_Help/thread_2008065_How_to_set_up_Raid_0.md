---
title: "How to set up Raid 0?"
date: 2012-06-22
forum: General Help
---

### Post by vishnumrao on 2012-06-22
Just built a AMD system with A8-3870K. Motherboard is Asrock A75m-itx. I have a OCZ Agility 3 120GB as the main boot drive. I have two identical Hitachi 320 GB hard drives which I want to put in a RAID 0. Just to be able to get it as a big filesystem. 

I am not very worried about data safety. The data in the RAID 0 will get backed up to my NAS once a week.


I set up the RAID in the motherboards RAID configuration utility. Shows up as a 640 GB. But when I boot into Ubuntu, I still see two separate 320 filesystems. Even gparted sees two separate drives.

What am I doing wrong?

---

### Post by vishnumrao on 2012-06-22
After a bit of searching on the web, I came to this ubuntu community documentation: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The recommendation is to not use fakeraid but to use the OS to do the RAID. I may go this route, but I am still keen on getting fakeraid working (just for the kicks).

The documentation mainly talks about installing Ubuntu on a RAID0. But I am more interested in creating a RAID0 for data

---

