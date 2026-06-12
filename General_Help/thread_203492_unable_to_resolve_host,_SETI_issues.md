---
title: "unable to resolve host, SETI issues"
date: 2006-06-25
forum: General Help
---

### Post by Adragontattoo on 2006-06-25
had a power blink in the middle of installing packages and now anytime I try to do anything with Apt I have to wade through 20 attempts of this

adragontattoo@wrathstack:~$ sudo dpkg --configure -a
Password:
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--11:35:25--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
           => `/tmp/file1ILDXX'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--11:38:35--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 2) => `/tmp/file1ILDXX'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--11:41:46--  [ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar](ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar)
  (try: 3) => `/tmp/file1ILDXX'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... d   

Is there anyway to cancel this so that I can get back to reinstalling all the packages I lost when the original drive died?

---

### Post by tonyr on 2006-06-25
Did you try removing **setiathome** first?  

**sudo apt-get remove setiathome**

or

**sudo dpkg --remove --purge setiathome**


EDIT: fixed dpkg command

---

