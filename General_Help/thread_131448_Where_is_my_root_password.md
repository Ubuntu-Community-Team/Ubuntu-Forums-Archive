---
title: "Where is my root password??"
date: 2006-02-16
forum: General Help
---

### Post by Slurm on 2006-02-16
OK, first I checked the FAQ before I posted this.

I have loaded Ubuntu 3 times and NEVER does it ask for a root password.  I am blocked out of myown system which has sort of an odd 'twighlight zone' feel to it.  

What is going on??

---

### Post by aysiu on 2006-02-16
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by rosvit on 2006-02-16
check this: [http://ubuntuforums.org/archive/index.php/t-34089.html](http://ubuntuforums.org/archive/index.php/t-34089.html)

---

### Post by carlosqueso on 2006-02-16
EDIT: Dang, third place...I'm too slow.

---

### Post by towsonu2003 on 2006-02-16
root password = your own password

check out wiki.ubuntu.com/RootSudo

---

### Post by alfonz on 2006-02-16
default install doesn't assing and/or create a root user and password.

You can access root privelages temporarly via the sudo command. This requires your user password.


if you really want to create a root password then open terminal and type:
```
sudo passwd root
```

---

### Post by towsonu2003 on 2006-02-16
[QUOTE=carlosqueso]EDIT: Dang, third place...I'm too slow.[/QUOTE]
lol

---

