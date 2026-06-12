---
title: "migrate home"
date: 2010-11-19
forum: General Help
---

### Post by flipper T on 2010-11-19
can anyone give me a step by step (yes i'm a noob) guide to transferring home to it's own partition ?

currently using 10.10, _not_ dual boot, so it should be really, really easy for you guys :)

---

### Post by DogMatix on 2010-11-19
I think this guide may help you out

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by flipper T on 2010-11-20
thx for reply,

have followed instructions but when i get to:

sudo mount -a

the following happens:

jason@jason-M570RU:~$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


any ideas ?

---

### Post by Verbeck on 2010-11-20
could you post the output of
```

cat /etc/fstab
```
and
```

sudo blkid
```

---

### Post by Backharlow on 2010-11-20
I have home on separate partition.
Here is the line in /etc/fstab that mounts the right partition as home:
```
# /dev/sda2
UUID=8452b46b-ca04-4f0c-a72d-a1653c545b0f /home           ext4    relatime        0       2

```
and the related line output of mount, once mounted:
```
/dev/sda2 on /home type ext4 (rw,relatime,commit=0)
```
don't know how helpful that is, but if you have ext4 instead of ext3 (which is used in that how to linked by DogMatix), my setting might be helpful.

---

### Post by flipper T on 2010-11-20
thx for prompt replies

having to postpone this project for a while as work interrupting my tinkering...grrr

will try again soon & repost,

thx

---

