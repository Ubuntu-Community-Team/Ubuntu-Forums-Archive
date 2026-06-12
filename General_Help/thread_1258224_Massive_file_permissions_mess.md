---
title: "Massive file permissions mess"
date: 2009-09-04
forum: General Help
---

### Post by Compintuit on 2009-09-04
OK, I'm in loooots of trouble. I've been trying to make my /home it's own partition, so I booted on a live cd, shortened my partition, made a new one, and as root copied /home over with this command: ```
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```
from here[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") I was trying to do a clean install after, but ubiquity crashed every time I specified the partition I for my home. So I installed without, and have since been trying to make my /home be on that partition. Unfortunatly, after I added this to fstab:```
/dev/sda6 	/home		ext4	rw,auto	0 0
``` And rebooting, NOTHING has the right permission! I have read only access to all the files! Most of my configuration is messed, because I can't edit the files. So, after panicking, what can I do to give myself access to my files again?

---

### Post by Vaphell on 2009-09-04
does ls -l say that root is the owner of everything?

---

### Post by Compintuit on 2009-09-04
```
caleb@caleb-laptop:~/Desktop$ ls -l
total 192
-rw-rw-r-- 1 root root 32068 2009-09-01 22:05 Asus Eee Pic2.jpg
-rw-rw-r-- 1 root root 64851 2009-09-01 22:04 Asus Eee Pic.jpg
drwxrwxrwx 5 root root  4096 2009-09-02 10:59 css
drwxrwxrwx 4 root root  4096 2009-09-02 10:59 example
-rw-rw-r-- 1 root root 79020 2009-09-01 21:40 inspiron-11z-design2.jpg
drwxrwxrwx 2 root root  4096 2009-09-02 10:59 templates
```
I'm pretty sure that means yes.

---

### Post by Whiffle on 2009-09-04
try:

sudo chown -R caleb:caleb <whateverdirectory that is>

---

### Post by Compintuit on 2009-09-04
*Massive sigh of relief*
I think that worked... I'm rebooting to see if my config has returned. 
On another note, should I change any of the options on fstab? I wasn't sure what to put.

---

### Post by Whiffle on 2009-09-04
I'd probably put:
```

/dev/sda6 /home           ext4    relatime        0       2

```

Also, you might find the UUID of that partition, and then put that in the fstab instead, so that if the position of the drive ever changes, it still works.  Like so:
```

UUID=bdf6a55c-3442-405f-b82c-cab05988ec86 /home           ext4    relatime        0       2
```

---

### Post by Vaphell on 2009-09-04
UUID: sudo blkid

---

### Post by Compintuit on 2009-09-04
OK, thank you very much, most everything is a go - I just have one other thing I'm still not sure about. The first time I booted up, another /home would have been created, still on my original partition. Can I delete that? And, for future reference for anybody that sees this thread, [here]("http://www.linuxmint.com/wiki/index.php/Move_home_to_its_own_partition") is a better guide.

---

### Post by Whiffle on 2009-09-04
I don't see why another home would have been created, but so long as it isn't listed in your fstab, no user's account uses it, and it doesn't have anything important in it, there shouldn't be any problem deleting it.

---

