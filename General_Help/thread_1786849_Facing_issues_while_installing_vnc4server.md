---
title: "Facing issues while installing vnc4server"
date: 2011-06-20
forum: General Help
---

### Post by sunandi on 2011-06-20
Hi Everyone,
I tried to install vnc4server on my new ubuntu 11.04 but its fauling and here is the error log

sunandi@sunandi-MM061:~/Downloads/linux-2.6.39.1$ sudo apt-get install vnc4server
[sudo] password for sunandi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vnc4server

Any pointers to fix this issue?

Help needed and will be sincerely appreciated

---

### Post by Toz on 2011-06-20
> $ apt-cache policy vnc4server
vnc4server:
  Installed: (none)
  Candidate: 4.1.1+xorg4.3.0-37ubuntu2
  Version table:
     4.1.1+xorg4.3.0-37ubuntu2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty/**universe** i386 Packages

vnc4server is in the universe repository. Make sure you have it enabled. See: [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by sunandi on 2011-06-20
Thanks a million, it worked for me
but when i execute this I am getting this error

sunandi@sunandi-MM061:~$ sudo vncpasswd ~/.vncpasswd
vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

any idea abt how to get away with this?

---

### Post by Toz on 2011-06-20
Hmm - works here. On my system, vncpasswd links to vnc4passwd. Try running vnc4passwd. Also, why are you running vncpasswd as root? Will you be connecting and logging in as root? (read: not really a good idea)

---

### Post by sunandi on 2011-06-20
Figured out a way to install the libraries:


1) Update sources.list: UbuntuGuide:How_to_add_extra_repositories  ([http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories))
or here for edgy ("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
2) sudo apt-get update

3) sudo apt-get install apt-file

4) sudo apt-file update

5) sudo apt-file search libstdc++-libc6.2-2.so.3

libstdc++2.10-dbg: usr/lib/debug/libstdc++-libc6.2-2.so.3
libstdc++2.10-glibc2.2: usr/lib/libstdc++-libc6.2-2.so.3

Hence

6) sudo apt-get install libstdc++2.10-glibc2.2

and then after vnc4server started working!!

Thanks a lot guys for helping me out
This forum is really useful

---

