---
title: "fdisk have limited support for filesystems"
date: 2009-08-20
forum: General Help
---

### Post by zainka on 2009-08-20
Hi

Why can  i only see the following file systems listed when trying to format a disk (see CODE section). If this is standard for Ubuntu, then why limit the system this way? I am no SunOS fan. Totally useless if asking me, but who does...

:confused:

```
me@my-laptop:/dev$ sudo fdisk /dev/sdb

Command (m for help): l

 0  Unassigned       4  SunOS usr        8  SunOS home      82  Linux swap     
 1  Boot             5  Whole disk       9  SunOS alt secto 83  Linux native   
 2  SunOS root       6  SunOS stand      a  SunOS cachefs   8e  Linux LVM      
 3  SunOS swap       7  SunOS var        b  SunOS reserved  fd  Linux raid auto


```

---

### Post by zainka on 2009-08-20
Hi

After some hours struggling i finaly found that my card was locked. No warning given. 

After unlocked my card it gaved me the full list of file systems


#-o

---

