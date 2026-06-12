---
title: "Installing Xubuntu for the first time, messed up partitioning"
date: 2009-10-07
forum: General Help
---

### Post by jongudm on 2009-10-07
I installed Xubuntu 9.04 (first time I try Ubuntu) last night on an old laptop with Windows XP and SuSE already installed.  Everything worked perfectly, all three OSes show up in the GRUB menu and run properly.  Then I realised that the space allocated for Xubuntu was so limited that when I had installed the Icelandic, Danish and German language packs, vim and LaTeX there was no more space.  Oops!  There is enough free space on the other partitions so they can be reduced but that did not happen.  I chose the "Install them side by side" option and expected to get a "How much space should be taken from the other partitions?" kind of screen.  How do I change the partitioning, do I have to reinstall?  If so, then how do I get this right during the reinstall?

Thanks in advance.

---

### Post by PacSci on 2009-10-07
The option to resize your disks was during the installer, on the same screen where you selected "Install them side by side" - the disk space indicator was actually a slider that you could use to change disk space allocations. Yes, I know that's confusing.

You don't have to reinstall, but you can put your Live CD back in and run "System > Partition Editor" to resize the partitions (you can't resize Xubuntu's partition while it's running).

---

### Post by jongudm on 2009-10-07
Ahh, I wondered if that was the case.  That is actually a bit confusing now that you mention it. :)  Thanks very much, I' try that as soon as I can.

---

### Post by jongudm on 2009-10-07
That was exactly what I needed,now I've got plenty of space! :)

Thank you very much for your help.

---

