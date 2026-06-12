---
title: "Sudo apt-get -f doesnt work"
date: 2011-01-09
forum: General Help
---

### Post by abdusamed on 2011-01-09
i'm havng issues

```

bahie@bahie-laptop:~$ sudo apt-get install screenlets python-rsvg
[sudo] password for bahie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-rsvg is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (>= 1:2.7.9) but 1:2.7.7-1ubuntu0+pidgin1.10.04 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bahie@bahie-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  xclip libalut0 virtualbox-ose-dkms
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  pidgin-data
The following packages will be upgraded:
  pidgin-data
1 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
3 not fully installed or removed.
Need to get 0B/8,650kB of archives.
After this operation, 463kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 277355 files and directories currently installed.)
Preparing to replace pidgin-data 1:2.7.7-1ubuntu0+pidgin1.10.04 (using .../pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb) ...
Unpacking replacement pidgin-data ...
dpkg: error processing /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/pidgin/protocols/48/facebook.png', which is also in package pidgin-facebookchat 0:1.67+svn746-1~frasten1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**i can't install anything **

---

### Post by wilee-nilee on 2011-01-09
try these two commands,in this order.
sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by abdusamed on 2011-01-09
[B]not fixed
[/B]```

bahie@bahie-laptop:~$ sudo dpkg --configure -a
[sudo] password for bahie: 
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on pidgin-data (>= 1:2.7.9); however:
  Version of pidgin-data on system is 1:2.7.7-1ubuntu0+pidgin1.10.04.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin-blinklight:
 pidgin-blinklight depends on pidgin (<< 1:3.0); however:
  Package pidgin is not configured yet.
 pidgin-blinklight depends on pidgin (>= 1:2.4); however:
  Package pidgin is not configured yet.
dpkg: error processing pidgin-blinklight (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin-autoresize:
 pidgin-autoresize depends on pidgin (<< 1:3.0); however:
  Package pidgin is not configured yet.
 pidgin-autoresize depends on pidgin (>= 1:2.7); however:
  Package pidgin is not configured yet.
dpkg: error processing pidgin-autoresize (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
 pidgin-blinklight
 pidgin-autoresize
bahie@bahie-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  xclip libalut0 virtualbox-ose-dkms
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  pidgin-data
The following packages will be upgraded:
  pidgin-data
1 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
3 not fully installed or removed.
Need to get 0B/8,650kB of archives.
After this operation, 463kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 277355 files and directories currently installed.)
Preparing to replace pidgin-data 1:2.7.7-1ubuntu0+pidgin1.10.04 (using .../pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb) ...
Unpacking replacement pidgin-data ...
dpkg: error processing /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/pidgin/protocols/48/facebook.png', which is also in package pidgin-facebookchat 0:1.67+svn746-1~frasten1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bahie@bahie-laptop:~$ 

```

---

### Post by wilee-nilee on 2011-01-09
Look in synaptic in custom filters-broken. You have a dependency problem with pidgin I believe look at it if it isn't in broken.

---

### Post by abdusamed on 2011-01-09
> **wilee-nilee said:**
> Look in synaptic in custom filters-broken. You have a dependency problem with pidgin I believe look at it if it isn't in broken.

pidgin was in the broken list under custom filter... but when I tried removing ...

this message popped up

```

E: /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb: trying to overwrite '/usr/share/pixmaps/pidgin/protocols/48/facebook.png', which is also in package pidgin-facebookchat 0

```

---

### Post by Sava on 2011-01-09
> **abdusamed said:**
> i'm havng issues



had the same issues, i gave up and just removed pidgin from Synaptic (while uncheck pidgin-data to prevent it from upgrading and giving the same error msgs of course)

try that

---

### Post by jmatthews13 on 2011-01-09
[http://ubuntuforums.org/showpost.php?p=10335589&postcount=2](http://ubuntuforums.org/showpost.php?p=10335589&postcount=2)

> The issue here is with pidgin-facebookchat plugin, which has yet to be fixed.

Removing just pidgin-facebookchat is useless.

Quick solution is to make sure you've made a copy of your .purple folder (in case something goes wrong, though the folder should remain untouched), then remove pidgin via Synaptic or command line, then reinstall.

Hopefully FBChat plugin will be fixed soon.

---

### Post by abdusamed on 2011-01-10
Thanks, I did a different thing..

killall pidgin

Removed pidgin

sudo apt-get update

Reinstalled pidigin

working fine :)

---

