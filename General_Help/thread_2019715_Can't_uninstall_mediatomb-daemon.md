---
title: "Can't uninstall mediatomb-daemon"
date: 2012-07-07
forum: General Help
---

### Post by UndeadCircus on 2012-07-07
Hey guys,

I just upgraded my headless server to 12.04 LTS Server edition this morning. While doing the upgraded, it spit out an error regarding the Mediatomb daemon not being able to be upgraded. It looks like it upgraded the main OS though, so I think that went okay. However, I tried this command after the LTS upgrade:

> sudo apt-get remove --purge mediatomb

and I was met with this:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mediatomb is not installed, so not removed
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration1 notification-daemon libcanberra-gtk3-0 libindicator6 libx264-116 kdebase-runtime libproxy0 libminiupnpc5 libnotify4 libcanberra-gtk3-module libxfont1 libhunspell-1.2-0
  libept1 libdbusmenu-gtk4 libvpx0 libmagickcore3 libaudiofile0 libappindicator1 libjpeg62 xfonts-utils libexiv2-10 libmysqlclient16 libmagickwand3 libmagickcore3-extra libattica0
  mediatomb-daemon libjs-prototype libindicator3-6 libexif12 xfonts-encodings defoma libnatpmp1 x-ttcidfont-conf mediatomb-common libllvm2.9
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mediatomb-daemon
The following packages will be upgraded:
  mediatomb-daemon
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,956 B of archives.
After this operation, 35.8 kB disk space will be freed.
Do you want to continue [Y/n]?

So I hit Y and was given this:

> (Reading database ... 66146 files and directories currently installed.)
Preparing to replace mediatomb-daemon 0.12.1-0ubuntu2 (using .../mediatomb-daemon_0.12.1-0ubuntu4_all.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error processing /var/cache/apt/archives/mediatomb-daemon_0.12.1-0ubuntu4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 /var/cache/apt/archives/mediatomb-daemon_0.12.1-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rford@server:~$

I don't know how in the world to uninstall MediaTomb completely so that I can reinstall it fresh and new and just re-do my configuration. I really don't want to completely re-install the OS because it's configured exactly the way I want it, but I guess if that's what I have to do, then I'll do it.

I also tried this command:

> sudo apt-get -f install

and was given this:

> rford@server:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration1 notification-daemon libcanberra-gtk3-0 libindicator6 libx264-116 kdebase-runtime libproxy0 libminiupnpc5 libnotify4 libcanberra-gtk3-module libxfont1 libhunspell-1.2-0
  libept1 libdbusmenu-gtk4 libvpx0 libmagickcore3 libaudiofile0 libappindicator1 libjpeg62 xfonts-utils libexiv2-10 libmysqlclient16 libmagickwand3 libmagickcore3-extra libattica0
  mediatomb-daemon libjs-prototype libindicator3-6 libexif12 xfonts-encodings defoma libnatpmp1 x-ttcidfont-conf mediatomb-common libllvm2.9
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mediatomb-daemon
The following packages will be upgraded:
  mediatomb-daemon
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,956 B of archives.
After this operation, 35.8 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66146 files and directories currently installed.)
Preparing to replace mediatomb-daemon 0.12.1-0ubuntu2 (using .../mediatomb-daemon_0.12.1-0ubuntu4_all.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: warning: subprocess old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error processing /var/cache/apt/archives/mediatomb-daemon_0.12.1-0ubuntu4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 /var/cache/apt/archives/mediatomb-daemon_0.12.1-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone help me out here? I'm dying for a solution!

Thanks!
Ricky

---

### Post by UndeadCircus on 2012-07-07
I should also add that I've even tried doing this:

> sudo apt-get autoremove

And this is how it went:

> rford@server:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  defoma kdebase-runtime libappindicator1 libattica0 libaudiofile0 libcanberra-gtk3-0 libcanberra-gtk3-module libdbusmenu-gtk4 libept1 libexif12 libexiv2-10 libhunspell-1.2-0 libindicator3-6
  libindicator6 libjpeg62 libjs-prototype liblaunchpad-integration1 libllvm2.9 libmagickcore3 libmagickcore3-extra libmagickwand3 libminiupnpc5 libmysqlclient16 libnatpmp1 libnotify4 libproxy0
  libvpx0 libx264-116 libxfont1 mediatomb-common mediatomb-daemon notification-daemon x-ttcidfont-conf xfonts-encodings xfonts-utils
0 upgraded, 0 newly installed, 35 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 42.9 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing mediatomb-daemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 66146 files and directories currently installed.)
Removing mediatomb-common ...
Removing x-ttcidfont-conf ...
Purging font configuration of x-ttcidfont-conf...
Purging category cmap..
Purging category cid..
Purging category truetype..
Removing defoma ...
Removing kdebase-runtime ...
Removing libappindicator1 ...
Removing libattica0 ...
Removing libaudiofile0 ...
Removing notification-daemon ...
Removing libcanberra-gtk3-module ...
Removing libcanberra-gtk3-0 ...
Removing libdbusmenu-gtk4 ...
Removing libept1 ...
Removing libexif12 ...
Removing libexiv2-10 ...
Removing libhunspell-1.2-0 ...
Removing libindicator3-6 ...
Removing libindicator6 ...
Removing libmagickcore3-extra ...
Removing libmagickwand3 ...
Removing libmagickcore3 ...
Removing libjpeg62 ...
Removing libjs-prototype ...
Removing liblaunchpad-integration1 ...
Removing libllvm2.9 ...
Removing libminiupnpc5 ...
Removing libmysqlclient16 ...
Removing libnatpmp1 ...
Removing libnotify4 ...
Removing libproxy0 ...
Removing libvpx0 ...
Removing libx264-116 ...
Removing xfonts-utils ...
Removing libxfont1 ...
Removing xfonts-encodings ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for gconf2 ...
Processing triggers for fontconfig ...
Errors were encountered while processing:
 mediatomb-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
rford@server:~$

---

