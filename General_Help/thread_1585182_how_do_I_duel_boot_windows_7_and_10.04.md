---
title: "how do I duel boot windows 7 and 10.04"
date: 2010-09-30
forum: General Help
---

### Post by teddy101 on 2010-09-30
How do I get windows to install and duel boot with ubuntu?

I am duel running Ubuntu 10.04 and uber student (Linux distro). The plan is to lose uber student and add windows 7. I need to format the part of the harddrive to good old ntfs (or what ever it may be called :P) So I went system > administration > disk utility. of course I then choose the hard drive deleted the uber student partition of 100 gigs and turned it in to ntfs.
Ramed windows disk in. But the windows screen didnt show up this partion and only gave me the option to use my swap space my 140 for ubuntu or my 110 for logical partitions.

Thanks guys :)

---

### Post by ronnielsen1 on 2010-09-30
I haven't had luck with having windows recognize ntfs partitions created from linux. Use gparted or diskutility to delete the ntfs partition and then leave it unpartitioned. Windows should see it then. You will have to reinstall grub after installing windows

---

### Post by teddy101 on 2010-09-30
thanks man.

umm how do I reinstall grub?

---

### Post by Rubi1200 on 2010-09-30
To reinstall GRUB:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by teddy101 on 2010-09-30
I followed your instructions to the letter and these are the following results:


setup cannot detect or create a partition for this drive. (not word for word)

Thanks again, I am pinning the hopes on you :P

---

### Post by Rubi1200 on 2010-09-30
Using the LiveCD, post the results of the bootscript linked at the bottom of my post please.

---

### Post by marin123 on 2010-09-30
can you install windows through virtual machine from ubuntu? install virtual machine in ubuntu and when installing win, assign to that ntfs partition you left blank. maybe that could work. and the advantage is that you can browse the web while windows is being installed :D

---

