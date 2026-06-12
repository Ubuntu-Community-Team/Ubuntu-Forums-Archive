---
title: "No More Hard Disk Space"
date: 2011-03-17
forum: General Help
---

### Post by Richiegs on 2011-03-17
I set up a Windows partition and an Ubuntu partition in my laptop and  each partition has about 60 GB of disk space. Recently I keep  getting messages that the disk space in my Ubuntu partition is almost  full. How is it possible since I only have computer programs in that partition which  I  absolutely need? What can I do to solve this problem besides buying a  larger hard disk? Many thanks

---

### Post by Elfy on 2011-03-17
I'd first look at both your's and root's trash.

I'd also look in baobab to see if I could find where files are - or at least see if I could find where there's file use that I was not expecting.

[Some more info here.]("http://ubuntuforums.org/showpost.php?p=7053432&postcount=1")

Also - [http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by r-senior on 2011-03-17
Could you fire up a terminal and enter the following command, then post the results (or a screenshot)?

```
$ df -h
```

To copy from the terminal, select with the mouse and Shift-Control-C, or use the Edit->Copy menu.

---

### Post by Richiegs on 2011-03-17
> **r-senior said:**
> Could you fire up a terminal and enter the following command, then post the results (or a screenshot)?

```
$ df -h
```To copy from the terminal, select with the mouse and Shift-Control-C, or use the Edit->Copy menu.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              53G   50G  826M  99% /
none                  997M  272K  996M   1% /dev
none                 1002M  252K 1002M   1% /dev/shm
none                 1002M  100K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock

---

### Post by Richiegs on 2011-03-17
There is a folder called Log which has about 45 GB in it. I wonder what that is and can I delete it? Many thanks

---

### Post by r-senior on 2011-03-17
That's a lot of space used. This machine running Maverick only has 6.3G used.

Did you empty your trash?

Where is the log directory and what files does it have in it?

---

### Post by Elfy on 2011-03-18
I have vague memories of a bug causing that.

```
baobab /var/log
```

Which ones are enormous?

It might be good to read the large ones - see what's causing them to fill and deal with that if there's aproblem.

---

