---
title: "Installing Ubunt, Won't Recognize Other OS"
date: 2011-04-30
forum: General Help
---

### Post by LonelyAspie on 2011-04-30
I am installing Ubuntu on my Dad's computer, but also leaving his default one on their too, so he can dual boot whenever he wants, instead of just chaning HDD's, like I was before.

When I try to Install UBuntu, the option dosen't appear (install along with other OS), it just says erase entire disk and use that and the one beneath that (I forget what it is). When I look at the partition during the install, The entire disk partition is green, I think it means that is empty, but when I boot up, Windows XP boots in just fine. I haven't had this problem before. ANy other time I go to install with another OS, it detects it.

---

### Post by 3Miro on 2011-04-30
This is interesting, I am not sure what could be causing it. You can try to go "advanced" and install Ubuntu manually.

1. BACKUP EVERYTHING IMPORTANT: you are supposed to do this every time you are going to mess around with different partitions.
2. Boot from Ubuntu LiveCD and start Gparted.
3. Resize the Windows partition and create two new partitions, one about the size of your RAM (or more if you have less than 3GB of RAM) and one partition where you want to put Ubuntu (at least 2GB, although more is preferable, depending on the size of your HDD I would give it at least 10 - 20GB). It is good to put those partitions "after" Windows XP.
4. When you install Ubuntu, during the partition stage, tell it to go advanced and then select the small partition and tell the installer to use it as Swap. The large partitions should be formated ext4 and using mount point /
5. The rest of the install should be the same.

Note: Pay special attention to step 1.

---

### Post by LonelyAspie on 2011-07-08
Instead I put in another HDD, so I can switch between them at startup.

---

### Post by Blasphemist on 2011-07-08
For your future reference then, Herman has a very comprehensive site on installing for dual boot that covers the options in detail.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

