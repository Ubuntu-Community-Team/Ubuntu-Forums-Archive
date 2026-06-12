---
title: "Cant mount new harddisks"
date: 2006-02-07
forum: General Help
---

### Post by foof on 2006-02-07
What can be the problem if I can't mount two new harddisks?
I have three harddisks and I boot on the first one.

I've run partman from the install-CD and created mount points /media/hdb1 and /media/hdc1 .
In my fstab file they look like this:
```

/dev/hdb1  /media/hdb1  ext3  defaults  0  3
/dev/hdc1  /media/hdc1  ext3  defaults  0  4

```

But when I run:
sudo mount -a
I get an error saying:
```

mount:  /dev/hdb1 is already mounted or /media/hdb1 is busy.
mount:  /dev/hdc1 is already mounted or /media/hdc1 is busy.

``` 

If i run:
sudo umount /dev/hdb1 it says it's not mounted!
If I create a new folder:
sudo mkdir /test1 and then try to mount with:
sudo mount /dev/hdb1 /test1
I get:
```

mount:  /dev/hdb1 is already mounted or /test1 is busy.

``` 

WTF is this!? Why can't I mount them? Help please!

---

### Post by foof on 2006-02-07
Can it have something to do with the upgrade of the kernel I did?
I followed a guide here in the forums and upgraded the Kernel to 2.6.14-ck1
??

---

### Post by pt78 on 2006-02-07
I guess you will have to chown and chmode mountpoint for new drives. 

Somethoing like this:
sudo chown root /media/hdb1
sudo chmod 777 /media/hdb1
sudo chown root /media/hdc1
sudo chmod 777 /media/hdc1

---

### Post by foof on 2006-02-10
I found the solution:
[http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=103900&page=1&pp=10)

---

