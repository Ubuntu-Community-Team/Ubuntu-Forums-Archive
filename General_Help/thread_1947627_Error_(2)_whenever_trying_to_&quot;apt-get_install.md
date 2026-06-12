---
title: "Error (2) whenever trying to &quot;apt-get install&quot;"
date: 2012-03-27
forum: General Help
---

### Post by Romanian on 2012-03-27
Using 10.04 LTS.

This happens whenever I try to apt-get install anything. Example:

```
mihai@mihai-htpc:~$ sudo apt-get install jgraph
[sudo] password for mihai:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  samba
The following NEW packages will be installed:
  jgraph
0 upgraded, 1 newly installed, 1 to remove and 91 not upgraded.
3 not fully installed or removed.
Need to get 105kB of archives.
After this operation, 16.8MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe jgraph 83-22 [105kB]
Fetched 105kB in 1s (82.7kB/s)
/usr/bin/dpkg: 1: Syntax error: word unexpected (expecting ")")
E: Sub-process /usr/bin/dpkg returned an error code (2)

```


These two lines show up every time

```
/usr/bin/dpkg: 1: Syntax error: word unexpected (expecting ")")
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Romanian on 2012-03-27
Bump

---

### Post by Romanian on 2012-03-28
Bump

---

### Post by plucky on 2012-03-29
Try ```
sudo apt-get clean
sudo apt-get install -f
``` and post the output if any errors.

Good Luck

p.s. Just ran that command on my 10.04.4 and it installed correctly.You could try a different mirror if the above commands don't work.

---

