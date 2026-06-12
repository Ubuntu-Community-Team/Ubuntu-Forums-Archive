---
title: "change write access of files inside a folder"
date: 2011-01-17
forum: General Help
---

### Post by shantiq on 2011-01-17
ok trying to use **grip** but it keeps giving me this message



```
No write access to write encoded file
```

so i have a folder in my home folder called flac and i want to modify the folder so that all files within can be written to

i have tried

```
chmod -R 777 flac/*
```

and

```
chmod -R 755 flac/*

```


also   ```
sudo chmod -R a+rwx flac

```


and still not what i want

files within the flac folder still cannot Be written to see image 1

what i want to have should look like (i think) this   at the moment when i click on
Apply Permissions To Enclosed Files    resets it to the way it is in picture 1


How can i change this so it remains with write and read access for all files within



thanx    shan

---

### Post by Lukiwuki on 2011-01-17
try
> sudo chmod -R 777 flac/ 
Without the *

---

### Post by WorMzy on 2011-01-17
Can you post the output of ```
ls -ld ~/flac
``` and also ```
mount
```

---

### Post by Lukiwuki on 2011-01-17
try
> sudo chmod -R 777 flac/ Without the *

---

### Post by Lukiwuki on 2011-01-17
try
> sudo chmod -R 777 flac/ Without the *

---

### Post by Lukiwuki on 2011-01-17
try
> sudo chmod -R 777 flac/ 
Without the *

---

### Post by Lukiwuki on 2011-01-17
try
> sudo chmod -R 777 flac/ Without the *

---

### Post by Lukiwuki on 2011-01-17
Sry, ma Laptop postet multiple times :(

---

### Post by shantiq on 2011-01-17
wormzy

output is    ```
drwxrwxrwx 3 shantiq shantiq 4096 2011-01-17 17:37 /home/shantiq/flac

```


and for mount


```
mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shantiq/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shantiq)

```




thanks lukiwuki but removing the wildcard made no difference

---

### Post by WorMzy on 2011-01-17
Well, permissions look fine, and you haven't done anything silly like tried to use an NTFS partition as your home folder, so the next thing that comes to mind is: how are you running the application in question? I've never used grip myself, but are you sure that you've configured it correctly?

---

