---
title: "/var/lib/dpkg/lock Problem"
date: 2010-04-07
forum: General Help
---

### Post by iXD on 2010-04-07
Ive been trying to install something using

```
 sudo apt-get ... 
```And i get this:

```
 E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```And yes, i am the root, i am the only user on my laptop.

I am a noob at Ubuntu so be friendly.

P.S i accidentally deleted /var/lib/dpkg/lock - Only the lock file and i cant get it back D;

Please help!

---

### Post by gzarkadas on 2010-04-07
Post the output of the following commands (use Ctrl+Shift+C to copy from the terminal window):
```
mount
```and
```
ls -l -a /var/lib/dpkg
```

---

### Post by iXD on 2010-04-07
Ok, terminal look from 
```
mount
```
```
chris@chris-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
```

Terminal from
```

ls -l -a /var/lib/dpkg
```
```
chris@chris-laptop:~$ ls -l -a /var/lib/dpkg
total 5680
drwxr-xr-x  7 root root    4096 2010-04-07 18:58 .
drwxr-xr-x 58 root root    4096 2010-03-20 16:21 ..
drwxr-xr-x  2 root root    4096 2010-04-07 18:53 alternatives
-rw-r--r--  1 root root 1360770 2010-04-07 18:53 available
-rw-r--r--  1 root root 1360770 2010-04-07 18:53 available-old
-rw-r--r--  1 root root       8 2009-10-28 20:55 cmethopt
-rw-r--r--  1 root root     338 2010-02-20 00:55 diversions
-rw-r--r--  1 root root     376 2010-02-20 00:49 diversions-old
drwxr-xr-x  2 root root  266240 2010-04-07 18:53 info
drwxr-xr-x  2 root root    4096 2009-09-20 09:23 parts
-rw-r--r--  1 root root      65 2009-10-28 21:02 statoverride
-rw-r--r--  1 root root      30 2009-10-28 21:01 statoverride-old
-rw-r--r--  1 root root 1385620 2010-04-07 18:53 status
-rw-r--r--  1 root root 1385492 2010-04-07 18:53 status-old
drwxr-xr-x  2 root root    4096 2010-04-07 18:47 triggers
drwxr-xr-x  2 root root    4096 2010-04-07 18:53 updates
chris@chris-laptop:~$ 
```

Thanks.

---

### Post by nem75 on 2010-04-07
iXD: you deleted the lock file and still cannot run apt-get? If so, are other instances of apt-get, synaptic etc. running? You can only run one apt frontend at a time, the first one you run creates the lock file and those started afterwards complain about it.

---

### Post by iXD on 2010-04-07
No, i dont think i have.

I did just do a search for files named lock:

lock - located in the firefox directory.
.gksu.lock - located .. doesnt say.
fdb.lock - located in a folder called .config/tomboy/addin-db-001 (i have never seen this before o.O)

Will any of these be the problem?

---

### Post by nem75 on 2010-04-08
No, apt-get (and the underlying dpkg) is only interested in /var/lib/dpkg/lock

---

### Post by gzarkadas on 2010-04-08
Try this (to recreate the lock file with appropriate size and permissions):
```

sudo -i
cd /var/lib/dpkg
: > lock
chmod 640 lock
exit

``` and then rerun apt-get; does it solve the issue?

---

### Post by Soul-Sing on 2010-04-08
prob. you more than one software manager/-apt/dpkg open/running.
otherwise try: 
cd /var/lib/dpkg/
mv status status.broken
cp status-old status

---

