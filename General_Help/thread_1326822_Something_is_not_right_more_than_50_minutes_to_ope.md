---
title: "Something is not right: more than 50 minutes to open a big xml file."
date: 2009-11-14
forum: General Help
---

### Post by lovinglinux on 2009-11-14
I have been experiencing some serious slow down when performing high intensive CPU tasks, but this is not right. I tried to open a big xml file (28 Mb) with Kate, but after 50 minutes waiting the file to show up I simply gave up. While Kate was trying to open the file, there was a lot of CPU activity and other applications like Firefox were slow like a turtle.

I have no idea how to troubleshoot this. This wasn't happening on Jaunty.

I'm using kde-minimal over a command-line only installation from an Ubuntu 9.10 alternate CD. My system is a Pentium 4 3.06 Ghz HT, mobo Gigabyte GA-945GCM-S2C with the latest BIOS version, 2 Gb DDR2 667 RAM, nvidia 7300 GT with driver 185.

---

### Post by rCXer on 2009-11-14
This is apparently a common problem.  See bugs

[https://bugs.kde.org/show_bug.cgi?id=145686](https://bugs.kde.org/show_bug.cgi?id=145686) (Look at the comments on this one!)
[https://bugs.kde.org/show_bug.cgi?id=211135](https://bugs.kde.org/show_bug.cgi?id=211135)
[https://bugs.kde.org/show_bug.cgi?id=203355](https://bugs.kde.org/show_bug.cgi?id=203355)

I have no idea how to fix this :(

---

### Post by lovinglinux on 2009-11-14
> **rCXer said:**
> This is apparently a common problem.  See bugs

[https://bugs.kde.org/show_bug.cgi?id=145686](https://bugs.kde.org/show_bug.cgi?id=145686) (Look at the comments on this one!)
[https://bugs.kde.org/show_bug.cgi?id=211135](https://bugs.kde.org/show_bug.cgi?id=211135)
[https://bugs.kde.org/show_bug.cgi?id=203355](https://bugs.kde.org/show_bug.cgi?id=203355)

I have no idea how to fix this :(

Thanks. Very enlightening.

---

### Post by rCXer on 2009-11-15
Another thing I forgot to mention.  The 1st link suggests that kate is slow because of its syntax highlighting.  Have you tried renaming your file from "file.xml" to "file.txt".  If kate thinks your file is a text-file it should open faster since there won't be any syntax highlighting.

---

### Post by lovinglinux on 2009-11-15
> **rCXer said:**
> Another thing I forgot to mention.  The 1st link suggests that kate is slow because of its syntax highlighting.  Have you tried renaming your file from "file.xml" to "file.txt".  If kate thinks your file is a text-file it should open faster since there won't be any syntax highlighting.

Nice tip. Thanks. I will try that.

---

