---
title: "Can't figure out how to get non-root user to own ntfs drive"
date: 2009-08-25
forum: General Help
---

### Post by josephellengar on 2009-08-25
I got a new computer that has two drives, including one 500gb drive that has to be formatted to ntfs.  I have to be able to write to this drive when I am not a root user, and as of now I have been unable to figure out how to do that through the fstab.  Currently, this is the line in my fstab that I have.  Any suggestion?

/dev/sdb1       /home/ross/storage ntfs   users 0 0

---

### Post by oldos2er on 2009-08-25
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by blueridgedog on 2009-08-25
In the following substitute you user name for USER.

Unmount the drive

```
sudo umount /home/ross/storage
```

Your user ID on the system is probably 1000, but it is easy to check:

```
cat /etc/passwd | grep USER
```

If your user ID is anything other than 1000, change it in the mount option below.

Edit /ect/fstab to mount the drives with user IDs
```

gksudo gedit /etc/fstab
```

Add The following line:

```
/dev/sdb1 /home/ross/storage ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1

```

Save the file then mount them with

```
sudo mount /home/ross/storage
```

If you don't have ntfs-3g installed, install it with synaptic.

---

