---
title: "synaptic don't load, E: The value 'natty-updates' is invalid for APT::Default-Release"
date: 2011-12-28
forum: General Help
---

### Post by nadavvin on 2011-12-28
ubuntu 11.10

I search for natty in the whole filesystem and didn't find anything:

```

:/# find bin boot etc lib lost+found opt root run sbin srv selinux var usr -print0|grep -v *.log|xargs -0 grep natty 2>&1|grep -v 'No such file or directory'
grep: Binary file (standard input) matches

```

---

### Post by plucky on 2011-12-28
> **nadavvin said:**
> ubuntu 11.10

I search for natty in the whole filesystem and didn't find anything:

```

:/# find bin boot etc lib lost+found opt root run sbin srv selinux var usr -print0|grep -v *.log|xargs -0 grep natty 2>&1|grep -v 'No such file or directory'
grep: Binary file (standard input) matches

```

Post ```
cat /etc/apt/sources.list
```

---

### Post by nadavvin on 2011-12-29
```

$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main
deb http://archive.ubuntu.com/ubuntu oneiric main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted universe multiverse

deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner
deb http://security.ubuntu.com/ubuntu/ oneiric-security restricted main multiverse universe


```

---

### Post by plucky on 2011-12-29
That looks OK,
What have you got in /etc/apt/sources.list.d

```
cat /etc/apt/sources.list.d/*.list
```

---

### Post by nadavvin on 2011-12-29
```


$ cat /etc/apt/sources.list.d/*.list
deb http://ppa.launchpad.net/cardapio-team/unstable/ubuntu oneiric main
deb-src http://ppa.launchpad.net/cardapio-team/unstable/ubuntu oneiric main
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu oneiric main
deb-src http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu oneiric main



```

---

### Post by plucky on 2011-12-29
That looks ok,

What does ```
sudo apt-get update
``` show you?

---

### Post by nadavvin on 2011-12-29
```

sudo apt-get clean
sudo apt-get update

```

message still appear

---

### Post by plucky on 2011-12-29
Try ```
sudo rm /var/lib/apt/lists/* -vf
``` Then run ```
sudo apt-get update
``` to reload the list files.

---

### Post by nadavvin on 2011-12-29
did it, message still appear

---

### Post by plucky on 2011-12-29
> **nadavvin said:**
> did it, message still appear

I am at a loss for what is causing it,did you just upgrade from Natty to Oneiric?

Did the Upgrade Complete?

**If it didn't complete,it might be worth a fresh install**

Try ```
sudo dpkg --configure -a
```

Can you post the complete messages as there might be something in the messages that you are not seeing.

---

