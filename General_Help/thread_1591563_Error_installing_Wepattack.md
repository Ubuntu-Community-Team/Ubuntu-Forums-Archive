---
title: "Error installing Wepattack"
date: 2010-10-09
forum: General Help
---

### Post by pattelin on 2010-10-09
Hi,

I am trying to install the latest version of wepattack on Ubuntu 10.04 (64 bits) and I am getting the following error:

root@laptop2:/home/jay1/WepAttack-0.1.3/src# make
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepfilter.o wepfilter.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepfilter.c: In function ‘my_callback’:
wepfilter.c:131: error: assignment of read-only location ‘*pkthdr’
wepfilter.c:132: error: assignment of read-only location ‘*pkthdr’
make: *** [wepfilter.o] Error 1

Any ideas about why?

Thanx

---

### Post by jvhellraiser on 2010-10-10
Do not use wepattack install wifite here:

To install Wifite
copy:

Download the latest version:
1.wget -O wifite.py [http://wifite.googlecode.com/svn/trunk/wifite.py](http://wifite.googlecode.com/svn/trunk/wifite.py)

Change permissions to executable: 
2.chmod +x wifite.py

Execute:
3.python wifite.py

To see a list of commands with info: 
4../wifite.py -help

Tools to be install before using wifite:
1.apt-get install aircrack-ng
2.apt-get install python-tk
3.apt-get install macchanger

---

