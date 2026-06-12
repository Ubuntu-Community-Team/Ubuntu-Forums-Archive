---
title: "Reinstalling ubuntu while grub 2.0 is installed into same partition !!"
date: 2011-02-21
forum: General Help
---

### Post by Rushyang on 2011-02-21
Hiya fellas!

I have triple boot machine Windows 7  + Ubuntu + Mac OS X in a single HDD.

Windows 7 -- /dev/sda1
Ubuntu 10.10 -- /dev/sda2 (In same Partition grub 2.0)
Mac Snow Leopard -- /dev/sda3 

I have installed GRUB 2.0 in same partition where current ubuntu is installed ie /dev/sda2..
and basically Windwos Boot manager is installed within MBR.. & I have added GRUB 2.0 and Mac OSX entry into windows boot manger with some freeware from windows 7. So practically when I start my computer First Windows Boot manager comes up and asks me which OS to start first. I set up this type of installation with the thought that when grub 2.0 is not installed within MBR, I can format the whole /dev/sda2 partition without any difficulty and reinstalled any future release distro of ubuntu. So is it practically possible? If I format /dev/sda2 and reinstall new ubuntu release there.. Old grub won't affect the installation of new one.. right?

---

### Post by Rushyang on 2011-02-25
Let me rephrase my question..
I have installed ubuntu 10.10 in /dev/sda2, and so do grub.
Now, If I want to reinstall Ubuntu 10.10, I will obviously format /dev/sda2 first. Will my new installation of ubuntu create any grub releated problem?

---

