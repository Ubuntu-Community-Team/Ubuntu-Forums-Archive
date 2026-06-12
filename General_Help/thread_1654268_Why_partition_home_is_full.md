---
title: "Why partition home is full"
date: 2010-12-28
forum: General Help
---

### Post by benohb on 2010-12-28
Please help
ubuntu 10.04
kernel 2.6.36

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             17301912   4858836  11564180  30% /
proc                         0         0         0   -  /proc
none                         0         0         0   -  /sys
none                         0         0         0   -  /sys/fs/fuse/connections
none                         0         0         0   -  /sys/kernel/debug
none                         0         0         0   -  /sys/kernel/security
none                    507668       228    507440   1% /dev
none                         0         0         0   -  /dev/pts
none                    512172       180    511992   1% /dev/shm
none                    512172       196    511976   1% /var/run
none                    512172         0    512172   0% /var/lock
none                    512172         0    512172   0% /lib/init/rw
/dev/sda3              7689384   7073076    616308  92% /home
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon             0         0         0   -  /home/hb/.gvfs
``` ls home
```
hb  lost+found
```"home" is  partition with 8gb
"hb" is my space With baobab disk usage analyzer the size of "hb" folder = 1.8 gb

Why partition home is full:confused:

---

### Post by dabl on 2010-12-28
In terminal:

```
cd /home
```

Or, if you are the only user on that computer, and assuming your user name is "ben", then

```
cd /home/ben
```

Next:

```
du -h --max-depth=1 | sort -n
```

Look at the output, which is sorted by size of directories. It will tell you where there is a lot of files.  Change to that directory and see what you can delete, using "rm".

---

### Post by benohb on 2010-12-28
```
1.8G    ./hb
4.9G    ./.Trash-0
6.7G    .
16K    ./lost+found

```

yes yes.... Thank you
I empty the trash ...
There was another user, and i delete it
how I empty the trash..?

---

### Post by benohb on 2010-12-28
Where is the folder ./.Trash-0. ..?

Does not exist 'hb' ,It exists in 'home'...:-k

---

### Post by benohb on 2010-12-28
The problem has been resolved
Thank you

```
cd /home
ls -a
sudo rm -r .Trash-0
```

---

