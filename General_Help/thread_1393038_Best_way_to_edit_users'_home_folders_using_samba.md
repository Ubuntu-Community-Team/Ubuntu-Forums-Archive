---
title: "Best way to edit users' home folders using samba"
date: 2010-01-28
forum: General Help
---

### Post by theman on 2010-01-28
A teacher needs the ability to view and edit the students' home folders. The students can't see each other's home folder though.

```

[homes]
    comment = Home Directories
    browseable = no
    writable = yes
    valid users = %S

```Here are my two solutions:


```
chmod -R 777 /home
``````
[student profiles]
    comment = student profiles
    path = /home
    writeable = no
    write list = 100, david
    valid users = 100, david
```OR

```
chmod -R 755 /home
``````
[student profiles]
    comment = student profiles
    path = /home
    writeable = no
    valid users = 100, david
    admin users = 100, david
```Both of these solutions aren't ideal though. I don't like have the /home directory so open and I also don't like the teacher being logged in as root since the files he creates will be owned by root. Would that affect the student's ability to edit the file?

Would putting "directory mask" override the unix permissions?

---

