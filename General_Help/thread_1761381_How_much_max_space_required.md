---
title: "How much max space required"
date: 2011-05-18
forum: General Help
---

### Post by pandurang_m on 2011-05-18
Hello...

I am switching over to Ubuntu from Windows 7...
Little confusion regarding /root partition and /home partition...done web research for it, got lot of informations but few are not clear to me...

1. How much MAX space required for /root partition? If I want to install lots of apps and games...
2. Is Ubuntu as good as Windows 7?
3. Can I distribute Ubuntu CD to anyone?
4. In Windows all the programs will get install in C: drive...What about Ubuntu?

---

### Post by noah++ on 2011-05-18
> **pandurang_m said:**
> Hello...
1. How much MAX space required for /root partition? If I want to install lots of apps and games...
The root partition is not at **/root **but simply **/**. I gave my root 30 GB, and that has been enough for this average-to-advanced user who doesn't game much. You may like more. But know that it is not required to put the root and home on separate filesystems/partitions.
> 2. Is Ubuntu as good as Windows 7?I think you'll have to judge for yourself! ...except I recommend using Ubuntu 10.10 instead of the latest 11.04. The latter still needs some polish.
> 3. Can I distribute Ubuntu CD to anyone?Yes.
> 4. In Windows all the programs will get install in C: drive...What about Ubuntu?**/ **is roughly equivalent to **C:\**. Just as in Windows, Linux programs are installed to subdirectories of the root. Windows programs' file locations tend to be less disparate than Linux ones'. In Windows, they are more or less in some subdirectory of **C:\Program Files**, as you know; whereas in Linux executables are installed somewhere like **/usr/bin**, code libraries to somewhere like **/lib**, and so on. I say "something like" because although there are conventional locations for these things, the conventions are hard for me to keep straight, and not every software developer follows them well.

You don't need to manipulate the files in a Windows application directory very often. Fortunately, you won't have much occasion to do so in Linux either. When you do have that occasion, it almost always concerns a configuration text file found in your home directory or in **/etc**. Pretty easy to locate that stuff.

---

