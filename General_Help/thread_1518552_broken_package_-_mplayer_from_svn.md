---
title: "broken package - mplayer from svn"
date: 2010-06-26
forum: General Help
---

### Post by Honza007 on 2010-06-26
Hello,
I think I've installed mplayer from svn and now I'm getting that annoying "broken package" pop-up. Is any way how to make Ubuntu to ignore this package?
I've tried it to solve it by following:

```
user@mymachine:~$ **sudo apt-get install -f**
[sudo] password for jan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apport-hooks-medibuntu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libopencore-amrnb0 libopencore-amrwb0
The following NEW packages will be installed:
  libopencore-amrnb0 libopencore-amrwb0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/148kB of archives.
After this operation, 467kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160387 files and directories currently installed.)
Unpacking libopencore-amrnb0 (from .../libopencore-amrnb0_0.1.2-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencore-amrnb0_0.1.2-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencore-amrnb.so.0.0.2', which is also in package libopencore-amr 0:0.1.2-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libopencore-amrwb0 (from .../libopencore-amrwb0_0.1.2-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencore-amrwb0_0.1.2-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencore-amrwb.so.0.0.2', which is also in package libopencore-amr 0:0.1.2-1
Errors were encountered while processing:
 /var/cache/apt/archives/libopencore-amrnb0_0.1.2-1_amd64.deb
 /var/cache/apt/archives/libopencore-amrwb0_0.1.2-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@mymachine:~$ 
```

but without success.
Any idea?
Thank you.

---

### Post by gzarkadas on 2010-06-26
You will either have to remove the package `libopencore-amr' with which your try-to-install packages clash and then repeat the installation of libopencore-amrnb0 and libopencore-amrwb0 packages, or use ```
sudo apt-get purge libopencore-amrnb0 libopencore-amrwb0

``` to get rid off the svn packages.

---

### Post by Honza007 on 2010-06-27
Hello,
thank you for your reply. I've tried - but without success:
```
jan@machine:~$ **sudo apt-get purge libopencore-amrnb0 libopencore-amrwb0**
[sudo] password for jan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopencore-amrnb0 is not installed, so not removed
Package libopencore-amrwb0 is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mplayer: Depends: libopencore-amrnb0 but it is not going to be installed
           Depends: libopencore-amrwb0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jan@machine:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apport-hooks-medibuntu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libopencore-amrnb0 libopencore-amrwb0
The following NEW packages will be installed:
  libopencore-amrnb0 libopencore-amrwb0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/148kB of archives.
After this operation, 467kB of additional disk space will be used.
**Do you want to continue [Y/n]? y**
(Reading database ... 160387 files and directories currently installed.)
Unpacking libopencore-amrnb0 (from .../libopencore-amrnb0_0.1.2-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencore-amrnb0_0.1.2-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencore-amrnb.so.0.0.2', which is also in package libopencore-amr 0:0.1.2-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libopencore-amrwb0 (from .../libopencore-amrwb0_0.1.2-1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libopencore-amrwb0_0.1.2-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libopencore-amrwb.so.0.0.2', which is also in package libopencore-amr 0:0.1.2-1
[B]Errors were encountered while processing:
 /var/cache/apt/archives/libopencore-amrnb0_0.1.2-1_amd64.deb
 /var/cache/apt/archives/libopencore-amrwb0_0.1.2-1_amd64.deb[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
jan@machine:~$ 
```

Any more ideas?
(I'm in kind of what was first problem chicken or egg? :-) )
Thank you.

---

### Post by hansdown on 2010-06-27
Hi Honza007.

Try 

```
sudo apt-get autoremove

```

---

