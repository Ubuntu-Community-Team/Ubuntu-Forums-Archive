---
title: "Mounting samba share"
date: 2010-02-08
forum: General Help
---

### Post by ztrange on 2010-02-08
I want to mount a samba share form another Ubuntu pc.

With nautilus I can do:
smb://xxxxxxx;username@192.168.1.12/sharedfolder/
And i can browse the shared folder without problem

but I want to mount it. I have tried:
```

user@compu:~$ sudo mount -t smbfs //192.168.1.12/sharedfolder /mnt/folder -o username=username
mount: wrong fs type, bad option, bad superblock on //192.168.1.64/esco3,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and also:
```

user@compu:~$ sudo mount -t cifs //192.168.1.12/sharedfolder /mnt/folder -o username=username
mount: block device //192.168.1.64/esco3 is write-protected, mounting read-only
mount: cannot mount block device //192.168.1.64/esco3 read-only

```

Im aware I'm not passing the password and I was hoping it would ask me. Also I'd like to store all that info in my computer and try to auto mount the shared every time i use the pc.

Thaks in advance

---

### Post by Merlinson on 2010-02-08
Hi,

Following this thread solved all my share issues.  I only needed to do the first couple up to firewall issues.

Good luck.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by ztrange on 2010-02-10
I managed to solve it installing i don't know what package that contains smbmount but i think its the same as mount -t cifs:

```
user@pc:~$ sudo smbmount //192.168.1.12/shared /home/user/mnt/shared/ -o credentials=/home/user/.smbpass 
```

And /home/user/.smbpass
contains simply:
```
username=user1
password=password1
```


It's not a very secure way to do it but I don't need a great security for it.

Thanks for your help

---

### Post by ztrange on 2010-02-10
After solving my problem, I found this thread and left it for later reading. But is very very well explained.

[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

