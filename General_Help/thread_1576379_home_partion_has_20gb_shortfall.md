---
title: "/home partion has 20gb shortfall"
date: 2010-09-17
forum: General Help
---

### Post by sundays211 on 2010-09-17
my /home partition, according to gparted, has 29.60gb used out of 31.99gb. but by analyzing through disk-usage-analyzer only 9.1gb has been used. what is using this additional 20gb of disk space and how can I get rid of it as my disk is nearly full.

---

### Post by plucky on 2010-09-17
> **sundays211 said:**
> my /home partition, according to gparted, has 29.60gb used out of 31.99gb. but by analyzing through disk-usage-analyzer only 9.1gb has been used. what is using this additional 20gb of disk space and how can I get rid of it as my disk is nearly full.

From a terminal post output of ```
df -h
```

See this [Howto check Trash when disk full Tutorial](http://ubuntuforums.org/showthread.php?t=898573&highlight=trash+drs305)

Good Luck

---

### Post by sundays211 on 2010-09-17
output of "df -h":

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              12G  4.1G  7.1G  37% /
none                  735M  376K  734M   1% /dev
none                  739M   88K  739M   1% /dev/shm
none                  739M  348K  738M   1% /var/run
none                  739M     0  739M   0% /var/lock
none                  739M     0  739M   0% /lib/init/rw
/dev/sda6              32G   27G  2.9G  91% /home
/dev/sdb3             478M   61M  392M  14% /boot

```

---

### Post by sundays211 on 2010-09-17
looking at the file about my trash, it seems as though all the files I thought I removed completely (even by emptying my trash) a long time ago are still here. the issue now is that every time I remove them form the directory (as root) they just come back! removing from the terminal works permanently, but it seems to not be able to remove directories.

EDIT: using rm -r * seems to work. now if I can just stop Ubuntu from keeping the files I have dumped from my personal trash bin!

oh, and thanks for your help

---

