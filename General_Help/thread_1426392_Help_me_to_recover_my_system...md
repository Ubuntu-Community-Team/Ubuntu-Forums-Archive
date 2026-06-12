---
title: "Help me to recover my system.."
date: 2010-03-10
forum: General Help
---

### Post by karthick87 on 2010-03-10
I am a begginner,by mistake i opened **Users and Groups ** (System-->Administration-->Users and Groups) and i unlocked the settings by entering my password and i have unticked the option **administer my system**.After a restart i cant able to use sudo command and some options were vanished from my system..Now when i click User and Groups it shows an error window..Pls someone help me to recover it to previous state..

---

### Post by nothingspecial on 2010-03-10
Boot into a root recovery shell and type

```
adduser username admin
```

Change username for your actual username.

Reboot

---

### Post by karthick87 on 2010-03-10
How to boot into root recovery shell?

---

### Post by nothingspecial on 2010-03-10
reboot and hold down shift

---

### Post by karthick87 on 2010-03-10
root@Learners-desktop:~# adduser test admin
adduser: The user `test' does not exist.

---

### Post by nothingspecial on 2010-03-10
Is your username test?

---

### Post by karthick87 on 2010-03-10
Sorry username is not test...
karthick@Learners-desktop:~$ sudo adduser karthick  admin
Adding user `karthick' to group `admin' ...
Adding user karthick to group admin
Multiple entries named 'admin' in /etc/group. Please fix this with pwck or grpck.
gpasswd: can't update entry
adduser: `/usr/bin/gpasswd -a karthick admin' returned error code 1. Exiting.

---

### Post by nothingspecial on 2010-03-10
Post the output of ```
cat /etc/group | grep admin
```

---

### Post by karthick87 on 2010-03-10
karthick@Learners-desktop:~$ cat /etc/group | grep admin
lpadmin:x:106:karthick
admin:x:121:
admin:x:117:karthick

---

### Post by nothingspecial on 2010-03-10
Ooops You have 2 admin groups. That`s not good. You will have to remove one of them. I am not sure which one. I would think the one with gid 121.

I am only 95% sure of this and don`t want to give you advice that will break your system further.

I`d remove 121 if it were me, but like I said, I`m not 100% sure on this.

---

### Post by karthick87 on 2010-03-10
I removed gid 121,now everything was alright...Thanks a lot :)

---

### Post by nothingspecial on 2010-03-10
Glad we got it sorted :D

---

