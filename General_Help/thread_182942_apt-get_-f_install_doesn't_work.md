---
title: "apt-get -f install doesn't work"
date: 2006-05-27
forum: General Help
---

### Post by baosheng on 2006-05-27
I wanna install multimedia codecs via the command

[FONT="Century Gothic"]sudo apt-get install beep-media-player totem-xine w32codecs gstreamer0.8-plugins[/FONT]

But I encountered the problem that some dependencies unmetted.
Then I tried to run apt-get -f install and got the following response:

[SIZE="1"][FONT="Century Gothic"]root@silver:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gstreamer0.8-visuals
The following NEW packages will be installed:
  gstreamer0.8-visuals
0 upgraded, 1 newly installed, 0 to remove and 178 not upgraded.
40 not fully installed or removed.
Need to get 0B/63.0kB of archives.
After unpacking 176kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gstreamer0.8-visuals
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 58667 files and directories currently installed.)
Unpacking gstreamer0.8-visuals (from .../gstreamer0.8-visuals_0.8.11-0unofficialubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gstreamer0.8-visuals_0.8.11-0unofficialubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/gstreamer-0.8/libgstgoom.so', which is also in package gstreamer0.8-misc
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.8-visuals_0.8.11-0unofficialubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT][/SIZE]

Now I can't use apt-get to do any thing. What shall I do now? How can I fix the problem?

thanks

---

### Post by sYs^ on 2006-05-27
apt-get remove gstreamer0.8-visuals then try apt-get upgrade 
Hope it'll help :p

---

### Post by az on 2006-05-27
Are you mixing repositories?  Try to remove all non-ubuntu repos.  Remove all package from non-ubuntu sources that are causing problems like this.

---

