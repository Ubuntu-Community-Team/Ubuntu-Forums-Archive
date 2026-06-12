---
title: "mounting"
date: 2009-08-23
forum: General Help
---

### Post by mbuehl on 2009-08-23
I am trying to mount a drive as readable/writable.

I have edited /etc/fstab with the following lines (the directories all exist)

/dev/sda5       /media/hdd1    ext3    rw,user        0    1
/dev/sda6       /media/hdd2    ext3    rw,user        0    1
/dev/sda8       /media/hdd3    ext3    rw,user        0    1

Upon rebooting the files are all in their respective folders (really, they are just empty save for the lost+found folder). But I cannot create folders, which means my permissions settings aren't right.

I don't know what I'm doing wrong =(

User is not my username, if that matters.

---

### Post by Rocket2DMn on 2009-08-23
You need to chown the mount point with your username since you are using ext3.  Let's say your system login username is mbuehl:
```
sudo chown mbuehl:mbuehl -R /media/hdd1 /media/hdd2 /media/hdd3
```
Also, you don't need to reboot if you change fstab, just run:
```
sudo mount -a
```

---

### Post by scouser73 on 2009-08-23
Follow the instructions set out in this tutorial [[COLOR="Red"]**Mount External Hard Disk**[/COLOR]]("http://it.toolbox.com/blogs/php-bsd-me/formatting-and-mounting-an-external-hard-drive-with-ubuntu-linux-606lts-28211/")

---

### Post by nhanquy on 2009-08-23
how do you create /media/hdd1?

does it have something like this with "ls -la"?

drwxr-xr-x  2 root    root    4096 2009-08-23 19:03 hdd1

---

### Post by mbuehl on 2009-08-23
> **nhanquy said:**
> how do you create /media/hdd1?

does it have something like this with "ls -la"?

drwxr-xr-x  2 root    root    4096 2009-08-23 19:03 hdd1


sudo mkdir /media/hdd1 

etc

---

### Post by mbuehl on 2009-08-23
> **Rocket2DMn said:**
> You need to chown the mount point with your username since you are using ext3.  Let's say your system login username is mbuehl:
```
sudo chown mbuehl:mbuehl -R /media/hdd1 /media/hdd2 /media/hdd3
```Also, you don't need to reboot if you change fstab, just run:
```
sudo mount -a
```


victorydance.

thanks

---

