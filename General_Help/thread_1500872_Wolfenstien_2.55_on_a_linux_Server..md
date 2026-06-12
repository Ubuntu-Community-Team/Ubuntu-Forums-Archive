---
title: "Wolfenstien 2.55 on a linux Server."
date: 2010-06-03
forum: General Help
---

### Post by Cputty on 2010-06-03
Well i was trying to install Wolfenstien 2.55 on a linux server which i own and is a proper one and not a local host and i get this error (i tried installing by using putty) 
The below code is from putty
_____________________________________________________


root@server [/home/etserver]# ./*.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup15651: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143: 15695 Aborted                 (core dumped) "$setup" "$@" 2>> $NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

_____________________________________________________________-

Now i have instaled this glibc by doing 

_________________________________________________________________


root@server [/home/etserver]# yum install glibc*
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * addons: centosz3-msync-dvd.centos.org
 * base: centosr4.centos.org
 * extras: centosn4-msync-dvd.centos.org
 * updates: centosr3.centos.org
addons                                                                                                |  951 B     00:00
base                                                                                                  | 1.1 kB     00:00
extras                                                                                                | 2.1 kB     00:00
updates                                                                                               | 1.9 kB     00:00
Excluding Packages in global exclude list
Finished
Setting up Install Process
Package glibc-devel-2.5-49.i386 already installed and latest version
Package glibc-2.5-49.i686 already installed and latest version
Package glibc-headers-2.5-49.i386 already installed and latest version
Package glibc-common-2.5-49.i386 already installed and latest version
Resolving Dependencies
--> Running transaction check
---> Package glibc-utils.i386 0:2.5-49 set to be updated
--> Finished Dependency Resolution

Dependencies Resolved

=============================================================================================================================
 Package                           Arch                       Version                       Repository                  Size
=============================================================================================================================
Installing:
 glibc-utils                       i386                       2.5-49                        base                       130 k

Transaction Summary
=============================================================================================================================
Install       1 Package(s)
Upgrade       0 Package(s)

Total download size: 130 k
Is this ok [y/N]: y
Downloading Packages:
glibc-utils-2.5-49.i386.rpm                                                                           | 130 kB     00:00
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing     : glibc-utils                                                                                           1/1

Installed:
  glibc-utils.i386 0:2.5-49
_________________________________________________________________

Now as i am a noob to this could we try to find a simple easy fix or please tell me if there is a way to get round it i have heard of one suggestion which will be getting 2.60 and downgrading but i do not know how to do this and this would be my final option 
Thankyou in Advance

---

