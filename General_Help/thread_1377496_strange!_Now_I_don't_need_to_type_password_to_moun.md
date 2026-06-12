---
title: "strange! Now I don't need to type password to mount a hdd partition"
date: 2010-01-10
forum: General Help
---

### Post by nalinib on 2010-01-10
I am having a dual boot system vista/ubuntu 9.04.

Till recently whenever I wanted to access my vista partition I had to type in the administrative password.

However, strangely, for last few days whenever I access the vista partition I don't need to type the password.  The partition is just mounted and I can access the files.

I would like to know the reasons and if possible to get back the previous situation (needing password to access the vista partition).

---

### Post by nalinib on 2010-01-11
May I request the knowledgeable members to kindly respond.

---

### Post by sisco311 on 2010-01-11
What's the output of:
```
pkaction --verbose -a org.freedesktop.devicekit.disks.filesystem-mount
```
and
```
pkaction --verbose -a org.freedesktop.devicekit.disks.filesystem-mount-system-internal
```?

---

### Post by nalinib on 2010-01-11
I copy-pasted the command "pkaction --verbose -a org.freedesktop.devicekit.disks.filesystem-mount"

The output is "bash: pkaction: command not found"

Also I copy-pasted the command "pkaction --verbose -a org.freedesktop.devicekit.disks.filesystem-mount-system-internal"

The output is the same "bash: pkaction: command not found"

---

### Post by Ordes on 2010-01-11
u probably checked "remeber authorization forever"  [or sth like that] on accident...it happened to me once on jaunty...

if so, it is stored in "passwords and encryption keys", just delete it from there...

---

