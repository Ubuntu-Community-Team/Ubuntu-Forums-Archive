---
title: "Added Second Storage Harddrive"
date: 2009-12-29
forum: General Help
---

### Post by Gillette on 2009-12-29
I've got an old computer I've setup with Ubuntu 9.10 that I'm going to give away. I have the Ubuntu Operating system on the first harddrive (6 GB) and I used gparted to create one partition on the second harddrive. I want to have it setup so that all stuff will be stored on the second harddrive. I've looked at several postings about doing this but they all seem rather confusing. I rarely use the command lines in the terminal so I'm not too good about deciphering all that arcane looking stuff. Anyway there is an icon that has shown up on the desktop "HardDrive2."

Can anyone give me step by step directions on getting the HardDrive2 setup as the home harddrive, specific to my system?

---

### Post by Admiral Yi on 2009-12-29
I think I may understand what you mean. When you install Ubuntu do partitioning manually, create the partition on the first hardrive and choose / (root) as the type. Also tick the box saying 'bootable'. Then on the second drive create a partition and chose '/home' as the type. 

If you have already installed and don't ant to reinstall, try following this guide: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome"). It uses the commandline, but it should be easy enough to do without much knowledge.

---

### Post by Gillette on 2009-12-29
> **Admiral Yi said:**
> 
If you have already installed and don't ant to reinstall, try following this guide: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome"). It uses the commandline, but it should be easy enough to do without much knowledge.

I've already installed. I had to use the alternate file since my RAM is only 256 and can't manage the live disk. 

I may reinstall. Thanks for the help.

---

### Post by Gillette on 2009-12-29
> **Admiral Yi said:**
> I think I may understand what you mean. When you install Ubuntu do partitioning manually, create the partition on the first hardrive and choose / (root) as the type. Also tick the box saying 'bootable'. Then on the second drive create a partition and chose '/home' as the type.


I reinstalled it doing the partitioning manually. Seems like something didn't go as planned. Each harddrive is 6 gb and when I look at the home folder properties it says there is only 3 gb disk space available. What now?

---

