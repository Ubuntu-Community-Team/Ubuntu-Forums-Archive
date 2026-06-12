---
title: "Partition Permission"
date: 2010-08-04
forum: General Help
---

### Post by jtcady on 2010-08-04
I need to change the permissions for the files in the separate data  partition. When I mount it, it mounts in /media/xxxxxxxxxxxxx

**_Do I use:_**
sudo chown -R user:group /media/sda3
sudo chmod -R 755 /media/sda3

or 

sudo chown -R user:group /dev/sda3
sudo chmod -R 755 /dev/sda3

---

### Post by deserthowler on 2010-08-04
> **jtcady said:**
> I need to change the permissions for the files in the separate data  partition. When I mount it, it mounts in /media/xxxxxxxxxxxxx

**_Do I use:_**
sudo chown -R user:group /media/sda3
sudo chmod -R 755 /media/sda3

or 

sudo chown -R user:group /dev/sda3
sudo chmod -R 755 /dev/sda3

I do the following :

cd /media
ls -l
sudo chown -R user:group UID
sudo chmod -R 755 UID

(if you type the first few characters of UID then tab, it will complete the UID)

Earl

---

### Post by jtcady on 2010-08-04
Thank you so much.  And for the quick reply.

---

