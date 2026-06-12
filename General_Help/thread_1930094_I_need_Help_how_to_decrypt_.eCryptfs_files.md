---
title: "I need Help how to decrypt *.eCryptfs files?"
date: 2012-02-23
forum: General Help
---

### Post by contime on 2012-02-23
Hi.

Accidentaly I removed my .Private directory and after long search I found that Photorec can restore my files.
Now I have a situation where I have a large amount Photorec restored directories and files.
Example:
ls -l /home/recup_dir.*
recup_dir.1/  recup_dir.16/ recup_dir.22/ recup_dir.29/ recup_dir.35/ recup_dir.41/ recup_dir.48/ recup_dir.54/ recup_dir.60/
recup_dir.10/ recup_dir.17/ recup_dir.23/ recup_dir.3/  recup_dir.36/ recup_dir.42/ recup_dir.49/ recup_dir.55/ recup_dir.61/
recup_dir.11/ recup_dir.18/ recup_dir.24/ recup_dir.30/ recup_dir.37/ recup_dir.43/ recup_dir.5/  recup_dir.56/ recup_dir.62/
recup_dir.12/ recup_dir.19/ recup_dir.25/ recup_dir.31/ recup_dir.38/ recup_dir.44/ recup_dir.50/ recup_dir.57/ recup_dir.7/
recup_dir.13/ recup_dir.2/  recup_dir.26/ recup_dir.32/ recup_dir.39/ recup_dir.45/ recup_dir.51/ recup_dir.58/ recup_dir.8/
recup_dir.14/ recup_dir.20/ recup_dir.27/ recup_dir.33/ recup_dir.4/  recup_dir.46/ recup_dir.52/ recup_dir.59/ recup_dir.9/
recup_dir.15/ recup_dir.21/ recup_dir.28/ recup_dir.34/ recup_dir.40/ recup_dir.47/ recup_dir.53/ recup_dir.6/

and under these directories there is a encrypted files.
ls -l /home/recup_dir.1/
total 1138584
-rw-r--r-- 1 root root   1443118 2012-02-20 15:50 f0661504.eCryptfs
-rw-r--r-- 1 root root   1488114 2012-02-20 15:50 f1634304.eCryptfs
-rw-r--r-- 1 root root   1703936 2012-02-20 15:50 f1874176.eCryptfs
-rw-r--r-- 1 root root   1048576 2012-02-20 15:50 f2162688.eCryptfs
-rw-r--r-- 1 root root   1196032 2012-02-20 15:50 f2164736.eCryptfs
-rw-r--r-- 1 root root    524288 2012-02-20 15:50 f2174976.eCryptfs
-rw-r--r-- 1 root root    131072 2012-02-20 15:50 f2176000.eCryptfs


Is there any way how to restore/decrypt these files? :(

---

### Post by HeroOfCanton on 2012-02-23
Not 100% if I understand your exact problem, but maybe this will help:

[http://manpages.ubuntu.com/manpages/natty/man1/ecryptfs-recover-private.1.html](http://manpages.ubuntu.com/manpages/natty/man1/ecryptfs-recover-private.1.html)

---

### Post by contime on 2012-02-23
Okey now I have a situation where after command "sudo ecryptfs-recover-private /home/recup_dir.2" I have 
"ls -l /tmp/ecryptfs.fmXWBQPw/ |wc -l"
501

How can I get normal filenames? at the moment I have many "f29827096.eCryptfs" files and if I look inside then these seems not encrypted anymore.

BR.

---

