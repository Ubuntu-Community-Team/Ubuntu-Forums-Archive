---
title: "External HDD doesn't work in Windows"
date: 2009-10-01
forum: General Help
---

### Post by jolindbe on 2009-10-01
Hi!

About 8 months ago, I started using Ubuntu, dual-booting with Vista, which I had earlier. I have an external harddrive (Seagate 500 GB, NTFS), which both operating systems have been able to see and use. For some time I've only been using Ubuntu (well, I like it), but when I recently booted in Vista, it doesn't recognise my external HDD any longer, it says something like "The drive is not formatted, do you want to format it now?", which I'd rather not...

Ubuntu sees it and writes to it without problem.

I have tried to put it in several different USB jacks, so this shouldn't be the problem.

I am sorry if this question is more related to Windows than Ubuntu, but my feeling is that the problem has arisen due to something that has been done by Ubuntu (or by me using Ubuntu...)

---

### Post by dcstar on 2009-10-01
> **jolindbe said:**
> Hi!

About 8 months ago, I started using Ubuntu, dual-booting with Vista, which I had earlier. I have an external harddrive (Seagate 500 GB, NTFS), which both operating systems have been able to see and use. For some time I've only been using Ubuntu (well, I like it), but when I recently booted in Vista, it doesn't recognise my external HDD any longer, it says something like "The drive is not formatted, do you want to format it now?", which I'd rather not...

Ubuntu sees it and writes to it without problem.
........
I am sorry if this question is more related to Windows than Ubuntu, but my feeling is that the problem has arisen due to something that has been done by Ubuntu (or by me using Ubuntu...)

Run a fsck on it, or use gparted to "Check" the partition.

---

### Post by juancarlospaco on 2009-10-02
Its formated on NTFS or native EXT4 partition? :)

---

### Post by jolindbe on 2009-10-02
> **juancarlospaco said:**
> Its formated on NTFS or native EXT4 partition? :)

It is NTFS (why fsck will not work) - it was first formatted in Vista, before I got Ubuntu.

---

### Post by jolindbe on 2009-10-05
I wasn't able to test until now, but gparted can't check ntfs disks, nor can fschk. What should I do?

---

### Post by StuartN on 2009-10-05
Install ntfsprogs and then gparted / parted will have added ntfs capabilities, or you can use the command-line tools from ntfsprogs.

---

