---
title: "useradd -ed a user, now cant remove"
date: 2011-07-16
forum: General Help
---

### Post by vangop on 2011-07-16
Hi!
I added a user. Wanted it to belong to my group (not create his own primary grp), and wanted him to have a UID <1000
```
$ sudo useradd -mN -g akm -K UID_MAX=900 nektois
```

It created a user, but gave it 1000 uid (same as my primary user).
Now can't change it,or delete the user. 
The user got deleted ok via gui, but /etc/passwd already has it:
```
$ grep nekto /etc/passwd 
nektois:x:1000:1000::/home/nektois:/bin/sh
```

Why did this happen? And more - how can I remove the user??

---

### Post by bhinderm on 2011-07-16
What happens if you try "sudo userdel nekto" ?

---

### Post by bhinderm on 2011-07-16
Sorry "sudo userdel nektois"

---

### Post by vangop on 2011-07-16
$ sudo userdel nektois
userdel: user nektois is currently logged in

which is because it got somehow 1000 uid. which is mine.

---

### Post by bhinderm on 2011-07-16
That is pretty strange, have you considered filing a bug for it? 

One sure way to delete the user would be to boot into recovery mode from the grub menu and then run the userdel command from there. You could also delete the line for the user from /etc/passwd, /etc/group and /etc/shadow and also remove the home folder manually. I'm sure there are better ways to do this but that's all I can think of :-(

---

### Post by ajgreeny on 2011-07-16
So are both users UID 1000 at the moment, or has your first user (you) changed to another UID?  I can not see how you can both have UID 1000.

Very strange!!

---

### Post by vangop on 2011-07-17
My user is akm (1000:1000).
I only created the nektois with the command above. Haven't touched anything else. The user's home dir was deleted via gui applet (users and groups).
So I'll clean /etc/passwd and /etc/shadow manually, looks like the only way..

---

