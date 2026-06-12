---
title: "Wiped out Partition table with GParted"
date: 2009-10-31
forum: General Help
---

### Post by Joe Ker1086 on 2009-10-31
Okay, I know that this is a Ubuntu forum but this is more a question about GParted. I had a dual boot with Windows 7 and Fedora 11. I had the windows 7 install on a 10 gig partition so I was trying to resize my Fedora partition to give it a little more space. In doing this I selected the wrong option (SU really is dangerous) and it blew out my partition table. Now I Cant boot into any OS. I tried putting in the Fedora Install CD to fix the MBR but it Can not find an os to mount. The windows cd can see all of my partitions but it is saying that it cannot be installed on a GPT partition...... I don't want to just blow it all away and reinstall everything (although at this point it might be easier). I downloaded the Linux System Rescue CD and have made some progress (now it actually tries to boot into windows which i dont really care about...would be willing to blow away that partition) but i still cannot get it to even attempt to boot into fedora....I'm using testdisk with the rescue cd but it cant seem to make the fedora partition bootable. I think this is because fedora uses LVM but I don't know where to go from here..... Can anyone help??????:confused:

---

### Post by phillw on 2009-10-31
> **Joe Ker1086 said:**
> Okay, I know that this is a Ubuntu forum but this is more a question about GParted. I had a dual boot with Windows 7 and Fedora 11. I had the windows 7 install on a 10 gig partition so I was trying to resize my Fedora partition to give it a little more space. In doing this I selected the wrong option (SU really is dangerous) and it blew out my partition table. Now I Cant boot into any OS. I tried putting in the Fedora Install CD to fix the MBR but it Can not find an os to mount. The windows cd can see all of my partitions but it is saying that it cannot be installed on a GPT partition...... I don't want to just blow it all away and reinstall everything (although at this point it might be easier). I downloaded the Linux System Rescue CD and have made some progress (now it actually tries to boot into windows which i dont really care about...would be willing to blow away that partition) but i still cannot get it to even attempt to boot into fedora....I'm using testdisk with the rescue cd but it cant seem to make the fedora partition bootable. I think this is because fedora uses LVM but I don't know where to go from here..... Can anyone help??????:confused:


Hi, this tutorial should point you in the right direction...

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Phill.

---

### Post by Joe Ker1086 on 2009-10-31
> **phillw said:**
> Hi, this tutorial should point you in the right direction...

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Phill.

Thank you, Looks a lot like the documentation i have for rescue cd but I will look through it and see what i can find

---

### Post by phillw on 2009-11-03
> **Joe Ker1086 said:**
> Thank you, Looks a lot like the documentation i have for rescue cd but I will look through it and see what i can find

Hi, I was looking for something, and stumbled upon this ..

[http://forums.fedoraforum.org/showthread.php?t=31275](http://forums.fedoraforum.org/showthread.php?t=31275)

It may be of help to you.

Phill.

---

### Post by Joe Ker1086 on 2009-11-06
> **phillw said:**
> Hi, I was looking for something, and stumbled upon this ..

[http://forums.fedoraforum.org/showthread.php?t=31275](http://forums.fedoraforum.org/showthread.php?t=31275)

It may be of help to you.

Phill.

This looks EXTREMELY useful, thank you!:D

---

### Post by phillw on 2009-11-06
> **Joe Ker1086 said:**
> This looks EXTREMELY useful, thank you!:D


You're welcome, and buddy request accepted.

Phill.

---

### Post by Joe Ker1086 on 2009-11-06
haha awesome :lolflag:

---

