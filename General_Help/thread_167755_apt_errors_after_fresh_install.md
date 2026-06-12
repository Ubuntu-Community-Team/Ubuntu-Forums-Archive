---
title: "apt errors after fresh install"
date: 2006-04-29
forum: General Help
---

### Post by perunaion on 2006-04-29
During the final stages of a fresh install of Ubuntu (breezy) on my laptop, apt-get generated a series of segmentation faults and wouldn't finish.  Specifically, during the configuration stages of 10 packages.
[LIST]
[*] evince
[*] gucharmap
[*] gnome-pilot
[*] gnome-pilot-conduits
[*] gnome-system-tools
[*] ubuntu-docs
[*] update-manager
[*] update-notifier
[*] zenty
[*] ubuntu-desktop
[/LIST]

apt-get output attached. 

I've tried performing an *apt-get update*, *apt-get dist-upgrade*.  No change.  
Also tried *apt-get -f install*, no go either.

Any suggestions on how to fix this?  

-danny.

```

root@kimsay:~# apt-get install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up evince (0.4.0-0ubuntu4.1) ...
/var/lib/dpkg/info/evince.postinst: line 11:  9061 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gucharmap (1.4.4-1ubuntu1) ...
/var/lib/dpkg/info/gucharmap.postinst: line 16:  9068 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing gucharmap (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-pilot (2.0.13-0ubuntu10) ...
/var/lib/dpkg/info/gnome-pilot.postinst: line 6:  9073 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing gnome-pilot (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-pilot-conduits:
 gnome-pilot-conduits depends on gnome-pilot (>= 2.0.0); however:
  Package gnome-pilot is not configured yet.
dpkg: error processing gnome-pilot-conduits (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-system-tools (1.4.0-0ubuntu10) ...
/var/lib/dpkg/info/gnome-system-tools.postinst: line 11:  9080 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ubuntu-docs (5.10-6.3) ...
sh: line 1:  9087 Segmentation fault      /usr/bin/scrollkeeper-update -q >/dev/null 2>&1
warning: error occured during execution of /usr/bin/scrollkeeper-update
/var/lib/dpkg/info/ubuntu-docs.postinst: line 12:  9091 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 139
Setting up update-manager (0.42.2ubuntu12~breezy1) ...
/var/lib/dpkg/info/update-manager.postinst: line 6:  9096 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Setting up zenity (2.12.1-0ubuntu1) ...
/var/lib/dpkg/info/zenity.postinst: line 6:  9101 Segmentation fault      scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing zenity (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-pilot-conduits; however:
  Package gnome-pilot-conduits is not configured yet.
 ubuntu-desktop depends on gnome-system-tools; however:
  Package gnome-system-tools is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on ubuntu-docs; however:
  Package ubuntu-docs is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.
 ubuntu-desktop depends on zenity; however:
  Package zenity is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evince
 gucharmap
 gnome-pilot
 gnome-pilot-conduits
 gnome-system-tools
 ubuntu-docs
 update-manager
 update-notifier
 zenity
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

