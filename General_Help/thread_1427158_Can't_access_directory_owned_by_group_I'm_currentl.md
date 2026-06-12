---
title: "Can't access directory owned by group I'm currently a member of."
date: 2010-03-11
forum: General Help
---

### Post by Munkoil on 2010-03-11
Hello,

I've been playing around with file access rights in linux because I need a directory that only two users can read and write in.

My user already exist, I call it myuser in this example. I created another user called seconduser using
```
groupadd seconduser
useradd -g seconduser seconduser
```

I've added a group using
```

groupadd mygroup

```

Then I added myself and the other user to mygroup using
```
usermod -a -G mygroup myuser
usermod -a -G mygroup seconduser
```

Then I create a dir
```
mkdir /share
chmod 770 /share
chgrp mygroup /share

```

When I try to access i get the following error:
```
myuser@ubuntu:/$ cd share/
bash: cd: share/: Permission denied
```

This is some commands and their output:
```
myuser@ubuntu:/$ id myuser
uid=1000(myuser) gid=1000(myuser) groups=1000(myuser), 4(adm),20(dialout),
24(cdrom),46(plugdev),104(lpadmin),122(sambashare),1002(mygroup)

myuser@ubuntu:/$ cat /etc/group | grep mygroup
mygroup:x:1002:myuser:seconduser

myuser@ubuntu:/$ ls -l | grep share
drwxrwx---   2 root mygroup  4096 2010-03-11 11:23 share

```

What am I doing wrong? Can't I access files or folders of my secondary groups? I've also tried
```
chmod g+s /share
```
with no success.

---

### Post by cjhabs on 2010-03-11
I reproduced your scenario on my 9.10 system and it worked exactly as expected - not they way you are seeing. I can't see anything wrong with what you are doing - so no idea what is going on - sorry.

---

### Post by sisco311 on 2010-03-11
After adding your user to the group you have to log out & log back in.

---

### Post by Munkoil on 2010-03-11
> **sisco311 said:**
> After adding your user to the group you have to log out & log back in.

Thanks for the tip! This solved the problem. I thought restarting the gnome console would do it but I needed to log out and then back in again! Now everything works as expected.

---

