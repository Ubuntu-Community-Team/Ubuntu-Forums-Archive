---
title: "Wine post-insall script returned 255"
date: 2010-04-10
forum: General Help
---

### Post by ivanatora on 2010-04-10
Hello,
I've installed wine on my laptop and it runs fine. Although it seems something happened while installing it (via apt-get install), because everytime I use apt-get untill then I get the following in my terminal:
```

$ sudo apt-get install vorbis-tools
[sudo] password for ivanatora: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  vorbis-tools
0 upgraded, 1 newly installed, 0 to remove and 228 not upgraded.
1 not fully installed or removed.
Need to get 118kB of archives.
After this operation, 795kB of additional disk space will be used.
Get:1 http://bg.archive.ubuntu.com karmic/main vorbis-tools 1.2.0-6 [118kB]
Fetched 118kB in 1s (68.0kB/s)          
Selecting previously deselected package vorbis-tools.
(Reading database ... 182482 files and directories currently installed.)
Unpacking vorbis-tools (from .../vorbis-tools_1.2.0-6_i386.deb) ...
Processing triggers for man-db ... **(end of normal output, these things below I get everytime I use apt-get install)**
Setting up wine (1.0.1-0ubuntu8) ...
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
vm.mmap_min_addr = 0
error: "Invalid argument" setting key "vm.laptop_mode"
vm.dirty_writeback_centisecs = 2000
kernel.nmi_watchdog = 0
vm.swappiness = 5
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up vorbis-tools (1.2.0-6) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Everything is working, but seeing these messages is a little annoying. Do you have any ideas why does dpkg do that?

---

### Post by ubunterooster on 2010-04-10
the "invalid argument" of "vm.latop-mode" precedes the wine error, hmm.

Are you using wine stable? or did you add sources for the beta version of wine?

Either way it seems best to uninstall wine, reboot, and install it again.

---

### Post by ivanatora on 2010-04-11
I got the same error about setting vm.laptop_mode, It seems I'm not the only one with that problem: [http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg149300.html](http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg149300.html)

---

