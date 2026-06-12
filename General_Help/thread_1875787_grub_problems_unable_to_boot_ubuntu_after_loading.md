---
title: "grub problems unable to boot ubuntu after loading"
date: 2011-11-05
forum: General Help
---

### Post by vijayasimha13 on 2011-11-05
i had deleted my previous version of ubuntu as it was getting hung. now i have installed ubuntu 11.04 but it is not showing in boot menu , i tried repair grub from running live cd but i experiencing problem. i have done following actions on terminal and seem to have reached a dead end.
please help
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ apt get grub
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * openjdk-7-jdk (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-legacy-doc mdadm
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc grub2-common
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 865 kB of archives.
After this operation, 1,536 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main grub amd64 0.97-29ubuntu64 [865 kB]
Fetched 865 kB in 23s (36.6 kB/s)                                              
W: Duplicate sources.list entry cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/ oneiric/main i386 Packages (/var/lib/apt/lists/Ubuntu%2011.10%20%5fOneiric%20Ocelot%5f%20-%20Release%20amd64%20(20111012)_dists_oneiric_main_binary-i386_Packages)
Preconfiguring packages ...
(Reading database ... 130324 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Removing grub2-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Selecting previously deselected package grub.
(Reading database ... 130288 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu64_amd64.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu64) ...
W: Duplicate sources.list entry cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/ oneiric/main i386 Packages (/var/lib/apt/lists/Ubuntu%2011.10%20%5fOneiric%20Ocelot%5f%20-%20Release%20amd64%20(20111012)_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> sudo grub
sudo grub

Error 27: Unrecognized command
grub> find /boot/grub/stage 1
find /boot/grub/stage 1

Error 15: File not found
grub> find /boot/grub/stage
find /boot/grub/stage

Error 15: File not found

---

### Post by drs305 on 2011-11-05
vijayasimha13

Welcome to the Ubuntu Forums.  :-)

Error messages by number indicate Grub legacy is in use and not Grub 2. The best thing you can do to allow us to help you is to boot the LiveCD and then download and run the Boot Info Script from the following site. 

Post the contents of RESULTS.txt here and we can analyze your boot files and make informed recommendations.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by raja.genupula on 2011-11-05
one more thing is you have got dpkg-lock error and to solve use this 

```
sudo fuser -k -KILL /var/lib/dpkg/lock
```

---

