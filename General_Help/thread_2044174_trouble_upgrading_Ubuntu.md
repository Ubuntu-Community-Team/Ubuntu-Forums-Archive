---
title: "trouble upgrading Ubuntu"
date: 2012-08-18
forum: General Help
---

### Post by waterfoul on 2012-08-18
Hi, I'm having trouble with dependencies. When I try and update Ubuntu (I'm on 11.10), I get the following error message: 

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

With detail:

```

The following packages have unmet dependencies:

firefox: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed

```

When I run ```
sudo apt-get install -f
``` I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgladeui-1-11 linux-headers-3.0.0-17 linux-headers-3.0.0-17-generic
  wine1.2-gecko libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox firefox-globalmenu
Suggested packages:
  latex-xft-fonts
The following packages will be REMOVED:
  adobe-flashplugin
The following packages will be upgraded:
  firefox firefox-globalmenu
2 upgraded, 0 newly installed, 1 to remove and 206 not upgraded.
1 not fully installed or removed.
Need to get 0 B/19.0 MB of archives.
After this operation, 9,449 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 223345 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I've seen similar threads, but nothing in them is helping my case. Thank you.

---

