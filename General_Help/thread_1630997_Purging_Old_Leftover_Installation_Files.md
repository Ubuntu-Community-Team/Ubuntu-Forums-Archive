---
title: "Purging Old Leftover Installation Files"
date: 2010-11-26
forum: General Help
---

### Post by jim_deadlock on 2010-11-26
Every time I install a new package via the software centre it installs fine but at the end I get a package failure dialog popping up every time. It seems to be an issue with the leftover remnants of firmware-b43-installer. How do I clean up redundant files like this?

[IMG]http://img16.imageshack.us/img16/146/screenshotynl.png[/IMG]

The details are:

```
installArchives() failed: Selecting previously deselected package pidgin-data. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 146536 files and directories currently installed.) 
Unpacking pidgin-data (from .../pidgin-data_1%3a2.7.3-1ubuntu3.2_all.deb) ... 
Selecting previously deselected package pidgin. 
Unpacking pidgin (from .../pidgin_1%3a2.7.3-1ubuntu3.2_amd64.deb) ... 
Selecting previously deselected package pidgin-libnotify. 
Unpacking pidgin-libnotify (from .../pidgin-libnotify_0.14-4ubuntu1_amd64.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for gconf2 ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for python-support ... 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up pidgin-data (1:2.7.3-1ubuntu3.2) ... 
Setting up pidgin (1:2.7.3-1ubuntu3.2) ... 
Setting up pidgin-libnotify (0.14-4ubuntu1) ... 
Errors were encountered while processing: 
 firmware-b43-installer 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 

```

---

### Post by Rubi1200 on 2010-11-26
Hi,
try running the following commands (separately) and see if it clears up the problem:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Report back if there are errors.

Thanks.

---

### Post by jim_deadlock on 2010-11-26
That didn't seem to have any effect, still getting the same error when installing a new package.

```
jim@ubuntu:~$ sudo apt-get install -f
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@ubuntu:~$ sudo dpkg --configure -a
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
```

---

### Post by wet-willy on 2010-11-26
I think the previous advisor meant: **sudo apt-get install -f packagename**
None the less, there is a broken package. According to the title of this thread, one would get the impression this "firmware-b43-installer" is "Old Leftover Installation Files". So why not open up Synaptic and hit the Custom Filters/Broken link on the left side, right click on firmware-b43-installer and b43-fwcutter (if present as it is a dependency type package), and select, "mark for complete removal" or similar, hit apply, and then when Synaptic is back for abuse, hit the Status link on the left to see if they are still lingering in "residual config" section, if so, right click and select "mark for complete removal", hit apply.
Then maybe run the **dpkg --configure -a** command again to see if it's happy.

> Not supported low-power chip with PCI id 14e4:4315!
Aborting.
BTW: **sudo apt-get purge firmware-b43-installer**

---

### Post by jim_deadlock on 2010-11-26
> **wet-willy said:**
> BTW: **sudo apt-get purge firmware-b43-installer**

... did the trick, thanks!

---

### Post by frankduffey on 2011-04-02
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.

---

### Post by frankduffey on 2011-04-02
I just ran command [B]sudo apt-get purge firmware-b43-installer I hope that gets rid of the error I was also receiving and why when running any install was I receiving this error?
[/B]

---

### Post by wet-willy on 2011-04-08
> **frankduffey said:**
> Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id [COLOR="Red"]14e4:4315[/COLOR]!
Aborting.
Based on that id, you need to set up the broadcom-sta which will produce a wl driver. I migrated to Debian live, I install module-assistant, build-essential, broadcom-sta-source, wireless-tools, headers, then run command:

m-a a-i broadcom-sta

[Here is the Debian link]("http://wiki.debian.org/wl"), I'm sure it's the same for Ubuntu.

---

