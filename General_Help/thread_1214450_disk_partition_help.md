---
title: "disk partition help"
date: 2009-07-15
forum: General Help
---

### Post by fedefinki on 2009-07-15
Hi,
I am having problems with my disk partition.
i have a 250gb, when i bought my laptop it came with windows vista, so i did a partition to install linux, so i have dual boot vista and linux ubuntu.
then i realize that i had a 10gb partition called EISA, which is a recovery for system defaults.
anyway i deleted that partition and i want to merge it with vista partition, but i cant do it with vista disk manager cause it cant resize to the left, and this 10gb partition is to the left of the vista partition.
then i also want to shrink my linux partition a give that free space to vista partition.
all this is because i have to use windows for my new job, so i want to have half of the disk vista half ubuntu.
take a look at the snapshot of gparted runing from ubuntu live cd, that will clarify what i am trying to do.
i don't want to backup first then format and upload backups to acomplish this.
any ideas on how to do this easilly without loosing data.
thanks.
):P

---

### Post by roccivic on 2009-07-16
right-click on /dev/sda1 and select "resize/move".

---

### Post by fedefinki on 2009-07-21
[roccivic]("http://ubuntuforums.org/member.php?u=560306") r u serious??, did you even read the question?
thanks anyway for trying.

---

### Post by SuperSonic4 on 2009-07-21
A) You could leave it as is. If you don't need the room it's the safest option

----------

B) What is sda2 (ext3) for?

If you can get away with it deleted sda2 and move your linux partition to the right although you may not be able to from within a logical partition

You should be able to then expand vista. It's possible you may have to repair grub so read up on that if you need to.

---------

C) You could shrink the ubuntu partition from the right and create an NTFS partition for data, vista would see this partition and you'd be able to save any work documents there, keeping sda1 open for programs etc

---

