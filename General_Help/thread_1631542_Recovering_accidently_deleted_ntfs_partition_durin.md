---
title: "Recovering accidently deleted ntfs partition during installation"
date: 2010-11-26
forum: General Help
---

### Post by VoodooRider on 2010-11-26
Hi guys!

During the installation of ubuntu i accidently changed type of my win7 ntfs partition to ext4 thinking that it was the other partition I wanted to change(format). I realized I've made a mistake and exited the installer. Is there any way I can recover the changed partition?

---

### Post by Tanner1294 on 2010-11-26
When you change the filesystem, it will completely re-write that partition (in other words, all data is destroyed). However, there are tools for Windows Linux and Mac that can (usually) recover deleted items. (It does with the fact that when a computer deletes a file, or formats a disc, it doesn't actually write to the entire disc. It just writes to the first line. The first line tells the computer what the rest of the disc is like. Programs that recover deleted data ignore the first line and read the physical data on the disc. The only problem with this is that they can't read the file type, so you usually just get a VERY bland list of files)

---

