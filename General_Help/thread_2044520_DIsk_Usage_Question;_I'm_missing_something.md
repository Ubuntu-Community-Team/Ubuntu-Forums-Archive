---
title: "DIsk Usage Question; I'm missing something"
date: 2012-08-19
forum: General Help
---

### Post by Husker Rat on 2012-08-19
This is probably something stupid that I am overlooking, but can't quite seem to find it and have not found an answer online. Possibly I just suck at searching. When testing a script to display my disk usage I found the numbers for /home don't add up. I seem to be missing 5GB somewhere:

root@localhost:~# du -sh /home/*
16K    /home/lost+found
9.3G    /home/user

Just over 9.3GB total for /home, however when I run df-h it shows 14G as being used. 

root@localhost:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
[irrelevant info deleted]
/dev/sda3       280G   14G  252G   6% /home

This is a fairly big discrepancy for such a small amount of data in the home directory. I am sure I am just overlooking something silly, but can't seem to figure out what it is. There is obviously plenty of free space so that is not an issue and won't be for some time, just trying to figure out what I am missing.  The file system is ext4.

Anyone have any ideas?

---

### Post by erind on 2012-08-19
> **Husker Rat said:**
> [...]
When testing a script to display my disk usage I found the numbers for /home don't add up. I seem to be missing 5GB somewhere:
[...]
This is a fairly big discrepancy for such a small amount of data in the home directory. I am sure I am just overlooking something silly, but can't seem to figure out what it is. There is obviously plenty of free space so that is not an issue and won't be for some time, just trying to figure out what I am missing.  The file system is ext4.

Anyone have any ideas?

Speaking in broad terms *df* and *du* rely on different information to determine a filesystem's disk usage, and probably there's not much to worry about regarding your situation.
I usually use *du* to measure disk usage, and *df *when I need a quick look at the free/used whole disk usage. Here it is a quote from an article (the link at the bottom):

> Summation: du is the better tool to use if you are interested in knowing how much space is actually being used on your filesystem "right now." df is great for "ballpark estimates" and is preferred if you need to know how big df thinks your filesystem is (so it will agree with other incorrect system statistics).Full article:

[http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html](http://linuxshellaccount.blogspot.com/2008/12/why-du-and-df-display-different-values.html)

---

### Post by dcstar on 2012-08-20
> **Husker Rat said:**
> 
.........
Anyone have any ideas?

There is a big difference between the size of a file and size it takes up on a partition if it is small.

---

