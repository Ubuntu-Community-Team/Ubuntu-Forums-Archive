---
title: "splashy killed kpackagekit...bootsplash screen"
date: 2010-07-17
forum: General Help
---

### Post by betlog on 2010-07-17
10.04 - Installing splashy fails and consequently makes kpackagekit completely unuseable.
Attempting to fix this with aptitude or 'sudo dpkg --force-overwrite --install' or 'sudo apt-get -f install' (as suggested elsewhere) brings me no joy either.
Is there a fix so I can remove splashy and repair kpackagekit?
People seem to be pointing to this thread, but nothing I can see in it actually solves the problem.
https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/328089

How do I kill splashy so i can repair kpackagekit?

---

### Post by cariboo on 2010-07-17
Xsplash no longer works in Lucid, it has been replaced with Plymouth. I would suggest install Synaptic Package Manager if you are having problems kpackagekit.

---

### Post by betlog on 2010-07-17
:|
 yeah thats what i am trying to do, however splashy seems to have impaired my ability to install/remove anyhting. 

sudo apt-get install synaptic
[sudo] password for betlog: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  splashy-themes: Depends: splashy (>= 0.3.12-1) but it is not going to be installed
  synaptic: Depends: libvte9 (>= 1:0.22.0) but it is not going to be installed
            Recommends: software-properties-gtk but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

..sigh...

betlog@betlogbox:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-ugly libfile-homedir-perl libswfdec-0.8-0 libfile-which-perl libvisual-0.4-0
  libfile-desktopentry-perl libproc-simple-perl gstreamer0.10-ffmpeg libfile-basedir-perl
  libvisual-0.4-plugins libsidplay1 libfile-mimeinfo-perl libopencore-amrnb0 libopencore-amrwb0
  gstreamer0.10-plugins-base libsort-naturally-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  splashy
Suggested packages:
  console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
8 not fully installed or removed.
Need to get 0B/1,182kB of archives.
After this operation, 1,843kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 152139 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-5ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0:4.0-0ubuntu8
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

see, what I am saying is i have already tried every solution offered, with no success.

I am a bit of a noob though, so it's possible i just dont understand some 'really obvious'  linuxy thing to do.

---

### Post by betlog on 2010-07-17
bump

betlog@betlogbox:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
  splashy-themes: Depends: splashy (>= 0.3.12-1) but it is not installed
E: Unmet dependencies. Try using -f.

betlog@betlogbox:~$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  splashy
Suggested packages:
  console-common
The following packages will be REMOVED:
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-ugly libfile-basedir-perl
  libfile-desktopentry-perl libfile-homedir-perl libfile-mimeinfo-perl libfile-which-perl
  libopencore-amrnb0 libopencore-amrwb0 libproc-simple-perl libsidplay1 libsort-naturally-perl
  libswfdec-0.8-0 libvisual-0.4-0 libvisual-0.4-plugins
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 16 to remove and 1 not upgraded.
8 not fully installed or removed.
Need to get 0B/1,182kB of archives.
After this operation, 5,595kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152139 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-5ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0:4.0-0ubuntu8
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


:{

---

### Post by betlog on 2010-07-17
http://ubuntuforums.org/showthread.php?t=1294858
.. problem is that despite everyone pointing  at the bug thread it doesn't actually solve my issue. 
 I am in a loop of cant do anyhting because splashy has munched my  ability to install/remove.

There is probably a simple solution... but what is that exactly?

Yes I know 10.04 and splashy are completely incompatible.. and that the silent introduction of plymouth is basically responsible..i know that  now.
.. so how do i remove splashy's mess so i can repair whatever is  broken with apt/aptitude/kpackagekit?

this 'splashy broke apt' concept seems to have come up a few times, I am guessing many users just fix it by reinstalling.
http://ubuntuforums.org/showthread.php?t=1359577&highlight=splashy
http://ubuntuforums.org/showthread.php?t=1439170&highlight=splashy
http://ubuntuforums.org/showthread.php?t=1467819&highlight=splashy
http://ubuntuforums.org/showthread.php?t=1243140&highlight=splashy <- they are not on 10.04

The thing that really confuses me is; why is splashy listed in  kpackagekit *at all* if it is inherently damaging to plymouth in 10.04? No  really.. why?

---

### Post by betlog on 2010-07-17
It seems that 
$ aptitude -f
and some random stabbing at 'u' and 'g' might have untangled things for me a bit.
/me crosses fingers

---

