---
title: "Urgent help needed! (grub rescue?)"
date: 2010-05-13
forum: General Help
---

### Post by tega2919 on 2010-05-13
While experimenting with partitions, stupid me decided it would be a good idea to fool around with them without backing up my data. Now my GRUB is on the partition that I deleted, and my entire computer is using one partition for windows 7. I have a whole operating system that I can't access because I can't boot anything!
How can I make it so Windows starts instead of the grub rescue?

EDIT: More detail:

I was in the windows disk management, I deleted my ubuntu partition and extended the windows 7 partition to take up the whole disk. How can I access my windows GUI again?

---

### Post by itiswhatitis on 2010-05-13
Boot your Windows CD
Select A Language
Select Repair your computer
Select System Recovery Options
Select Command Prompt

Run  bootsect.exe /FIXMBR
Run bootsect.exe /FIXBOOT

---

### Post by tega2919 on 2010-05-13
Thanks, but I found an alternative.
Just for anybody who happens to come across this problem do the following:
Boot from Ubuntu LiveCD and select Install Ubuntu.
Do an installation of Ubuntu as normal, partitioning however much space you would like for Ubuntu.
Once the install is complete, the computer will restart and you will have a new grub with access to all partitions.

---

