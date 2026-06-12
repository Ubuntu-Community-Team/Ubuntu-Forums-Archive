---
title: "super delete"
date: 2006-06-28
forum: General Help
---

### Post by souteneur3190 on 2006-06-28
what is the forbiddin command that lets u delte and format absolutly everything on your hardrive?

---

### Post by Maggot on 2006-06-28
rm -rf /

?

Oh, that just deletes not format.

You can type fdisk /dev/hda (or whatever your hard drive is) and remove the partitions.

---

### Post by thasheep on 2006-06-29
fdisk can remove the partition table but it doesn't destroy the data. Useful rescue tools like gpart (in universe) can guess the partition table. To blank the entire disk (not just partition) hda

sudo -i
cat /dev/null > /dev/hda

to turn the disk into absolute jibberish (slower)

sudo -i
cat /dev/random > /dev/hda

---

### Post by Maggot on 2006-06-29
[QUOTE=thasheep]
sudo -i
cat /dev/null > /dev/hda

to turn the disk into absolute jibberish (slower)

sudo -i
cat /dev/random > /dev/hda[/QUOTE]
8-)

---

