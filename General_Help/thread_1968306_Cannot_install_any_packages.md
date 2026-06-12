---
title: "Cannot install any packages"
date: 2012-04-28
forum: General Help
---

### Post by aemerick on 2012-04-28
Hello. I have been having problems recently installing any pacakge, regardless of what it is. The problem is associated with flashplayer it seems, as whenever I attempt to "sudo apt-get install" a package, it fails with an error along the lines of the following:

=====
$ sudo apt-get install gedit-latex-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit-latex-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ...
Downloading...
--2012-04-28 22:05:34--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz)
Resolving archive.canonical.com... 91.189.92.150, 91.189.92.191
Connecting to archive.canonical.com|91.189.92.150|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-04-28 22:05:34 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-downloader:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
======

Again, this is happening (or some variation of the above) regardless of what I am installing. I was able to install packages just fine a few days ago. I do not really know what may have changed in the past few days that could cause the above. 

Thanks for any help.

---

### Post by oboedad55 on 2012-04-28
> **aemerick said:**
> Hello. I have been having problems recently installing any pacakge, regardless of what it is. The problem is associated with flashplayer it seems, as whenever I attempt to "sudo apt-get install" a package, it fails with an error along the lines of the following:

=====
$ sudo apt-get install gedit-latex-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit-latex-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ...
Downloading...
--2012-04-28 22:05:34--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz)
Resolving archive.canonical.com... 91.189.92.150, 91.189.92.191
Connecting to archive.canonical.com|91.189.92.150|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-04-28 22:05:34 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-downloader:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
======

Again, this is happening (or some variation of the above) regardless of what I am installing. I was able to install packages just fine a few days ago. I do not really know what may have changed in the past few days that could cause the above. 

Thanks for any help.

Have a look here: [http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)

---

### Post by aemerick on 2012-04-28
> **oboedad55 said:**
> Have a look here: [http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)

Perfect fix. Thank you.

---

### Post by oboedad55 on 2012-04-29
> **aemerick said:**
> Perfect fix. Thank you.

No problem. I just googled the error. I couldn't remember the commands to fix dpkg. When I was running Ubuntu all the time I kept a text file with commands in it to remind me of stuff like that.

---

