---
title: "Load Terminal from Command Line"
date: 2011-01-17
forum: General Help
---

### Post by sokkerkid13 on 2011-01-17
Hi All,
    I was tinkering around with my /etc/grub.d/10_linux file to try and alter the way my OS's were displayed on startup and somehow I filtered out my Ubuntu option, now I have no way off accessing the terminal, I tried the command gnome-terminal, but had no success, does anybody know how to access my /etc/grub.d/10_linux file through the grub2 command line?? Thanks!

---

### Post by oldos2er on 2011-01-17
I think you would need to boot a LiveCD, then mount the partition where the file is in order to edit it.

Did you create a backup copy of the file?

---

### Post by sokkerkid13 on 2011-01-17
Yes I created a backup, thats a good idea thank you!  Im not going to call this issue resolved till i can try i tonight after work though

---

### Post by sokkerkid13 on 2011-01-18
So I mounted my sda1 /mnt partition, and then in the terminal opened the file with gedit, but only opened the /etc directory of the live disc, how to I fully port into my partition so that I can edit the file that I altered (sorry Im a bit of a newbie)  Thanks

---

### Post by oldos2er on 2011-01-19
If the disk is mounted in /mnt/sda1, you would use the command **gksu gedit /mnt/sda1/etc/grub.d/10_linux**

---

### Post by sokkerkid13 on 2011-01-20
got it! Thanks for your help!

---

### Post by oldos2er on 2011-01-20
Great! Please mark the thread as Solved (under Thread Tools).

---

