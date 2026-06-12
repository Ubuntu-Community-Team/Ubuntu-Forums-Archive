---
title: "General LVM info needed"
date: 2010-03-23
forum: General Help
---

### Post by snares on 2010-03-23
I was wondering if when you setup an LVM if your volumes needed to be reformatted? Can you combine two disks that have data on them together without losing the data?

cheers
snares

---

### Post by psusi on 2010-03-23
Yes, you have to reformat to start using LVM.  Once you're on LVM though, you can move volumes around, add and remove drives, all without data loss.

---

### Post by snares on 2010-04-01
I have another question for you. What would you use to setup a LVM? I know the Ubuntu setup cd could do it but could you use GParted or the Gparted Live CD?

---

### Post by psusi on 2010-04-04
No, gparted does not understand lvm.  The recommended way is to install using the alternate installer.  I just installed the lvm2 package on the livecd and manually set up lvm then installed.

---

