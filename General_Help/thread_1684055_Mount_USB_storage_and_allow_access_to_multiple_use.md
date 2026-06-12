---
title: "Mount USB storage and allow access to multiple users"
date: 2011-02-08
forum: General Help
---

### Post by kitchens on 2011-02-08
Here's my situation: My wife and I both have profiles on my Ubuntu 10.10 system. We are both logged in at the same time and we switch from session to session. If I plug in my Ipod/USB storage while I'm logged in as me, the device mounts just fine. When I switch to her session I see an error that the device was unable to mount. She can't see the device. I have the same problem if the device is plugged in while she her desktop session is open. Then I can't see the device. Is it possible to make USB storage devices available to both users?

Thanks

---

### Post by djeikyb on 2011-02-08
You need to make an entry in fstab. Please post the output from these commands (make sure and use the code tags) while you are logged in and accessing the drive:

```
fdisk -l
ls -l /dev/disk/by-uuid/
df
```

---

### Post by kitchens on 2011-02-08
fdisk -l doesn't return any output.

```
user@pc:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2011-02-08 19:40 3434-3135 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2011-02-06 16:36 3ca27fdb-50f9-4437-b803-9098bba7615e -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-02-06 16:36 8d52c4e1-d941-4a41-b7c4-ecd2dfc37f0a -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-02-06 16:36 94b4d2b0-d35e-4852-b5be-7fa7bb2fde4e -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-02-06 16:36 98a84ece-3509-42e6-b663-b718589706c8 -> ../../sda1

```
Robot is the device I'm interested in. 
```
user@pc:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            230529188   6665748 212153232   4% /
none                   2021076       316   2020760   1% /dev
none                   2027932      2500   2025432   1% /dev/shm
none                   2027932       256   2027676   1% /var/run
none                   2027932         0   2027932   0% /var/lock
/dev/sdb1            961432072 276935836 635658236  31% /home
/dev/sdc1            480719056 171383244 284916612  38% /media/Backup
/dev/sdd1              7753728   7065280    688448  92% /media/ROBOT

```

---

### Post by djeikyb on 2011-02-08
Bugger. That should have been `sudo fdisk -l`. Oh well. There may well be a fancy Ubuntu tool for doing this I don't know about, but the old school way is directly editing /etc/fstab.


Make a folder and give everyone in the ipod group permission to read and write it:
```

mkdir /media/ipod
chown :ipod /media/ipod
chmod 660 /media/ipod

```

Make a group called ipod and add both your accounts to it:
```

groupadd ipod
usermod -G ipod husband
usermod -G ipod wife

```

Open fstab as an administrator. Something like:
```

sudo gedit /etc/fstab
OR
sudo vim /etc/fstab

```

Now add this line at the end:
```

UUID=3434-3135    /media/ipod    vfat    user,noauto,relatime    0  0

```

---

### Post by Tharquil on 2011-06-05
Thanks for the instructions. It worked for me with a few modifications. (To begin with, most of theses commands ask for root privileges and you have to sudo them.)

First thing to do is to add the new proup `ipod' or else the chown command will fail. Be careful to pass along the `-a' option to the usermod commands to restrict operations to the append mode or else you'll end up with ipod being the only group you are a member of:
```
groupadd ipod
usermod **-a** -G ipod husband
usermod **-a** -G ipod wife
```

Then create the mount point /media/ipod as indicated.

Finally, modify your /etc/fstab file (it is always wise to backup it first) using the `users' option instead of `user':
```
UUID=3434-3135    /media/ipod    vfat    **users**,noauto,relatime    0  0
```

Note: I applied these instructions to a usb hard drive formatted with an ext4 partition and I had to apply the chown command to it (once it was mounted) for the changes to be effective. Also, I had to give exec rights with the chmod command (i.e. chmod 770) or else I could not `cd' into the filesystem.

---

