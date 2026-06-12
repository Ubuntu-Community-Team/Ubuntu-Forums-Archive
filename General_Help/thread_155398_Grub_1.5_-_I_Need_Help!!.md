---
title: "Grub 1.5 - I Need Help!!"
date: 2006-04-05
forum: General Help
---

### Post by kypez on 2006-04-05
Hey all I have a serious situation on my hands. I had my Toshiba Laptop dual booted with Breezy Badger and Windows XP. I just recovered my HDD for a fresh new start. So basically my HDD should just have windows on it now. However GRUB 1.5 loader still comes up but doesn't do anything. It sits at

Error 22...

So basically I can't get into Windows or anything. How can I either get rid of GRUB 1.5 or get by it into windows?? Any usefull help is appreciated because I need my laptop every day.

Alex

---

### Post by croak77 on 2006-04-05
Just put in the Windows Xp cd and choose the recovery mode, boot to DOS and enter FIXMBR and reboot. You should then boot straight into windows, no grub.

---

### Post by dermotti on 2006-04-05
if you have your windows XP CD, you can boot off that. Once the CD boots there will be an option for Recovery Console. (press R).

Once in the recover console, type ** fixmbr**

---

### Post by kypez on 2006-04-05
yeah ok thanks for the help, however I re-installed ubuntu which got the GRUB working. What I would LOVE to do right now is completely get rid of ubuntu. I want to try another distribution of linux until the new ubuntu update comes out. I want to get rid of ubuntu, and take over the harddrive space that linux is taking right now and have it back for windows. How do I get rid of linux?

---

### Post by dermotti on 2006-04-05
You can just delete the partitions from within windows.
[B]
Control Panel --> Administrative Tools --> Storage[/B] i belive

---

### Post by Harry_Sack on 2006-04-06
You can also just install another distro just like you reinstalled ubuntu, then it will ask you to install grub. Just use its partitioner to format the ubuntu parttions while you install.

---

