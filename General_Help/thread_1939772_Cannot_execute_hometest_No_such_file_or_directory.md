---
title: "Cannot execute /home/test: No such file or directory"
date: 2012-03-12
forum: General Help
---

### Post by meduser on 2012-03-12
added a user using useradd testuser,

now when I try to go su -
password:XXXXXXXXXX
I get the following message:

Cannot execute /home/test: No such file or directory

any help is greatly appreciated

---

### Post by ajgreeny on 2012-03-12
> **meduser said:**
> added a user using useradd testuser,

now when I try to go su -
password:XXXXXXXXXX
I get the following message:

Cannot execute /home/test: No such file or directory

any help is greatly appreciated
For a start, ubuntu does not normally use the standard root account, so using the command **su** will not work (see Root-sudo link in my signature).  If you wanted to add a user you would need to preface the command with "sudo"

Can you show the output of ```
ls -l /home
``` so we can see what users there really are on your machine.

---

### Post by Suparious on 2012-03-12
have a look at the shell setting in /etc/passwd:

```
grep test /etc/passwd
```

if you see a "/home/test" at the end of that result, then you set the shell to that users home directory instead of '/bin/bash' or '/bin/sh'.

To change that user's shell to BASH:

```
sudo usermod -s /bin/bash test
```

---

### Post by meduser on 2012-03-12
> **Suparious said:**
> have a look at the shell setting in /etc/passwd:

```
grep test /etc/passwd
```

if you see a "/home/test" at the end of that result, then you set the shell to that users home directory instead of '/bin/bash' or '/bin/sh'.

To change that user's shell to BASH:

```
sudo usermod -s /bin/bash test
```

that worked perfectly, thank you.

---

