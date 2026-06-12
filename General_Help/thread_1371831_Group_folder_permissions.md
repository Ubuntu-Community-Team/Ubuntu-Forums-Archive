---
title: "Group folder permissions"
date: 2010-01-03
forum: General Help
---

### Post by mcgrmic2 on 2010-01-03
I cannot access folders even though I am a member of owning group "sysadmin" and the permissions are set up properly.

```
mcgregor@srvr001:~$ groups mcgregor
mcgregor : sysadmin adm dialout cdrom plugdev mcgregor lpadmin sambashare admin
```but when I try to access or view files (eg ls -l)

```
mcgregor@srvr001:~$ ls -l /var/media
ls: cannot access /var/media/lost+found: Permission denied
ls: cannot access /var/media/help: Permission denied
total 0
-????????? ? ? ? ?                ? help
d????????? ? ? ? ?                ? lost+found

```but if I "sudo !!"

```
mcgregor@srvr001:~$ sudo !!
sudo ls -l /var/media
total 20
-rwxrw-r-- 1 root sysadmin     6 2009-12-31 00:47 help
drwxrw-r-- 2 root sysadmin 16384 2009-12-30 21:59 lost+found

```Even disregarding the group association, the file is set to read by everyone else, but I can't read or access it. 

I have already logged out/in, and even rebooted the server before posting this. Can anyone help?

---

### Post by mcgrmic2 on 2010-01-03
Anybody? This problem is rather difficult to fix and pretty frustrating.

---

### Post by jonest1 on 2010-01-03
What are the permissions on /var/media.

Do the following and reply with the output.

```
ls -ld /var/media
```

---

### Post by mcgrmic2 on 2010-01-04
```
mcgregor@srvr001:~$ sudo ls -ld /var/media
[sudo] password for mcgregor: 
drwxrw-r-- 3 root sysadmin 4096 2010-01-03 18:52 /var/media

```

---

### Post by mcgrmic2 on 2010-01-04
*bump*

---

### Post by 0x29a on 2010-01-04
The reason that you can't see beyond /var/media is that it's not executable to the sysadmin group or mcgregor, therefore can't be entered by these entities. Root, of course, has full access. Try changing the permissions to 775:
```
$ sudo chmod 775 /var/media
```
or
```
# chmod 775 /var/media
```

This will make it read/writable/executable by sysadmin, and readable/executable by mcgregor. Remember that directories must be executable to unpriviledged users to even list their contents, or enter them.

Hope this helps. Good luck!

---

