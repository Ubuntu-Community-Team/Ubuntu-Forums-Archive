---
title: "Unmount"
date: 2006-02-19
forum: General Help
---

### Post by mofomikeman on 2006-02-19
I accidently mounted hda1 and hdb1 to /mnt.  How do I unmount hdb1 or hda1?  or both?  I want to mount hda1 to /mnt/hda1 and hdb1 to /mnt/hdb1.

---

### Post by Randomskk on 2006-02-19
sudo umount hda1
sudo umount hdb1

either of those, or it might be
sudo umount /mnt

try them out

---

### Post by kaamos on 2006-02-19
Read your first thread..

---

### Post by mofomikeman on 2006-02-19
For future searches that reach this thread:

You have to umount /mnt for each drive thats mounted in there.  I had to do it twice because I had two drives mounted there.

---

### Post by lha on 2006-02-19
sudo umount /dev/hda1
sudo umount /dev/hdb1
sudo mkdir /mnt/hda1
sudo mkdir /mnt/hdb1
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hdb1 /mnt/hdb1

---

