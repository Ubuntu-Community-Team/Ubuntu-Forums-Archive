---
title: "Error: No space left on device"
date: 2011-06-14
forum: General Help
---

### Post by shigihito on 2011-06-14
I've been getting popups regarding space issues for a while now. During a download, I got that error again. I don't know how this is possible because I know for a fact that I have almost 200gbs left. What do I do? Whenever I try to search it up on google, all the answers involve complicated things that I don't understand.

---

### Post by Primefalcon on 2011-06-14
Could be a file system error (don't quote me on this, but its worth a try right).

Try booting a live disk and start gparted, and then right click the particular partition and select check....

---

### Post by shigihito on 2011-06-14
What's gparted?

Isn't this a common problem? What do I do?

---

### Post by matt_symes on 2011-06-14
Hi

Open a terminal and type

```
df -h
```

Copy and paste the results from the terminal into your next post. This will tell us about your disc usage.

Kind regards

---

### Post by shigihito on 2011-06-14
Filesystem            Size  Used Avail Use% mount position
/dev/loop0             17G   15G  614M  97% /
none                  1.8G  696K  1.8G   1% /dev
none                  1.9G  1.8M  1.9G   1% /dev/shm
none                  1.9G  220K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda2             454G  268G  186G  59% /host
allen@ubuntu:~$

EDIT: I think I know the problem. When I installed Ubuntu from Windows via wubi, I chose 17g as a virtual disk size. anyway to change this?

---

### Post by matt_symes on 2011-06-14
Hi

For resizing a wubi partition have a look here (back it up first)

[http://ubuntuforums.org/showthread.php?t=1696765](http://ubuntuforums.org/showthread.php?t=1696765)

To see where the folders are that are using the most space run this in a terminal

```
du -h | sort -nr | head -n30
```

Post the results back here.

With that information we will be able to tell you what you can remove and what is taking up space.

Have you tried cleaning the apt caches etc

Kind regards

---

