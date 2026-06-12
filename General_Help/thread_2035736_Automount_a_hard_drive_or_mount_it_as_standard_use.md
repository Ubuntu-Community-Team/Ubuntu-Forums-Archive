---
title: "Automount a hard drive or mount it as standard user"
date: 2012-07-31
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-31
Hi all,

I'm trying to set up Ubuntu on my girlfriend's laptop. I want to have an Administrator account for me, and a Standard User account for her, since she's not experienced with Linux. But I can't figure out how to allow her account to have the privilege to mount other hard drive partitions. I'd like to either have all hd partitions mount automatically after login, or grant her User account the mounting privilege. I'd also like to know if there are any better suggestions about how this can be solved.

---

### Post by drmrgd on 2012-07-31
What you'll need to do is to add the entries for the partitions you want mounted in the fstab file.  This will allow those partitions to be mounted every time automatically so that she won't have to go through the hassle of doing it herself.  Here is some Ubuntu Community documentation on how to alter the fstab file to add entries:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-07-31
drmrgd thanks for the help. I've managed to edit fstab and make the partition automount. However, now all the files and folders on that partition with non-latin (cyrillic) names show only question marks instead of their names. How can I fix this?

---

