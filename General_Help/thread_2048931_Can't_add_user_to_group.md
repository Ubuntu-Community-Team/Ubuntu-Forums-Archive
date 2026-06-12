---
title: "Can't add user to group"
date: 2012-08-27
forum: General Help
---

### Post by elemings on 2012-08-27
Can anyone explain the following commands and/or recommend a solution?  Thanks.

```
$ uname -a
Linux ubuntu1204vm 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
$ id
uid=1000(flh) gid=1000(flh) groups=1000(flh),27(sudo)
$ groupadd -f xyz
$ echo $?
0
$ sudo usermod -aG xyz flh
$ id
uid=1000(flh) gid=1000(flh) groups=1000(flh),27(sudo)
$ sudo adduser flh xyz
The user `flh' is already a member of `xyz'.
$ id
uid=1000(flh) gid=1000(flh) groups=1000(flh),27(sudo)
$ mkdir /tmp/test
$ sudo chown root:xyz /tmp/test
$ sudo chmod 775 /tmp/test
$ ls -alR /tmp/test
/tmp/test:
total 8
drwxrwxr-x  2 root xyz        4096 Aug 22 18:29 .
drwxrwxrwt 17 root root       4096 Aug 22 18:29 ..
$ touch /tmp/test/foo
touch: cannot touch `/tmp/test/foo': Permission denied

```

---

### Post by spjackson on 2012-08-27
The current session does not acquire the new group. You need to login for the new group to become effective for your new session.

---

### Post by elemings on 2012-08-27
Of course.  I knew that.  (Or should have.)  :P  Thanks.

---

