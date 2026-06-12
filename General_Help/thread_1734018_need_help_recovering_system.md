---
title: "need help recovering system"
date: 2011-04-19
forum: General Help
---

### Post by marcusj2 on 2011-04-19
Hi,

I was running 10.04 and lost power in the middle of an upgrade. 
The system now boots to the splash screen and just..... sits......there...... with the logo and the pretty little dots rotating.

When I boot into recovery mode to repair broken packages I can get a command line at least. 

as root I run apt-get -f install 
and I get the following:

root@db-test1:/home/marc# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome empathy empathy-common evolution gnome-settings-daemon
Suggested packages:
  gnome-themes bug-buddy evolution-dbg evolution-plugins-experimental gnome-pilot-conduits
The following packages will be upgraded:
  compiz-gnome empathy empathy-common evolution gnome-settings-daemon
5 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
23 not fully installed or removed.
Need to get 0B/4,278kB of archives.
After this operation, 139kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 177067 files and directories currently installed.)
Preparing to replace metacity-common 1:2.30.1-0ubuntu1 (using .../metacity-common_1%3a2.30.1-0ubuntu1_all.deb) ...
Unpacking replacement metacity-common ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/metacity-common_1%3a2.30.1-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace compiz-gnome 1:0.8.4-0ubuntu15 (using .../compiz-gnome_1%3a0.8.4-0ubuntu15.3_i386.deb) ...
Unpacking replacement compiz-gnome ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.8.4-0ubuntu15.3_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace empathy 2.30.2-0ubuntu1 (using .../empathy_2.30.3-0ubuntu1_i386.deb) ...
Unpacking replacement empathy ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/empathy_2.30.3-0ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace empathy-common 2.30.2-0ubuntu1 (using .../empathy-common_2.30.3-0ubuntu1_all.deb) ...
Unpacking replacement empathy-common ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/empathy-common_2.30.3-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace evolution 2.28.3-0ubuntu10 (using .../evolution_2.28.3-0ubuntu10.2_i386.deb) ...
Unpacking replacement evolution ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/evolution_2.28.3-0ubuntu10.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace gnome-settings-daemon 2.30.1-0ubuntu1 (using .../gnome-settings-daemon_2.30.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gnome-settings-daemon ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/gnome-settings-daemon_2.30.1-0ubuntu1.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
gtk-update-icon-cache: symbol lookup error: /usr/lib/libgdk_pixbuf-2.0.so.0: undefined symbol: g_once_init_enter_impl
WARNING: icon cache generation failed
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/metacity-common_1%3a2.30.1-0ubuntu1_all.deb
 /var/cache/apt/archives/compiz-gnome_1%3a0.8.4-0ubuntu15.3_i386.deb
 /var/cache/apt/archives/empathy_2.30.3-0ubuntu1_i386.deb
 /var/cache/apt/archives/empathy-common_2.30.3-0ubuntu1_all.deb
 /var/cache/apt/archives/evolution_2.28.3-0ubuntu10.2_i386.deb
 /var/cache/apt/archives/gnome-settings-daemon_2.30.1-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help would be greatly appreciated.

Thanks much,

marc

---

### Post by Krytarik on 2011-04-19
Try reinstalling all those concerning packages:
```
apt-get install --reinstall metacity-common compiz-gnome empathy empathy-common evolution gnome-settings-daemon
```
Note: No need to use 'sudo' since the OP is already root.

Greetings.

---

### Post by marcusj2 on 2011-04-19
Thanks for the effort.

I tried your suggestion and received the exact same errors.

The common thread seems to be this particular error:

gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext
dpkg: error processing /var/cache/apt/archives/gnome-settings-daemon_2.30.1-0ubuntu1.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              gconftool-2: symbol lookup error: /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: undefined symbol: g_dgettext

Got any other tricks up your sleeve?

Thanks,

marc

---

### Post by Krytarik on 2011-04-19
Try following the steps stated here:
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by marcusj2 on 2011-04-20
I followed the steps as outlined in the provided link.

We'll see if someone can provide an answer.

Thanks,

marc

---

### Post by marcusj2 on 2011-04-20
Just a thought....

Is it not possible to simply do a repair i.e. using an installation disk just reinstall but only those components that are broken. Does ubuntu even have such a feature? 

I did boot the initial installation disk I used to create this machine and stepped through the first through screens but there was no such option. It just informed me that the system already had a ubuntu 10.04 installation and asked me if I wanted to install them side by side or clobber the existing install.

Any insights on this possible approach?

Thanks,

marc

---

