---
title: "broken dependecies"
date: 2010-04-21
forum: General Help
---

### Post by teacosy on 2010-04-21
hi... 

i really need help with this one as I can't find an answers anywhere.

im having a problem after trying to add the **RareWares Debian GNU / Linux Repository** to my **apt source list**... 

i get this error when using **kpackagekit**... 

```

There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation.

```seems to be a problem with **libanyevent-perl**...

**sudo apt-get install -f **returns:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ogmtools anyevent-perl libasound2-plugins binfmt-support
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libanyevent-perl
The following NEW packages will be installed:
  libanyevent-perl
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
2 not fully installed or removed.
Need to get 0B/210kB of archives.
After this operation, 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 190559 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_4.410-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_4.410-1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 0:1.02-0.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_4.410-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```someone mentioned to use the **dpkg-divert** command im not too familiar with the dpkg-divert command... 
i read the dpkg-divert man page and thought i needed to add a diversion for the **/var/cache/apt/archives/libanyevent-perl_4.410-1_all.deb** file... 

i did that and tried install -f again but same result...

im sure im missing something... 

i made a reply to this post [http://ubuntuforums.org/showthread.php?t=1424319](http://ubuntuforums.org/showthread.php?t=1424319) but not sure if it is still active and didnt resolve the issue there...

can anybody help me out on this? as it is i cant upgrade, update install or remove anything...

thanks

t

---

### Post by teacosy on 2010-04-21
ha... i thought so...

as soon as i made a new thread i would find a solution...

found something of interest here: 

[http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian](http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian) 

i used dkpg to force the overwrite of the package:
cd /var/cache/apt/archives/
dpkg -i --force-overwrite libanyevent-perl_4.410-1_all.deb

now it seems my dependencies have been resolved...

thanks

---

