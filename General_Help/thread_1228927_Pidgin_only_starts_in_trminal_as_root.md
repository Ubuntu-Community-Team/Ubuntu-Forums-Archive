---
title: "Pidgin only starts in trminal as root"
date: 2009-08-01
forum: General Help
---

### Post by poliltimmy on 2009-08-01
Yesterday all was working fine. Today it tries to start then crashes. I did two things to it yesterday. Added the Notes plug in and blocked someone. That is the extent of changes. I removed and purged by way of apt. And reinstalled. Same problem. I purged and reinstalled, same problem. I can only start in the terminal as root now
timmy@timmy-pawpawsliltoy:~$ /usr/bin/pidgin
Segmentation fault
timmy@timmy-pawpawsliltoy:~$ pidgin
Segmentation fault
timmy@timmy-pawpawsliltoy:~$ sudo su
[sudo] password for timmy: 
root@timmy-pawpawsliltoy:/home/timmy# /usr/bin/pidgin
Using the start menu short cut produces the crash. Thanks in advance for any help you may have.  2.5.2 is the version. Straight from apt-get for 8.10.

Now command line does not work either. It shows up then disappears.

---

### Post by Brandon Williams on 2009-08-02
It sounds like you probably have some files that ended up with bad ownership somehow. Run 'find ~/.purple ! -user $USER' on the command line. Does it produce any output? If so, then run 'find ~/.purple ! -user $USER -exec chown $USER:$(id -gn) {} \;'. This should reset file and directory ownership.

---

### Post by poliltimmy on 2009-08-03
Yeah I probably did that upgrading to 9.04. A fresh install fixed that problem.

---

### Post by Liz on 2009-08-04
fresh install keeps bringing up dependencies problems. 

pidgin:
  Depends: pidgin-data (<1:2.5.2-z) but 1:2.5.8-1ubuntu2~pidgin1.8.04 is to be installed
 Depends: libpurple0 but it is not going to be installed

---

