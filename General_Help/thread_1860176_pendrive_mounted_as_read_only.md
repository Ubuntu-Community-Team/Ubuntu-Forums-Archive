---
title: "pendrive mounted as read only"
date: 2011-10-14
forum: General Help
---

### Post by doom3d on 2011-10-14
A few days ago my fat32 formatted 8GB pendrive started to be mounted as read only file system.  OS: Ubuntu 10.10, gnome2 DE.

I have the following observations:

- my old fat16 formatted 128 MB pendrive always mounted propely,
- I can write the 8GB pendrive when logged in as another(backup) user with same privileges to gnome
- I can read/write/delete files on the 8GB pendrive when logged in as default user to LXDE
- filesystem is read only when logged in as default user to gnome+openbox

-> problem related to gnome!

Now I would like to know, how to repair my system.

---

### Post by dcstar on 2011-10-14
> **doom3d said:**
> A few days ago my fat32 formatted 8GB pendrive started to be mounted as read only file system.  OS: Ubuntu 10.10, gnome2 DE.

I have the following observations:

- my old fat16 formatted 128 MB pendrive always mounted propely,
- I can write the 8GB pendrive when logged in as another(backup) user with same privileges to gnome
- I can read/write/delete files on the 8GB pendrive when logged in as default user to LXDE
- filesystem is read only when logged in as default user to gnome+openbox

-> problem related to gnome!

Now I would like to know, how to repair my system.

Do a fsck on the partition.

---

### Post by doom3d on 2011-10-15
I have run gparted -> partition check from live CD. Still have the problem. Results for / attached. (I don't have separate /home partition.)

BTW, I have just realized, that the volume control applet also disappeared from the upper menu. I also can't add it- it is missing from the applet list.
 However, this applet works when I log in as another user.

---

### Post by dcstar on 2011-10-15
> **doom3d said:**
> I have run gparted -> partition check from live CD. Still have the problem. Results for / attached. (I don't have separate /home partition.)


I seriously doubt that you pendrive has 6 partitions on it, which is what you have attached as a fsck of /dev/sda6.

Do the fsck on the pendrive partition.

---

### Post by doom3d on 2011-10-16
> **dcstar said:**
> Do the fsck on the pendrive partition.

OK, I did it. Thanks. Now It works.

 I'm just curious, why the problem appeared for the default user only, and only on gnome desktop. Results attached.
[SIZE="1"](In most of the cases it would affect all users, regardless desktop environment. Is it right?)[/SIZE]

---

