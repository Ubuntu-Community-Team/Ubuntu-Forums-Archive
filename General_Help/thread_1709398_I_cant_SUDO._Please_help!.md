---
title: "I cant SUDO. Please help!"
date: 2011-03-18
forum: General Help
---

### Post by TheBishopOfSoho on 2011-03-18
Hi there, I have Ubuntu 10.10 64bit desktop edition which has been working fine for the past week but since yesterday I can no longer sudo. I dont know what has happened to change this but how do I fix it? Ive checked the sudoers file and it looks identical to the documentation. Ive manually added my username to the /etc/group file for the admin group from the live cd but its not showing up in id. Here is the relevant info:
id shane
```
uid=1000(shane) gid=1000(shane) groups=0(root),1000(shane)

```

cat /etc/group (trimmed)
```
uid=1000(shane) gid=1000(shane) groups=0(root),1000(shane)

```

cat /etc/sudoers
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by TheBishopOfSoho on 2011-03-18
Oops, the /etc/ group output shoud be 
```

utempter:x:116:
rtkit:x:117:
saned:x:118:
**admin:x:119:shane,root**
gdm:x:120:
nopasswdlogin:x:121:
shane:x:1000:


```

---

### Post by TheBishopOfSoho on 2011-03-18
I solved this myself using the live CD. I merely replaced the /etc/group with the backup /etc/group- and then chmod 644 the file and rebooted and everything works again!

---

