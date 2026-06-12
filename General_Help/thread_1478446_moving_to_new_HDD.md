---
title: "moving to new HDD?"
date: 2010-05-09
forum: General Help
---

### Post by HHx66 on 2010-05-09
I have Xubuntu installed on an older 40GB IDE HDD right now, however that HDD is rather slow, so I'd like to move my installation over to a faster 70GB SATA drive I have, what steps would I take to do it properly?

---

### Post by kako13 on 2010-05-09
> **HHx66 said:**
> I have Xubuntu installed on an older 40GB IDE HDD right now, however that HDD is rather slow, so I'd like to move my installation over to a faster 70GB SATA drive I have, what steps would I take to do it properly?

I think that what you can do is use a tool called Simple Backup Config to backup your files.

Simple Backup Website [https://help.ubuntu.com/community/BackupYourSystem#Simple%20Backup%20Suite]("http://simplelinuxbkup.sourceforge.net/")

---

### Post by flyingmonkey35 on 2010-05-09
are you planning on upgarding to a diff flavor of linux? 
 
if so i would deffnelty recomend backing up your data and just installing a fresh copy of linux on your new hd and migrating your data over after the install.
 
Cheers!

---

### Post by louieb on 2010-05-09
Several ways - heres a couple.
[Clonezilla]("http://www.clonezilla.org/")   - advantage - will copy MBR too - disadvantage -partitions are the same size - if needed will have to be resized later.

[Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")  - advantage - easy as Clonezilla  - can resize and copy at the same time. - disadvantage - will have to fix the MBR to boot grub. [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by HHx66 on 2010-05-10
Just looking to migrate my current install to a new drive.

---

### Post by HHx66 on 2010-05-11
I ended up using ddrescue to move to my new drive, everything appears to work so far.

---

