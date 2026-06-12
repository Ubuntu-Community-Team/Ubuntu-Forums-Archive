---
title: "acpi-support"
date: 2010-06-29
forum: General Help
---

### Post by =ChAoS= on 2010-06-29
Hi guys, I am renting a dedicated server and i'm following a tutorial to install rutorrent. I'm asked to ...
 
> sudo apt-get install -y build-essential pkg-config libcurl4-openssl-dev libsigc++-2.0-dev libncurses5-dev lighttpd nano screen subversion libterm-readline-gnu-perl php5-cgi apache2-utils
 
But continually get this error ...
 
>  
sudo apt-get install -y build-essential pkg-config libcurl4-openssl-dev libsigc++-2.0-dev libncurses5-dev lighttpd nano screen subversion libterm-readline-gnu-perl php5-cgi apache2-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
pkg-config is already the newest version.
libcurl4-openssl-dev is already the newest version.
libsigc++-2.0-dev is already the newest version.
libncurses5-dev is already the newest version.
lighttpd is already the newest version.
nano is already the newest version.
screen is already the newest version.
subversion is already the newest version.
libterm-readline-gnu-perl is already the newest version.
php5-cgi is already the newest version.
apache2-utils is already the newest version.
The following packages were automatically installed and are no longer required:
xserver-xorg-video-amd linux-headers-2.6.24-16-generic
linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
* Starting ACPI services... 
acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
acpid
acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

 
I have followed ideas posted in different threads for this problem but none have worked. I'm new to linux so here comes the dumb questions ... 
 
What is acpid and what problems will it cause if ignored?
 
Thanks =ChAoS=

---

### Post by GreenN00b on 2010-06-29
Try running apt-get without -y switch, it will probably ask you some questions about acpi ...

---

### Post by =ChAoS= on 2010-06-29
Thanks i tried but same result?

---

### Post by GreenN00b on 2010-06-29
See this [thread]("http://ubuntuforums.org/showthread.php?t=584578"), seems to be a similar issue and a solution:

```
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
sudo dpkg --configure -a
```

---

### Post by =ChAoS= on 2010-06-29
Thanks again for the quick reply. That was a thread i followed when i originally googled the problem. This is what i get when i try the second command ... 
 
>  
sudo dpkg --configure acpid
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                   
acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid


 
As i still don't fully know what it does and i dunno how important it is i'll keep looking.

---

### Post by dino99 on 2010-06-29
you seem to run an oldish distro, have you a serious reason for it ?

---

### Post by =ChAoS= on 2010-06-29
Its the distro that was pre installed on my dedicated server. I was asked what i wanted and chose ubuntu desktop because i'm a linux noob and thought it would be the best bet. I know theres s newer version but this is what they installed. There was no option for choosing what version was installed.
 
Should i enquire about the latest version?

---

### Post by dino99 on 2010-06-29
this kind of software is no more updated or maintained, sorry

---

