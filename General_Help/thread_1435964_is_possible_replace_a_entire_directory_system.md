---
title: "is possible replace a entire directory system?"
date: 2010-03-22
forum: General Help
---

### Post by pdro7 on 2010-03-22
hi, i have crashed my system, i have a lot of simualtion software already configured and working on it,  i'm thinking to do a new installation of ubuntu in a different partition and  copy there all directory tree, basically replace the new / directory system, whit the old one that i have back up. Can i do this and everything will works ok?

---

### Post by Herman on 2010-03-22
You can install a another Ubuntu in another partition in the same hard disk, or in a different hard disk or in a USB flash memory stick.

Then if you know how to boot with GRUB using the Command Line, or if you are willing to learn, (give it a try, it's easy if you try it), then you can boot the kernel in one disk and run the root file system in another disk or partition. ;)

Here's a link about how to use GRUB2 in CLI mode,  [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System  

If you're still using the old 'Legacy' GRUB, here's the link about that, [GRUB's Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli"). - GRUB can function as a miniature operating system.

Remember, the kernel doesn't need to be part of the same operating system to boot with it, you can boot with a kernel from any other Ubuntu operating system.

---

