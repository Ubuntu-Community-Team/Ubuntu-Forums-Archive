---
title: "apt-get wedged  [newbie]"
date: 2011-02-21
forum: General Help
---

### Post by kurtguenther on 2011-02-21
I tried installing eclipse which is apparently a known problem.  However, know my packet manager seems  broken. 


> 
root@ubuntu-spike:~# apt-get remove eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package eclipse is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 eclipse-pde : Depends: eclipse-jdt (= 3.5.2-6ubuntu1.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
But, when I try  "apt-get -f install", I also get errors: 

> 
root@ubuntu-spike:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  eclipse-jdt
Suggested packages:
  eclipse
The following NEW packages will be installed:
  eclipse-jdt
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/39.9MB of archives.
After this operation, 43.6MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 160151 files and directories currently installed.)
Unpacking eclipse-jdt (from .../eclipse-jdt_3.5.2-6ubuntu1.1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/eclipse-jdt_3.5.2-6ubuntu1.1_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/eclipse-jdt_3.5.2-6ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
So, how do I get apt-get to give up on eclipse?  :confused:    I've tried "apt-get remove", but I get similar errors. 

--Kurt

---

### Post by thefasterblueone on 2011-02-21
Try running:

```
sudo apt-get remove --purge eclipse-jdt
```

---

### Post by kurtguenther on 2011-02-21
Thanks.   I'm running again.

---

