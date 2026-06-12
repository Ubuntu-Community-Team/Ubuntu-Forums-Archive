---
title: "Use of &quot;apt-get --install-suggests&quot; adds a lot!?"
date: 2012-09-12
forum: General Help
---

### Post by djetch on 2012-09-12
I have done a couple of searches in this specific forum and have no found any thread mentioning the use of 'sudo apt-get --install-suggests install blah' to get all of the suggested installs.  Does '--install-suggests' work recursively?  Is there another option to avoid this?  Are we doomed to copy and paste the original suggested list back in another command?

Here's an example:
- 1st apt-get install git; 
```
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn git-email git-gui gitk gitweb
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,741 kB of archives.
After this operation, 15.2 MB of additional disk space will be used.
```

-THEN apt-get --install-suggest install git

```
The following extra packages will be installed:
  cvs cvsps db4.8-util emacs emacs23 emacs23-bin-common emacs23-common emacs23-el emacsen-common exim4 exim4-base exim4-config exim4-daemon-light exim4-doc-html eximon4 fgetty gawk git-arch git-cvs
  git-daemon-run git-doc git-el git-email git-gui git-man git-svn gitk gitweb groff heirloom-mailx libapr1 libaprutil1 libauthen-ntlm-perl libauthen-sasl-perl libconfig-inifiles-perl libcxxtools-dev
  libcxxtools7 libdbd-sqlite3-perl libdbi-perl libemail-valid-perl liberror-perl libgssapi-perl libm17n-0 libmail-spf-perl libnet-daemon-perl libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl
  libnet-smtp-ssl-perl libnetaddr-ip-perl libotf0 libplrpc-perl libsigsegv2 libsvn-perl libsvn-ruby1.8 libsvn1 libterm-readkey-perl libtntnet-dev libtntnet9 m17n-contrib m17n-db m17n-docs mksh perl-doc psutils
  python-dbg python-subversion python-subversion-dbg python2.7-dbg rcs ri1.8 ruby1.8 ruby1.8-examples runit spf-tools-perl ssh subversion subversion-tools swaks tcl tk tk8.5 tla tla-doc tntnet tntnet-demos
  tntnet-doc tntnet-runtime xsltproc
Suggested packages:
  httpd-cgi libcgi-fast-perl python-gdbm-dbg python-tk-dbg socklog-run
Recommended packages:
  mailx
The following NEW packages will be installed:
  cvs cvsps db4.8-util emacs emacs23 emacs23-bin-common emacs23-common emacs23-el emacsen-common exim4 exim4-base exim4-config exim4-daemon-light exim4-doc-html eximon4 fgetty gawk git git-arch git-cvs
  git-daemon-run git-doc git-el git-email git-gui git-man git-svn gitk gitweb groff heirloom-mailx libapr1 libaprutil1 libauthen-ntlm-perl libauthen-sasl-perl libconfig-inifiles-perl libcxxtools-dev
  libcxxtools7 libdbd-sqlite3-perl libdbi-perl libemail-valid-perl liberror-perl libgssapi-perl libm17n-0 libmail-spf-perl libnet-daemon-perl libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl
  libnet-smtp-ssl-perl libnetaddr-ip-perl libotf0 libplrpc-perl libsigsegv2 libsvn-perl libsvn-ruby1.8 libsvn1 libterm-readkey-perl libtntnet-dev libtntnet9 m17n-contrib m17n-db m17n-docs mksh perl-doc psutils
  python-dbg python-subversion python-subversion-dbg python2.7-dbg rcs ri1.8 ruby1.8 ruby1.8-examples runit spf-tools-perl ssh subversion subversion-tools swaks tcl tk tk8.5 tla tla-doc tntnet tntnet-demos
  tntnet-doc tntnet-runtime xsltproc
0 upgraded, 90 newly installed, 0 to remove and 0 not upgraded.
Need to get 95.1 MB of archives.
After this operation, 262 MB of additional disk space will be used.
```

---

### Post by josephmills on 2012-09-12
So inside of ever debian package there is a file called the [COLOR="Olive"]control[/COLOR] file in this metadata file we fill out the correct information and we also put a line for suggest. so say that I have am making a package that is using mysql-client- what ever. 
 I would give the correct paramaters in the CONTROL file to say hey my package that I am making (app) needs mysql so it 
DEPENDS on it But it needs apache before that can install so it 
PRE_DEPENDS on apache 
I also think that PHP is needed but not to run my app but to make better. 
RECOMENDS: php


you can see all this with a couple commands
```
apt-cache poilcy <name of app>
```
example 
```

apt-cache show  mythbuntu-desktop

```


Shows
```

Package: mythbuntu-desktop
Priority: optional
Section: multiverse/metapackages
Installed-Size: 30
Maintainer: Ubuntu MythTV Teamm <ubuntu-mythtv@lists.ubuntu.com>
Architecture: amd64
Source: mythbuntu-meta
Version: 0.79
[COLOR="Red"]Depends:[/COLOR] [COLOR="Navy"]accountsservice, acpi-support, alsa-utils, jockey-gtk, lightdm, mythbuntu-control-centre, mythbuntu-default-settings, mythbuntu-lightdm-theme, mythtv-common, notify-osd, update-manager, xfce4-panel, xfce4-session, xfconf, xfdesktop4, xfwm4, xorg[/COLOR]
[COLOR="Red"]Recommends:[/COLOR] [COLOR="Indigo"]apport-gtk, avahi-autoipd, chromium-browser, dvb-apps, gcc, gnome-time-admin, hdhomerun-config, hdhomerun-config-gui, linux-headers-generic, make, mythbuntu-lirc-generator, mythbuntu-log-grabber, mythgallery, mythmusic, mythtv, mythtv-backend-master, mythtv-theme-mythbuntu, mythweb, network-manager-gnome, openssh-server, samba, software-center, thunar-volman, update-notifier, xfce4-terminal, xmltv, xscreensaver[/COLOR]
Filename: pool/multiverse/m/mythbuntu-meta/mythbuntu-desktop_0.79_amd64.deb
Size: 3024
MD5sum: cc31a81db1d87208d06b1761ee6af709
SHA1: 08776e5c4bc31b5f332cb735b5312a2cf7d25746
SHA256: 1c2859d25b18d2984873ac23ffa166b0b2e0e37ddc22f3df4de7c307735eb541
Description-en: The Mythbuntu standalone system
 This package depends on all of the packages in the Mythbuntu standalone system.
 This set of packages provides the essentials for an operable Mythbuntu
 system.  Many roles will contain other packages not listed here, so this
 package is fairly minimal to allow flexibility.
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.
Description-md5: 8971615f15e6eae57015be9ca4dc0136
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master

```

---

