---
title: "chmod -R root:root /usr"
date: 2009-12-21
forum: General Help
---

### Post by dagarwal82 on 2009-12-21
Hi,
I was upto something and issued 'chmod -R root:root /usr' :(

Now, how to revert it back? At least the system dirs/files could be reverted back somehow...

Linux deepak-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

---

### Post by dagarwal82 on 2009-12-21
Anyone? I am stuck with most of things not working (due to invalid permissions)

---

### Post by Vaphell on 2009-12-21
you used chmod instead of chown to set root as an owner? It's like that by default if i am not mistaken, so there was no need to do that in the first place

terminal:
```
cd /usr
ls -l
```
and see what ownership/permissions are

---

### Post by dagarwal82 on 2009-12-21
you are right , It was 'chown'. (typo)
all the dirs and files have 
drwxr-xr-x    root root

---

### Post by Vaphell on 2009-12-21
on my box every single directory in /usr is owned by root (find /usr -type d ! -user root -print returns 0 results), i don't know what could happen to mess your system up.

check if stuff located in /usr has permissions set to 755 (rwxr-xr-x) for executables and 644 (rw-r--r--) for the rest

---

### Post by dagarwal82 on 2009-12-21
I remember doing : 'chmod -R 755 /usr' just after the chown command. ( I did it as to run an application accidentally).
so each file has rwxr-xr-x

---

### Post by stlsaint on 2009-12-21
so you changed ownership to root and what happened to crash the system?

---

### Post by sisco311 on 2009-12-21
chown clears the setuid/setgid attribute of the files (sudo, pkexec...).

@OP:
Backup and reinstall.

---

### Post by dagarwal82 on 2009-12-21
1) I click on Places->sda6 then lots of splashes (automatic Authentication failure) and then it displays unable to mount
2) Sound is gone
3) I don't see sound icon anymore, (System->Preferences->Sound shows 'waiting for sound system to respond'
4) pulseaudio won't start (displays "E: core-util.c: Home directory /home/deepak not ours.")

There might be a lot to it. 
So, right now I am just trying figure it out If there is such listing of permissions for the default system dir and files or any workaround.

"sda6" is my partition

---

### Post by dagarwal82 on 2009-12-21
> **sisco311 said:**
> chown clears the setuid/setgid attribute of the files (sudo, pkexec...).

@OP:
Backup and reinstall.
Yes, I was unable to run sudo and mount also , then  found this script to set some of the permission back to default (which worked for listed commands):
cd /usr/bin
chown root:root *
chown daemon:daemon at
chown root:tty bsd-write wall
chown root:shadow chage expiry
chown root:crontab crontab
chown root:mail dotlock.mailutils
chown root:lpadmin lppasswd
chown root:mlocate mlocate
chmod 4755 arping chfn chsh gpasswd lppasswd mtr newgrp passwd pulseaudio sudo sudoedit traceroute6.iputils
chmod 6755 at X
chmod 2755 bsd-write chage crontab dotlock.mailutils expiry mlocate screen ssh-agent wall xterm
cd /usr/sbin
chown root:root *
chown root:dip pppd
chown libuuid:libuuid uuidd
chmod 4754 pppd
chmod 6755 uuidd
cd /bin
chown root:root *
chown root:fuse fusermount
chmod 4754 fusermount
chmod 4755 mount ping ping6 su umount
cd /sbin
chown root:root *
chown root:shadow unix_chkpwd
chmod 2755 unix_chkpwd
chmod 4755 mount* umount*

---

### Post by dagarwal82 on 2009-12-23
There is still some problem with the permission (since the setuid got changed) but after doing 1 or 2 restart I am able to do most of the work (90%). But I had to degraded the permissions from auth_admin_keep to 'yes' in few of the files under /usr/share/polkit-1/actions/ directory. If anyone has some clue what might have gone wrong and a script or something to get every permissions back then It would be appreciable.

---

### Post by dcstar on 2009-12-24
> **dagarwal82 said:**
> There is still some problem with the permission (since the setuid got changed) but after doing 1 or 2 restart I am able to do most of the work (90%). But I had to degraded the permissions from auth_admin_keep to 'yes' in few of the files under /usr/share/polkit-1/actions/ directory. If anyone has some clue what might have gone wrong and a script or something to get every permissions back then It would be appreciable.

Boot off a Live CD and copy that /usr to the hard drive, or just examine its settings and manually change the others.

Or simply stop wasting time and do a reinstall (and learn your lesson).

---

