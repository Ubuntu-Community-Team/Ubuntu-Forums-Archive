---
title: "mounted partion help"
date: 2006-06-17
forum: General Help
---

### Post by junior aspirin on 2006-06-17
i have an ext3 partion, mounted in fstab as so:
```
/dev/hdb2       /mnt/backups    ext3    defaults	0       0
```

the problem is when i delete stuff from that partition it wont send it to the wastebasket, it fully deletes it. how to i make it work properly. i am guessing that it is something to do with the drive being root owned, but do not know how to change it.
any ideas?

---

### Post by TLE on 2006-06-17
How do you delete it ?

---

### Post by junior aspirin on 2006-06-18
by pressing the delete key on my keyboard. it then says > Cannot move file to wastebasket, do you want to delete immediately? with the optons cancel and delete.

---

### Post by TLE on 2006-06-18
Ok, I also have a ext3 partition mounted and I can delete from it to the wastebasket. My fstab is a little different though. That last number is a 2
```
/dev/sda5       /mnt/multimedia ext3    defaults        0       2
```
Try it and see if it works

---

### Post by junior aspirin on 2006-06-18
same problem. will have a play later...

---

### Post by Joe Momma on 2006-06-21
did you try looking in

/mnt/multimedia/.Trash-username

I think Ubuntu makes a new trash directory on mounted drives so it can just change the pointer instead of actually copying the file to your home direcotry trash bin.

---

### Post by junior aspirin on 2006-06-26
haha the answer was simple, just needed to change the permisions in /mnt/ so every one can write to the folder :p

---

