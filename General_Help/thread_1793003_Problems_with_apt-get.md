---
title: "Problems with apt-get"
date: 2011-06-28
forum: General Help
---

### Post by jenks517 on 2011-06-28
I actually think php5-cli is installed possibly... maybe wrong but ignore that tidbit. The problem is I can't install anything. I've tried autoclean, purge, remove. A few dpkg commands. I'm exhausted and just want to be able to install some packages and get back to developing. Here's what I'm encountering: 

> enksed: ~ --> sudo apt-get install php5-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-cli is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
13 not fully installed or removed.
Need to get 0B/125kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `python-cherrypy' missing, assuming package has no files currently installed.
(Reading database ... 297352 files and directories currently installed.)
Preparing to replace gnome-applets 2.30.0-0ubuntu2 (using .../gnome-applets_2.30.0-0ubuntu2_i386.deb) ...
Unpacking replacement gnome-applets ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
NameError: global name 'file' is not defined
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
NameError: global name 'file' is not defined
dpkg: error processing /var/cache/apt/archives/gnome-applets_2.30.0-0ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
NameError: global name 'file' is not defined
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-applets_2.30.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jenksed: ~ --> 


---

### Post by jenks517 on 2011-06-28
Forgot to add I'm running 10.04 LTS

---

### Post by noah++ on 2011-06-28
[This Google hit]("http://diveintopython3.org/case-study-porting-chardet-to-python-3.html") for *global name 'file' is not defined* makes me think maybe Python 3 is in use on your system where this program is expecting Python 2. In any case, it's almost definitely a Python-related problem.

---

### Post by jenks517 on 2011-06-29
Thank you sir. I had tried to force Ubuntu to use python3.0. I got my link back to where it should be and everything fell into place so far. Guess it's time to investigate managing multiple python versions. I'm guessing I can force apache to use 3 and keep 2.6.5 running.

---

