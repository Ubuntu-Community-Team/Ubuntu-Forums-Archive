---
title: "package managers crashing"
date: 2011-11-18
forum: General Help
---

### Post by Randymanme on 2011-11-18
I've been having some problems with Oneiric: Synaptic Package Manager keeps crashing.  I've been to both ://ubuntuforums.org/showthread.php?t=1854470 and [http://ubuntuforums.org/showthread.php?t=1864259&highlight=synaptic+crashes](http://ubuntuforums.org/showthread.php?t=1864259&highlight=synaptic+crashes). Nothing that worked for others has worked for me.

randall@randall-Dimension-8300:~$ gksudo synaptic 
  what():  vector::_M_range_check 
 instance of 'std::out_of_range' 
randall@randall-Dimension-8300:~$ sudo apt-get remove --purge synaptic 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  galculator giblib1 scrot 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  gnome* gnome-core* synaptic* 
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded. 
After this operation, 7,250 kB disk space will be freed. 
Do you want to continue [Y/n]? y 
Abort. 
randall@randall-Dimension-8300:~$

From what I gather, the bug at work here is already documented.

I seemed to me that this was a good time to try out Muon Package Manager.  Well, guess what?  It crashes also.

randall@randall-Dimension-8300:~$ sudo muon 
[sudo] password for randall: 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
randall@randall-Dimension-8300:~$ Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
kdeinit4: Shutting down running client. 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString) 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
kbuildsycoca4 running... 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Failed to read classid file: Object not found 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
KCrash: Application 'muon' crashing... 
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit 
sock_file=/home/randall/.kde/socket-randall-Dimension-8300/kdeinit4__0 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
kbuildsycoca4 running... 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Cannot access memory at arandall@randall-Dimension-8300:~$ sudo muon 
[sudo] password for randall: 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
randall@randall-Dimension-8300:~$ Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
kdeinit4: Shutting down running client. 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString) 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
kbuildsycoca4 running... 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Failed to read classid file: Object not found 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
KCrash: Application 'muon' crashing... 
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit 
sock_file=/home/randall/.kde/socket-randall-Dimension-8300/kdeinit4__0 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Error: "/tmp/kde-randall" is owned by uid 1000 instead of uid 0. 
kbuildsycoca4 running... 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
Cannot access memory at address 0xb6135430 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
[6134:6134:3193188431:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
[6175:6175:3267902771:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root. 
[6206:6206:3275427207:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root. 
ddress 0xb6135430 
Error: "/var/tmp/kdecache-randall" is owned by uid 1000 instead of uid 0. 
[6134:6134:3193188431:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root. 
Error: "/tmp/ksocket-randall" is owned by uid 1000 instead of uid 0. 
[6175:6175:3267902771:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root. 
[6206:6206:3275427207:ERROR:browser_main_gtk.cc(125)] Startup refusing to run as root. 

I tried following the prompts with the KDE Crash Handler's Crash Reporting Assistant, but when I tried to send it, it said that need to register and get an account first. So when I click on the highlighted “here,” (I think it was),  I'm informed that Chrome will not open for root (???).  Maybe that's part of the bug, too.  I coped and pasted the backtrack to Libre Office and I'll try to attach it to this posting as an attachment.

As always, any and all help will be much appreciated.  Thank you.

---

### Post by Randymanme on 2011-11-23
I found the solution: [https://bugs.launchpad.net/ubuntu/+s...19/comments/16]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16")

---

