---
title: "sudo without passwords"
date: 2006-02-16
forum: General Help
---

### Post by rkakkar on 2006-02-16
is there anyway i can disable sudo to ask for a password for a particular set of commands?

---

### Post by sbassett on 2006-02-16
Yes. But be aware this is not advisable, and dramatically lowers the effectiveness of linux's security. That being said:

sudo gedit /etc/sudoers

and ADD the following to the end, do not replace anything listed or you may not be able to sudo ever again without booting into recovery mode.

```
username ALL= NOPASSWD: /path/to/program
```

replace username with the desired user's name, and replacing /path/to/program with the actually path to program (i.e. /usr/bin/mount)

Save and you should be set, simply repeat the entry for each program that will be run without password. Be sure your firewalls are in top shape, and that your physical pc is safe from unintended use as well.

---

