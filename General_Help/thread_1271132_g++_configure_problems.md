---
title: "g++ configure problems"
date: 2009-09-20
forum: General Help
---

### Post by frt975 on 2009-09-20
I think that freeze during updates caused this:
```
flaviu@upstairs-laptop:~$ sudo aptitude install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following partially installed packages will be configured:
  g++ 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up g++ (4:4.3.3-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing g++ (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


```

---

### Post by Bachstelze on 2009-09-20
That's... weird. Try

```
sudo apt-get install build-essential
```

---

### Post by frt975 on 2009-09-20
```
flaviu@upstairs-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev
Suggested packages:
  debian-keyring
The following NEW packages will be installed:
  build-essential dpkg-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/650kB of archives.
After this operation, 2040kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  dpkg-dev build-essential
Authentication warning overridden.
Selecting previously deselected package dpkg-dev.
(Reading database ... 152314 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.14.24ubuntu1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Processing triggers for man-db ...
Setting up g++ (4:4.3.3-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing g++ (--configure):
 subprocess post-installation script returned error exit status 2
Setting up dpkg-dev (1.14.24ubuntu1) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.3.1); however:
  Package g++ is not configured yet.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 g++
 build-essential
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Still doesn't work:(

---

### Post by frt975 on 2009-09-20
Who knew! [afbase]("http://ubuntuforums.org/showthread.php?t=1270358") had the same problem but different goals.

---

