---
title: "where is /proc mounted by default"
date: 2010-08-19
forum: General Help
---

### Post by anirudhtomer on 2010-08-19
I typed the following thing

[anirudh@localhost ~]$ df /proc
Filesystem           1K-blocks      Used Available Use% Mounted on
proc                         0         0         0   -  /proc

& then I check this for all folders like /opt, /home , /mnt

[anirudh@localhost ~]$ df /home
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             14877028   3560816  10548312  26% /
[anirudh@localhost ~]$ df /opt
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             14877028   3560816  10548312  26% /
[anirudh@localhost ~]$ df /mnt
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             14877028   3560816  10548312  26% /

during installation I had given the mount point as "/" & installed ubuntu.
I want to know why only /proc is mounted on /proc & not others....

---

### Post by anirudhtomer on 2010-08-19
Isn't there anyone who can help me out on this simple issue.

---

