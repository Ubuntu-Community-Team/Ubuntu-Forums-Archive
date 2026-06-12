---
title: "Samba - create mask does not work"
date: 2009-09-29
forum: General Help
---

### Post by krowa on 2009-09-29
Hi, 

 I decided to put files on the samba server. I installed the samba and configured it as follows: 
```

[global]
  workgroup = DOM
  server string = ruter
  security = user
  log file = /var/log/samba/log.%m
  max log size = 50
  socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
  os level = 60
  dns proxy = no 
  display charset = UTF8
  unix charset = UTF8 
  dos charset = CP852

[test]
  path = /test
  valid users = user
  public = no
  writable = yes
  create mask = 0664

```

 Now it is time for tests. Well, on a computer with windows client, everything is ok, files are created with a mask of 0664: 

```

user@delta:~$ ls -l /test/
razem 0
-rw-rw-r-- 1 user root 0 2009-09-28 12:58 New document.txt

``` 

But now, I mount it on Ubuntu client:
```

sudo mount --verbose -t smbfs //ruter/test/ /test/ -o user=user,uid=user,gid=user,iocharset=utf8,file_mode=000,dir_mode=000

``` 
 and if linux user, try to create a "test" it will mask was 0644 

```
rw-rw-r-- 1 user root 0 2009-09-28 12:58 Nowy Dokument tekstowy2.txt
-rw-r--r-- 1 user root 0 2009-09-28 13:10 test
``` My question is why? 
I tried mount with parameter umask=000 on linux, but it does not get effect. Files form linux client still are create witch mask 0644.
How do users of Linux that also created files with a mask of 0664? Perhaps the solution is trivial but it somehow stuck, please help. 

 Yours

---

### Post by Iowan on 2009-09-29
000 *removes* no permissions, but does not add any.  (maybe my cold medicine has affected my understanding of your problem...)

---

