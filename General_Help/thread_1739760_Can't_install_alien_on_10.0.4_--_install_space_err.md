---
title: "Can't install alien on 10.0.4 -- install space error?"
date: 2011-04-26
forum: General Help
---

### Post by curmudge1 on 2011-04-26
I'm trying to install alien on an Ubuntu 10.0.4 server, which happens to be a virtual host on an ESX 4  Vmware server, in case that matters.

Can someone make sense of this & provide feedback?  I have a lot of experience with various Unixes over the years, especially Solaris, but we're just getting going with Linux servers here.  TIA.

dstrom@webserver:~$ sudo apt-get install alien
[sudo] password for dstrom:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  alien: Depends: debhelper (>= 3) but it is not going to be installed
         Depends: rpm (>= 2.4.4-2) but it is not going to be installed
         Depends: dpkg-dev but it is not going to be installed
         Depends: rpm2cpio but it is not going to be installed
  linux-headers-server: Depends: linux-headers-2.6.32-31-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dstrom@webserver:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libjna-java junit4 libsamplerate0 javahelp2 linux-headers-2.6.32-28-server
  libnb-platform11-java linux-headers-2.6.32-28 linux-headers-2.6.32-29
  libswing-layout-java linux-headers-2.6.32-29-server visualvm
  libhamcrest-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.32-31 linux-headers-2.6.32-31-server
The following NEW packages will be installed:
  linux-headers-2.6.32-31 linux-headers-2.6.32-31-server
0 upgraded, 2 newly installed, 0 to remove and 45 not upgraded.
4 not fully installed or removed.
Need to get 0B/10.7MB of archives.
After this operation, 85.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 92919 files and directories currently installed.)
Unpacking linux-headers-2.6.32-31 (from .../linux-headers-2.6.32-31_2.6.32-31.61_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-31_2.6.32-31.61_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.32-31/arch/h8300/platform/h8s/edosk2674/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-31/arch/h8300/platform/h8s/edosk2674/Makefile'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking linux-headers-2.6.32-31-server (from .../linux-headers-2.6.32-31-server_2.6.32-31.61_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-31-server_2.6.32-31.61_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.32-31-server/include/config/cifs/experimental.h.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-31-server/include/config/cifs/experimental.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.32-31_2.6.32-31.61_all.deb
 /var/cache/apt/archives/linux-headers-2.6.32-31-server_2.6.32-31.61_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dstrom@webserver:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/webserver-root
                       19G  8.1G  9.6G  46% /
none                  3.8G  196K  3.8G   1% /dev
none                  3.8G     0  3.8G   0% /dev/shm
none                  3.8G   92K  3.8G   1% /var/run
none                  3.8G     0  3.8G   0% /var/lock
none                  3.8G     0  3.8G   0% /lib/init/rw
none                   19G  8.1G  9.6G  46% /var/lib/ureadahead/debugfs
/dev/sda5             228M   99M  117M  46% /boot
/dev/sdc1             246G   40G  193G  18% /cacheFS
/dev/sdb1             222G   25G  196G  12% /repo
sunserver0.ciesin.columbia.edu:/ufs/local1/svsu/home/irt.ops
                      135G  127G  7.0G  95% /nfs/home/irt.ops
dstrom@webserver:~$ cd /usr/src
dstrom@webserver:/usr/src$ df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/webserver-root
                       19G  8.1G  9.6G  46% /

---

### Post by 3Miro on 2011-04-26
Most likely corrupt repository databse. Try installing "aptitude", it is more sophisticated than apt-get.

```
sudo aptitude install alien
```

If you don't already have aptitude, you will need to install it:
```
sudo apt-get install aptitude
```

Why do you need alien anyway, this is supposed to be a last resort in all cases.

---

### Post by curmudge1 on 2011-04-26
We need alien to convert the EMC (formerly Legato) Networker rpm, so we can back this system up.

--
Dave

---

### Post by curmudge1 on 2011-04-26
aptitude works!   

Thanks.

--
Dave

---

