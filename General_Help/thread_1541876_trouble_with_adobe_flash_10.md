---
title: "trouble with adobe flash 10"
date: 2010-07-29
forum: General Help
---

### Post by entropy7 on 2010-07-29
Hi,
I updated 8.04 a few days ago and adobe flash 10 has stopped working on youtube. I get a message saying, "you need to install adobe flash 10 plug-in". I installed the Adobe Flash 10 plug-in, it seemed to install OK. But I still get the same message. I rebooted, restarted, re-installed, etc etc. but I still get the same message. Up until now, I have had no trouble using Adobe Flash to view youtube on Ubuntu.   thanks.

---

### Post by hhh on 2010-07-29
You said you reinstalled, see if uninstalling/reinstalling will work, I've seen that posted as a solution before...

```
sudo apt-get purge flashplugin-nonfree
```
```
sudo apt-get install flashplugin-nonfree
```

-edit- found a bug report, it suggests purging flashplugin-installer as well...
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/529153](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/529153)

---

### Post by entropy7 on 2010-07-30
OK, when I do the second command I get:

>sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-27-generic firefox-3.0-gnome-support
  xulrunner-1.9-gnome-support linux-headers-2.6.24-27
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9kB of archives.
After this operation, 164kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse flashplugin-nonfree 9.0.48.0.0ubuntu11~dapper3 [17.9kB]
Fetched 17.9kB in 0s (23.5kB/s)       
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 149919 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.0ubuntu11~dapper3_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu11~dapper3) ...
Downloading...
--10:31:43--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.17.114.70
Connecting to fpdownload.macromedia.com|96.17.114.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:31:43 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

---

### Post by Raymond2201 on 2010-07-30
> **entropy7 said:**
> 
10:31:43 ERROR 404: Not Found.


Indeed the URL apt is using is not the propper url for flash, flash is now owned by adobe and not macromedia which would suggest an out of date sources.list
```

sudo apt-get update

```then 
```

sudo apt-get install flashplugin-nonfree

```If that does not work then goto the adobe site and download the plugin from there. [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 

Select APT for Ubuntu 9.04+ and it should be failry obvious how to proceed.

Good luck

---

### Post by linux18 on 2010-07-30
get the flash aid extention for firefox, it solved all of my problems

---

### Post by Raymond2201 on 2010-07-30
That works too :)

---

