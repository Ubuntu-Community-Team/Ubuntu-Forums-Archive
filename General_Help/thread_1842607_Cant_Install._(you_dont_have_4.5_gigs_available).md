---
title: "Cant Install. (you dont have 4.5 gigs available)"
date: 2011-09-11
forum: General Help
---

### Post by Sittingduck91 on 2011-09-11
Well I know this is wrong. It sais I dont have 4.5 gigs available, and I have 500 gigs. Can someone help me. This happens all the time. i am installing through a disc by the way.

---

### Post by Quackers on 2011-09-11
Welcome to UF.
Do you have free space that is not within a partition or is it free space within a Windows partition?

---

### Post by Sittingduck91 on 2011-09-11
No partitions yet. Fresh brand new hard drive.

---

### Post by Quackers on 2011-09-11
Brand new, as in out of the box, or has it been used in another system? A raid system or a Mac, for instance.

---

### Post by Sittingduck91 on 2011-09-11
Never been used, but I am sure it is running. The drive blinks constantly.

---

### Post by Quackers on 2011-09-11
Is it a SSD? Is it plugged in to a sata 3 port - try sata 2.
You don't have a Marvell sata controller do you?

---

### Post by Sittingduck91 on 2011-09-11
No not Solid State, and its in Port 1 sata, and I created a partition using Windows 7 disc. Lets see if that works. and whats that program?

---

### Post by Quackers on 2011-09-11
Did the partition you created use the whole disc? That would do it :-)

---

### Post by Sittingduck91 on 2011-09-11
Well I am going to install 7 and then use wubi to do the rest I think, but explain your plan please.

---

### Post by Quackers on 2011-09-11
If you have created a NTFS partition from within Windows and that partition takes up all the disc space then there is no room for Ubuntu to install to, as Ubuntu cannot install to an NTFS partition, unless it's a wubi install.
Ubuntu uses ext4 partitions nowadays.

---

### Post by Sittingduck91 on 2011-09-11
do I even have to partition for Ubuntu till after I go through the install?

---

### Post by Quackers on 2011-09-11
No, an empty hard drive is ok. The installer can partition an empty disc.

---

