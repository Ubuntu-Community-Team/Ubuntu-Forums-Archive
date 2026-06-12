---
title: "Errors were encountered while processing:  base-files"
date: 2010-01-20
forum: General Help
---

### Post by rakesh1908 on 2010-01-20
Hi there,

I'm unable to install any package on my Ubuntu, apt-get terminates with following error message.
I'm using Ubuntu Intrepid 8.10

```
baipaneni@Baipaneni:~$ sudo apt-get install python-tagpy
[sudo] password for baipaneni: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-python1.34.1
The following NEW packages will be installed:
  libboost-python1.34.1 python-tagpy
0 upgraded, 2 newly installed, 0 to remove and 342 not upgraded.
1 not fully installed or removed.
Need to get 880kB of archives.
After this operation, 3715kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://in.archive.ubuntu.com intrepid/main libboost-python1.34.1 1.34.1-11ubuntu1 [372kB]
Get:2 http://in.archive.ubuntu.com intrepid/universe python-tagpy 0.94.5-1 [508kB]
Fetched 880kB in 13s (63.1kB/s)                                                
Setting up base-files (4.0.4ubuntu2.2) ...
/var/lib/dpkg/info/base-files.postinst: 147: awk: Too many levels of symbolic links
/var/lib/dpkg/info/base-files.postinst: 147: awk: Too many levels of symbolic links
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

baipaneni@Baipaneni:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 342 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up base-files (4.0.4ubuntu2.2) ...
/var/lib/dpkg/info/base-files.postinst: 147: awk: Too many levels of symbolic links
/var/lib/dpkg/info/base-files.postinst: 147: awk: Too many levels of symbolic links
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help!

Thanks in advance.

---

### Post by n0dix on 2010-01-20
Try:
```
sudo dpkg --configure -a
```

See this thread too: [http://ubuntuforums.org/showthread.php?t=541998](http://ubuntuforums.org/showthread.php?t=541998)

---

### Post by rakesh1908 on 2010-01-20
> **n0dix said:**
> Try:
```
sudo dpkg --configure -a
```

See this thread too: [http://ubuntuforums.org/showthread.php?t=541998](http://ubuntuforums.org/showthread.php?t=541998)

I'm getting the same error :(

```
baipaneni@Baipaneni:~$ sudo dpkg --configure -a
Setting up base-files (4.0.4ubuntu2.2) ...
/var/lib/dpkg/info/base-files.postinst: 147: awk: Too many levels of symbolic links
/var/lib/dpkg/info/base-files.postinst: 147: awk: Too many levels of symbolic links
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 base-files


```

---

### Post by n0dix on 2010-01-20
- edit /var/lib/dpkg/info/base-files.postinst and add a "set -x" after the "set -e" at the top
- run "sudo dpkg-configure -a" in a terminal and copy the full output to the bug report

---

