---
title: "clamdscan can't open files"
date: 2010-09-24
forum: General Help
---

### Post by kanthoney on 2010-09-24
I've got a strange problem with clamdscan. I'm intending to use it alongside the Anomy sanitizer, so I've set up a directory /var/spool/sanitizer with owner clamav. Clamdscan refuses to scan anything in this directory, claiming it can't open any of the files despite it running as the owner of the files. It can scan some files in other directories, although there doesn't seem to be much pattern as to which files will scan.
 
This is a fresh install of Ubuntu server 10.04.1, using bog-standard packages.
 
```
 
$ clamdscan /var/spool/sanitizer/at2-order.pdf-4c9b713b.9X
/var/spool/sanitizer/at2-order.pdf-4c9b713b.9X: Can't open file or directory ERROR
----------- SCAN SUMMARY -----------
Infected files: 0
Total errors: 1
Time: 0.000 sec (0 m 0 s)
$ clamdscan /var/spool/sanitizer/
/var/spool/sanitizer: lstat() failed: Permission denied. ERROR
----------- SCAN SUMMARY -----------
Infected files: 0
Total errors: 1
Time: 0.000 sec (0 m 0 s)
$ ls -ld / /var /var/spool /var/spool/sanitizer /var/spool/sanitizer/*
drwxr-xr-x 22 root   root     4096 2010-09-22 12:46 /
drwxr-xr-x 16 root   root     4096 2010-09-22 11:55 /var
drwxr-xr-x  8 root   root     4096 2010-09-22 16:25 /var/spool
drwxr-xr-x  2 clamav clamav   4096 2010-09-23 16:28 /var/spool/sanitizer
-rw-r--r--  1 clamav clamav 118613 2010-09-23 16:24 /var/spool/sanitizer/at2-order.pdf-4c9b713b.9X
-rw-r--r--  1 clamav clamav 118613 2010-09-23 16:28 /var/spool/sanitizer/at2-order.pdf-4c9b721a.13
-rw-r--r--  1 clamav clamav   3171 2010-09-23 16:24 /var/spool/sanitizer/at2-order.xml-4c9b713c.DQ
-rw-r--r--  1 clamav clamav   3171 2010-09-23 16:28 /var/spool/sanitizer/at2-order.xml-4c9b721a.TL
-rw-r--r--  1 clamav clamav    473 2010-09-23 16:24 /var/spool/sanitizer/at2-unnamed.txt-4c9b713b.60
-rw-r--r--  1 clamav clamav    473 2010-09-23 16:28 /var/spool/sanitizer/at2-unnamed.txt-4c9b721a.KR
$ grep clamav /etc/passwd
clamav:x:112:122::/var/lib/clamav:/bin/false
$ ps lax | grep clamd
1   112 20558     1  20   0 175604 147384 poll_s Ssl ?          0:01 /usr/sbin/clamd

```

---

### Post by dcstar on 2010-09-25
> **kanthoney said:**
> I've got a strange problem with clamdscan. I'm intending to use it alongside the Anomy sanitizer, so I've set up a directory /var/spool/sanitizer with owner clamav. Clamdscan refuses to scan anything in this directory, claiming it can't open any of the files despite **it running as the owner of the files**. It can scan some files in other directories, although there doesn't seem to be much pattern as to which files will scan.
........

**You** are running it under **your** account privileges.

---

### Post by kanthoney on 2010-09-29
That doesn't matter - the files are world readable, and the same happens when I log in as root.
 
Anyway, I've worked round the problem by installing from source direct from ClamAV, which works fine.

---

### Post by GICodeWarrior on 2010-12-27
You need to change the apparmor profile to allow clamd to access that directory.
/etc/apparmor.d/local/usr.sbin.clamd

---

