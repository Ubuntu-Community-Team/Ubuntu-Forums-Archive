---
title: "help with intialisin package information"
date: 2012-07-03
forum: General Help
---

### Post by jakefish on 2012-07-03
hello i am having problems with my software updater, it began the other day, when the power was cut to my home, and when i turned my pc back on, everything appeared fine, but i get the 'busy' symbol in the top left of the screen.

When I try and update i get this

The package system is broken

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

and the details are

The following packages have unmet dependencies:

libgail-3-0: Depends: libgtk-3-0 (= 3.4.2-0ubuntu0.3) but 3.4.2-0ubuntu0.2 is installed
libgtk-3-0: Depends: libgtk-3-common (= 3.4.2-0ubuntu0.2) but 3.4.2-0ubuntu0.3 is installed
            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2 is installed
            Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.3-2build1 is installed
            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is installed
            Depends: libxi6 (>= 2:1.2.99.4) but 2:1.6.0-0ubuntu2 is installed
            Depends: libxrandr2 (>= 2:1.2.99.3) but 2:1.3.2-2 is installed
libgtk-3-bin: Depends: libgtk-3-0 (>= 3.4.2-0ubuntu0.3) but 3.4.2-0ubuntu0.2 is installed
              Depends: libgtk-3-common (= 3.4.2-0ubuntu0.3) but 3.4.2-0ubuntu0.3 is installed


My sources list is

[HTML]# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://archive.ubuntu.com/ubuntu precise main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates universe main multiverse restricted[/HTML]

I cannot do anything with the software centre, i cannot remove or install, the internet works ok, but does occasionally crash


I hope you can help

John

---

### Post by msammels on 2012-07-03
Did you try this:

```
sudo apt-get install -f
```

Like it asked you to?

---

### Post by jakefish on 2012-07-04
jakefish@jakefish-System-Product-Name:~$ sudo apt-get install -f
[sudo] password for jakefish: 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing pd-windowing (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


thanks for your help

i got this error message

John

---

### Post by jakefish on 2012-07-06
also tried this

jakefish@jakefish-System-Product-Name:~$ sudo apt-get purge
[sudo] password for jakefish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 glabels : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
 libgnome2-perl : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
 libgnome2.24-cil : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
 python-gnome2 : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
 python-gnomeapplet : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
 rtkit : Depends: libdbus-1-3 (= ~= 1.0.2) but 1.4.6-1ubuntu6 is installed
 tsclient : Depends: libgnomeui-0 (>= 2.22.0) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by jakefish on 2012-07-06
also this

[HTML]Get:103 http://archive.ubuntu.com/ubuntu/ precise/main libgnomeui-0 amd64 2.24.5-2ubuntu2 [257 kB]
Get:104 http://archive.ubuntu.com/ubuntu/ precise/main python-glade2 amd64 2.24.0-3 [10.3 kB]
Get:105 http://archive.ubuntu.com/ubuntu/ precise/universe python-gtksourceview2 amd64 2.10.1-2build1 [93.7 kB]
Get:106 http://archive.ubuntu.com/ubuntu/ precise/main python-gconf amd64 2.28.1+dfsg-1 [28.5 kB]
Get:107 http://archive.ubuntu.com/ubuntu/ precise/main python-gtk2 amd64 2.24.0-3 [894 kB]
Get:108 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-gobject all 3.2.2-1~precise [2,468 B]
Get:109 http://archive.ubuntu.com/ubuntu/ precise/main python-gobject-2 amd64 2.28.6-10ubuntu1 [240 kB]
Get:110 http://archive.ubuntu.com/ubuntu/ precise/main libgirepository-1.0-1 amd64 1.32.0-1 [101 kB]
Get:111 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-gi amd64 3.2.2-1~precise [222 kB]
Get:112 http://archive.ubuntu.com/ubuntu/ precise/main gir1.2-freedesktop amd64 1.32.0-1 [6,638 B]
Get:113 http://archive.ubuntu.com/ubuntu/ precise/main gir1.2-glib-2.0 amd64 1.32.0-1 [157 kB]
Get:114 http://archive.ubuntu.com/ubuntu/ precise/main gir1.2-notify-0.7 amd64 0.7.5-1 [3,712 B]
Get:115 http://archive.ubuntu.com/ubuntu/ precise/main libnotify4 amd64 0.7.5-1 [19.5 kB]
Get:116 http://archive.ubuntu.com/ubuntu/ precise/main telepathy-logger amd64 0.4.0-0ubuntu1 [7,252 B]
Get:117 http://archive.ubuntu.com/ubuntu/ precise/main libtelepathy-logger2 amd64 0.4.0-0ubuntu1 [81.3 kB]
Get:118 http://archive.ubuntu.com/ubuntu/ precise-updates/main empathy-common all 3.4.2.1-0ubuntu1 [455 kB]
Get:119 http://archive.ubuntu.com/ubuntu/ precise-updates/main libnautilus-extension1a amd64 1:3.4.2-0ubuntu3 [51.5 kB]
Get:120 http://archive.ubuntu.com/ubuntu/ precise/main libcolord1 amd64 0.1.16-2 [48.6 kB]
Get:121 http://archive.ubuntu.com/ubuntu/ precise/main gnome-desktop3-data all 3.4.1-0ubuntu1 [28.4 kB]
Get:122 http://archive.ubuntu.com/ubuntu/ precise/main libgnome-desktop-3-2 amd64 3.4.1-0ubuntu1 [102 kB]
Get:123 http://archive.ubuntu.com/ubuntu/ precise/main libxklavier16 amd64 5.2.1-1ubuntu1 [50.2 kB]
Get:124 http://archive.ubuntu.com/ubuntu/ precise/main libgnomekbd-common all 3.4.0.2-1 [8,584 B]
Get:125 http://archive.ubuntu.com/ubuntu/ precise/main libgnomekbd7 amd64 3.4.0.2-1 [54.7 kB]
Get:126 http://archive.ubuntu.com/ubuntu/ precise/main liblcms2-2 amd64 2.2+git20110628-2ubuntu3 [142 kB]
Get:127 http://archive.ubuntu.com/ubuntu/ precise/main libltdl7 amd64 2.4.2-1ubuntu1 [37.6 kB]
Get:128 http://archive.ubuntu.com/ubuntu/ precise-updates/main libpulsedsp amd64 1:1.1-0ubuntu15.1 [24.8 kB]
Get:129 http://archive.ubuntu.com/ubuntu/ precise-updates/main pulseaudio-utils amd64 1:1.1-0ubuntu15.1 [61.6 kB]
Get:130 http://archive.ubuntu.com/ubuntu/ precise-updates/main pulseaudio amd64 1:1.1-0ubuntu15.1 [929 kB]
Get:131 http://archive.ubuntu.com/ubuntu/ precise-updates/main pulseaudio-module-bluetooth amd64 1:1.1-0ubuntu15.1 [82.4 kB]
Get:132 http://archive.ubuntu.com/ubuntu/ precise-updates/main pulseaudio-esound-compat amd64 1:1.1-0ubuntu15.1 [36.9 kB]
Get:133 http://archive.ubuntu.com/ubuntu/ precise-updates/main pulseaudio-module-gconf amd64 1:1.1-0ubuntu15.1 [14.0 kB]
Get:134 http://archive.ubuntu.com/ubuntu/ precise-updates/main pulseaudio-module-x11 amd64 1:1.1-0ubuntu15.1 [19.2 kB]
Get:135 http://archive.ubuntu.com/ubuntu/ precise/main libjson0 amd64 0.9-1ubuntu1 [16.3 kB]
Get:136 http://archive.ubuntu.com/ubuntu/ precise-updates/main libpulse-mainloop-glib0 amd64 1:1.1-0ubuntu15.1 [13.1 kB]
Get:137 http://archive.ubuntu.com/ubuntu/ precise-updates/main libpulse0 amd64 1:1.1-0ubuntu15.1 [289 kB]
Get:138 http://archive.ubuntu.com/ubuntu/ precise/main libwacom-common all 0.4-1ubuntu1 [8,232 B]
Get:139 http://archive.ubuntu.com/ubuntu/ precise/main libwacom2 amd64 0.4-1ubuntu1 [13.0 kB]
Get:140 http://archive.ubuntu.com/ubuntu/ precise-updates/main nautilus-data all 1:3.4.2-0ubuntu3 [63.4 kB]
Get:141 http://archive.ubuntu.com/ubuntu/ precise-updates/main ubuntuone-client-gnome amd64 3.0.1-0ubuntu1 [34.0 kB]
Get:142 http://archive.ubuntu.com/ubuntu/ precise/main python-twisted-bin amd64 11.1.0-1ubuntu2 [22.8 kB]
Get:143 http://archive.ubuntu.com/ubuntu/ precise/main python-twisted-core all 11.1.0-1ubuntu2 [1,209 kB]
Get:144 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-ubuntuone-storageprotocol all 3.0.0-0ubuntu1.1 [62.9 kB]
Get:145 http://archive.ubuntu.com/ubuntu/ precise-updates/main ubuntuone-client all 3.0.1-0ubuntu1.0.1 [46.7 kB]
Get:146 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-ubuntuone-client all 3.0.1-0ubuntu1.0.1 [232 kB]
Get:147 http://archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-gtk-3.0 amd64 3.4.2-0ubuntu0.3 [236 kB]
Get:148 http://archive.ubuntu.com/ubuntu/ precise/main gir1.2-javascriptcoregtk-3.0 amd64 1.8.0-0ubuntu2 [12.7 kB]
Get:149 http://archive.ubuntu.com/ubuntu/ precise/main gir1.2-webkit-3.0 amd64 1.8.0-0ubuntu2 [66.7 kB]
Get:150 http://archive.ubuntu.com/ubuntu/ precise/main python-httplib2 all 0.7.2-1ubuntu2 [57.2 kB]
Get:151 http://archive.ubuntu.com/ubuntu/ precise-updates/main ubuntu-sso-client all 3.0.0-0ubuntu2 [3,062 B]
Get:152 http://archive.ubuntu.com/ubuntu/ precise-updates/main python-ubuntu-sso-client all 3.0.0-0ubuntu2 [55.5 kB]
Get:153 http://archive.ubuntu.com/ubuntu/ precise-updates/main libdbusmenu-glib4 amd64 0.6.2-0ubuntu0.1 [47.7 kB]
Get:154 http://archive.ubuntu.com/ubuntu/ precise-updates/main libdbusmenu-gtk3-4 amd64 0.6.2-0ubuntu0.1 [31.4 kB]
Get:155 http://archive.ubuntu.com/ubuntu/ precise/main libindicator3-7 amd64 0.5.0-0ubuntu1 [24.9 kB]
Get:156 http://archive.ubuntu.com/ubuntu/ precise/main libappindicator3-1 amd64 0.4.92-0ubuntu1 [22.7 kB]
Get:157 http://archive.ubuntu.com/ubuntu/ precise/main libgnome-bluetooth8 amd64 3.2.2-0ubuntu5 [55.5 kB]
Get:158 http://archive.ubuntu.com/ubuntu/ precise/main libnm-gtk-common all 0.9.4.1-0ubuntu2 [6,118 B]
Get:159 http://archive.ubuntu.com/ubuntu/ precise/main libnm-gtk0 amd64 0.9.4.1-0ubuntu2 [67.8 kB]
Get:160 http://archive.ubuntu.com/ubuntu/ precise/main network-manager-pptp amd64 0.9.4.0-0ubuntu1 [22.4 kB]
Get:161 http://archive.ubuntu.com/ubuntu/ precise/main libnl-3-200 amd64 3.2.3-2ubuntu2 [46.6 kB]
Get:162 http://archive.ubuntu.com/ubuntu/ precise/main libnl-genl-3-200 amd64 3.2.3-2ubuntu2 [10.0 kB]
Get:163 http://archive.ubuntu.com/ubuntu/ precise/main libnl-route-3-200 amd64 3.2.3-2ubuntu2 [108 kB]
Get:164 http://archive.ubuntu.com/ubuntu/ precise/main openssh-client amd64 1:5.9p1-5ubuntu1 [943 kB]
Get:165 http://archive.ubuntu.com/ubuntu/ precise-updates/main libssl1.0.0 amd64 1.0.1-4ubuntu5.2 [1,011 kB]
Get:166 http://archive.ubuntu.com/ubuntu/ precise/main debianutils amd64 4.2.1ubuntu2 [65.2 kB]
Get:167 http://archive.ubuntu.com/ubuntu/ precise/main initscripts amd64 2.88dsf-13.10ubuntu11 [27.8 kB]
Get:168 http://archive.ubuntu.com/ubuntu/ precise/main mountall amd64 2.36 [67.0 kB]
Get:169 http://archive.ubuntu.com/ubuntu/ precise/main wpasupplicant amd64 0.7.3-6ubuntu2 [490 kB]
Get:170 http://archive.ubuntu.com/ubuntu/ precise-updates/main network-manager amd64 0.9.4.0-0ubuntu4.1 [530 kB]
Get:171 http://archive.ubuntu.com/ubuntu/ precise-updates/main libgtk-3-bin amd64 3.4.2-0ubuntu0.3 [15.9 kB]
Get:172 http://archive.ubuntu.com/ubuntu/ precise/main gnome-icon-theme all 3.4.0-0ubuntu1 [656 kB]
Get:173 http://archive.ubuntu.com/ubuntu/ precise/main gir1.2-gnomebluetooth-1.0 amd64 3.2.2-0ubuntu5 [5,738 B]
Get:174 http://archive.ubuntu.com/ubuntu/ precise/main libexempi3 amd64 2.2.0-1 [448 kB]
Get:175 http://archive.ubuntu.com/ubuntu/ precise/main liblaunchpad-integration-3.0-1 amd64 0.1.56 [8,744 B]
Get:176 http://archive.ubuntu.com/ubuntu/ precise/main libdee-1.0-4 amd64 1.0.10-0ubuntu1 [85.8 kB]
Get:177 http://archive.ubuntu.com/ubuntu/ precise-updates/main libunity9 amd64 5.12.0-0ubuntu1 [161 kB]
Get:178 http://archive.ubuntu.com/ubuntu/ precise-updates/main libzeitgeist-1.0-1 amd64 0.3.18-1ubuntu1 [45.4 kB]
Get:179 http://archive.ubuntu.com/ubuntu/ precise/main gnome-session-common all 3.2.1-0ubuntu8 [41.6 kB]
Get:180 http://archive.ubuntu.com/ubuntu/ precise-updates/main libgnome-control-center1 amd64 1:3.4.2-0ubuntu0.2 [79.5 kB]
Get:181 http://archive.ubuntu.com/ubuntu/ precise/main libgnome-menu-3-0 amd64 3.4.0-0ubuntu1 [55.1 kB]
Get:182 http://archive.ubuntu.com/ubuntu/ precise-updates/main libaccountsservice0 amd64 0.6.15-2ubuntu9.1 [30.5 kB]
Get:183 http://archive.ubuntu.com/ubuntu/ precise-updates/main accountsservice amd64 0.6.15-2ubuntu9.1 [44.1 kB]
Get:184 http://archive.ubuntu.com/ubuntu/ precise/main apg amd64 2.2.3.dfsg.1-2 [65.5 kB]
Get:185 http://archive.ubuntu.com/ubuntu/ precise/main libpam-runtime all 1.1.3-7ubuntu2 [40.4 kB]
Get:186 http://archive.ubuntu.com/ubuntu/ precise/universe gdm amd64 3.0.4-0ubuntu15 [1,733 kB]
Get:187 http://archive.ubuntu.com/ubuntu/ precise-updates/main gnome-control-center-data all 1:3.4.2-0ubuntu0.2 [1,121 kB]
Get:188 http://archive.ubuntu.com/ubuntu/ precise/main gnome-icon-theme-symbolic all 3.4.0-1 [96.4 kB]
Get:189 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-system2.0-cil all 2.10.8.1-1ubuntu2.1 [1,557 kB]
Get:190 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-security4.0-cil all 2.10.8.1-1ubuntu2.1 [126 kB]
Get:191 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-system-xml4.0-cil all 2.10.8.1-1ubuntu2.1 [441 kB]
Get:192 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-system-security4.0-cil all 2.10.8.1-1ubuntu2.1 [61.3 kB]
Get:193 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-system-configuration4.0-cil all 2.10.8.1-1ubuntu2.1 [58.9 kB]
Get:194 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-system4.0-cil all 2.10.8.1-1ubuntu2.1 [664 kB]
Get:195 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-posix4.0-cil all 2.10.8.1-1ubuntu2.1 [84.2 kB]
Get:196 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-system-core4.0-cil all 2.10.8.1-1ubuntu2.1 [280 kB]
Get:197 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-csharp4.0-cil all 2.10.8.1-1ubuntu2.1 [415 kB]
Get:198 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-management4.0-cil all 2.10.8.1-1ubuntu2.1 [13.6 kB]
Get:199 http://archive.ubuntu.com/ubuntu/ precise-updates/main mono-csharp-shell all 2.10.8.1-1ubuntu2.1 [30.6 kB]
Get:200 http://archive.ubuntu.com/ubuntu/ precise-updates/main mono-gmcs all 2.10.8.1-1ubuntu2.1 [422 kB]
Get:201 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-corlib2.0-cil all 2.10.8.1-1ubuntu2.1 [915 kB]
Get:202 http://archive.ubuntu.com/ubuntu/ precise-updates/main mono-runtime amd64 2.10.8.1-1ubuntu2.1 [1,557 kB]
Get:203 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-corlib4.0-cil all 2.10.8.1-1ubuntu2.1 [1,008 kB]
Get:204 http://archive.ubuntu.com/ubuntu/ precise-updates/main mono-4.0-gac all 2.10.8.1-1ubuntu2.1 [19.8 kB]
Get:205 http://archive.ubuntu.com/ubuntu/ precise-updates/main mono-gac all 2.10.8.1-1ubuntu2.1 [13.9 kB]
Get:206 http://archive.ubuntu.com/ubuntu/ precise/main libswitch-perl all 2.16-2 [19.2 kB]
Get:207 http://archive.ubuntu.com/ubuntu/ precise/main libclass-isa-perl all 0.36-3 [11.9 kB]
Get:208 http://archive.ubuntu.com/ubuntu/ precise/main doc-base all 0.10.3 [80.9 kB]
Get:209 http://archive.ubuntu.com/ubuntu/ precise/main perl-modules all 5.14.2-6ubuntu2 [3,369 kB]
Get:210 http://archive.ubuntu.com/ubuntu/ precise/main update-inetd all 4.41 [19.5 kB]
Get:211 http://archive.ubuntu.com/ubuntu/ precise-updates/main libsnmp-base all 5.4.3~dfsg-2.4ubuntu1.1 [213 kB]
Get:212 http://archive.ubuntu.com/ubuntu/ precise/main libperl5.14 amd64 5.14.2-6ubuntu2 [1,224 B]
Get:213 http://archive.ubuntu.com/ubuntu/ precise-updates/main libsnmp15 amd64 5.4.3~dfsg-2.4ubuntu1.1 [1,333 kB]
Get:214 http://archive.ubuntu.com/ubuntu/ precise/universe libnet-dbus-perl amd64 1.0.0-1build1 [219 kB]
Get:215 http://archive.ubuntu.com/ubuntu/ precise-updates/main libapparmor1 amd64 2.7.102-0ubuntu3.1 [38.2 kB]
Get:216 http://archive.ubuntu.com/ubuntu/ precise-updates/main libapparmor-perl amd64 2.7.102-0ubuntu3.1 [30.2 kB]
Get:217 http://archive.ubuntu.com/ubuntu/ precise/universe frozen-bubble amd64 2.2.0-2ubuntu3 [170 kB]
Get:218 http://archive.ubuntu.com/ubuntu/ precise/universe frozen-bubble-data all 2.2.0-2ubuntu3 [19.8 MB]
Get:219 http://archive.ubuntu.com/ubuntu/ precise/universe libsdl-gfx1.2-4 amd64 2.0.23-1 [48.0 kB]
Get:220 http://archive.ubuntu.com/ubuntu/ precise/universe libsdl-perl amd64 2.2.5-1build2 [871 kB]
Get:221 http://archive.ubuntu.com/ubuntu/ precise/main libdb5.1 amd64 5.1.25-11build1 [700 kB]
Get:222 http://archive.ubuntu.com/ubuntu/ precise/main perl amd64 5.14.2-6ubuntu2 [4,417 kB]
Get:223 http://archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:224 http://archive.ubuntu.com/ubuntu/ precise/main libio-pty-perl amd64 1:1.08-1build2 [36.7 kB]
Get:225 http://archive.ubuntu.com/ubuntu/ precise/main libhtml-parser-perl amd64 3.69-1build1 [97.3 kB]
Get:226 http://archive.ubuntu.com/ubuntu/ precise/main libcairo-perl amd64 1.081-1build2 [123 kB]
Get:227 http://archive.ubuntu.com/ubuntu/ precise/main libgtk2-perl amd64 2:1.223-1build3 [880 kB]
Get:228 http://archive.ubuntu.com/ubuntu/ precise/main libalgorithm-diff-xs-perl amd64 0.04-2build2 [12.4 kB]
Get:229 http://archive.ubuntu.com/ubuntu/ precise/main libterm-readkey-perl amd64 2.30-4build3 [28.6 kB]
Get:230 http://archive.ubuntu.com/ubuntu/ precise/main libnet-dns-perl amd64 0.66-2ubuntu3 [275 kB]
Get:231 http://archive.ubuntu.com/ubuntu/ precise/main libglib-perl amd64 2:1.241-1 [393 kB]
Get:232 http://archive.ubuntu.com/ubuntu/ precise/universe libgnome2-vfs-perl amd64 1.081-3build1 [189 kB]
Get:233 http://archive.ubuntu.com/ubuntu/ precise/main libuuid-perl amd64 0.02-4ubuntu1 [9,620 B]
Get:234 http://archive.ubuntu.com/ubuntu/ precise-updates/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.2 [932 kB]
Get:235 http://archive.ubuntu.com/ubuntu/ precise/main libapt-pkg-perl amd64 0.1.25build2 [82.9 kB]
Get:236 http://archive.ubuntu.com/ubuntu/ precise/universe libgnome2-perl amd64 1.042-2build3 [273 kB]
Get:237 http://archive.ubuntu.com/ubuntu/ precise/main libdigest-hmac-perl all 1.03+dfsg-1 [12.1 kB]
Get:238 http://archive.ubuntu.com/ubuntu/ precise/universe libgnome2-canvas-perl amd64 1.002-2build3 [123 kB]
Get:239 http://archive.ubuntu.com/ubuntu/ precise/main libxml-parser-perl amd64 2.41-1build1 [265 kB]
Get:240 http://archive.ubuntu.com/ubuntu/ precise/main perl-base amd64 5.14.2-6ubuntu2 [1,515 kB]
Get:241 http://archive.ubuntu.com/ubuntu/ precise/main libtext-charwidth-perl amd64 0.04-7build1 [10.9 kB]
Get:242 http://archive.ubuntu.com/ubuntu/ precise/main libtext-iconv-perl amd64 1.7-5 [15.6 kB]
Get:243 http://archive.ubuntu.com/ubuntu/ precise/universe libgtk2-gladexml-perl amd64 1.007-1build2 [41.9 kB]
Get:244 http://archive.ubuntu.com/ubuntu/ precise/main libpango-perl amd64 1.222-1build1 [222 kB]
Get:245 http://archive.ubuntu.com/ubuntu/ precise/main liblocale-gettext-perl amd64 1.05-7build1 [19.3 kB]
Get:246 http://archive.ubuntu.com/ubuntu/ precise/main libyaml-tiny-perl all 1.50-1 [27.8 kB]
Get:247 http://archive.ubuntu.com/ubuntu/ precise/main libattr1 amd64 1:2.4.46-5ubuntu1 [10.7 kB]
Get:248 http://archive.ubuntu.com/ubuntu/ precise/main libacl1 amd64 2.2.51-5ubuntu1 [17.8 kB]
Get:249 http://archive.ubuntu.com/ubuntu/ precise/main liblzma5 amd64 5.1.1alpha+20110809-3 [88.7 kB]
Get:250 http://archive.ubuntu.com/ubuntu/ precise/main acl amd64 2.2.51-5ubuntu1 [43.2 kB]
Get:251 http://archive.ubuntu.com/ubuntu/ precise-updates/main policykit-1 amd64 0.104-1ubuntu1 [53.1 kB]
Get:252 http://archive.ubuntu.com/ubuntu/ precise/main colord amd64 0.1.16-2 [92.4 kB]
Get:253 http://archive.ubuntu.com/ubuntu/ precise/universe gstreamer0.10-plugins-bad amd64 0.10.22.3-2ubuntu2 [1,739 kB]
Get:254 http://archive.ubuntu.com/ubuntu/ precise/universe libgstreamer-plugins-bad0.10-0 amd64 0.10.22.3-2ubuntu2 [148 kB]
Get:255 http://archive.ubuntu.com/ubuntu/ precise/universe libkate1 amd64 0.4.1-1 [42.7 kB]
Get:256 http://archive.ubuntu.com/ubuntu/ precise/main libopenal1 amd64 1:1.13-4ubuntu3 [133 kB]
Get:257 http://archive.ubuntu.com/ubuntu/ precise/main libopenal-data all 1:1.13-4ubuntu3 [7,872 B]
Get:258 http://archive.ubuntu.com/ubuntu/ precise/main libyajl1 amd64 1.0.12-2 [17.5 kB]
Get:259 http://archive.ubuntu.com/ubuntu/ precise/main libraptor2-0 amd64 2.0.6-1 [177 kB]
Get:260 http://archive.ubuntu.com/ubuntu/ precise/main libmhash2 amd64 0.9.9.9-1 [105 kB]
Get:261 http://archive.ubuntu.com/ubuntu/ precise/main librasqal3 amd64 0.9.28-1 [197 kB]
Get:262 http://archive.ubuntu.com/ubuntu/ precise/main librdf0 amd64 1.0.14-1 [111 kB]
Get:263 http://archive.ubuntu.com/ubuntu/ precise/universe libslv2-9 amd64 0.6.6+dfsg1-1 [27.1 kB]
Get:264 http://archive.ubuntu.com/ubuntu/ precise/universe libspandsp2 amd64 0.0.6~pre18-2build1 [322 kB]
Get:265 http://archive.ubuntu.com/ubuntu/ precise/universe libvo-aacenc0 amd64 0.1.1-2 [74.8 kB]
Get:266 http://archive.ubuntu.com/ubuntu/ precise/universe libvo-amrwbenc0 amd64 0.1.1-2 [68.4 kB]
Get:267 http://archive.ubuntu.com/ubuntu/ precise/main libvpx1 amd64 1.0.0-1 [269 kB]
Get:268 http://archive.ubuntu.com/ubuntu/ precise/universe libzvbi-common all 0.2.33-4 [35.7 kB]
Get:269 http://archive.ubuntu.com/ubuntu/ precise/universe libzvbi0 amd64 0.2.33-4 [273 kB]
Get:270 http://archive.ubuntu.com/ubuntu/ precise/main libnettle4 amd64 2.4-1 [95.1 kB]
Get:271 http://archive.ubuntu.com/ubuntu/ precise/main libarchive12 amd64 3.0.3-6ubuntu1 [272 kB]
Get:272 http://archive.ubuntu.com/ubuntu/ precise-updates/main libatspi2.0-0 amd64 2.4.2-0ubuntu0.1 [57.3 kB]
Get:273 http://archive.ubuntu.com/ubuntu/ precise/main libglew1.6 amd64 1.6.0-4 [114 kB]
Get:274 http://archive.ubuntu.com/ubuntu/ precise/main libglewmx1.6 amd64 1.6.0-4 [101 kB]
Get:275 http://archive.ubuntu.com/ubuntu/ precise/main libglibmm-2.4-1c2a amd64 2.32.0-0ubuntu1 [481 kB]
Get:276 http://archive.ubuntu.com/ubuntu/ precise/main libibus-1.0-0 amd64 1.4.1-3ubuntu1 [112 kB]
Get:277 http://archive.ubuntu.com/ubuntu/ precise-updates/main mysql-common all 5.5.24-0ubuntu0.12.04.1 [13.5 kB]
Get:278 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmysqlclient18 amd64 5.5.24-0ubuntu0.12.04.1 [946 kB]
Get:279 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-test amd64 4:4.8.1-0ubuntu4.1 [60.2 kB]
Get:280 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-qt3support amd64 4:4.8.1-0ubuntu4.1 [1,022 kB]
Get:281 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-opengl amd64 4:4.8.1-0ubuntu4.1 [293 kB]
Get:282 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-svg amd64 4:4.8.1-0ubuntu4.1 [137 kB]
Get:283 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-declarative amd64 4:4.8.1-0ubuntu4.1 [1,062 kB]
Get:284 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqtgui4 amd64 4:4.8.1-0ubuntu4.1 [4,023 kB]
Get:285 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-designer amd64 4:4.8.1-0ubuntu4.1 [3,611 kB]
Get:286 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-script amd64 4:4.8.1-0ubuntu4.1 [758 kB]
Get:287 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-xmlpatterns amd64 4:4.8.1-0ubuntu4.1 [1,031 kB]
Get:288 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-network amd64 4:4.8.1-0ubuntu4.1 [534 kB]
Get:289 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-dbus amd64 4:4.8.1-0ubuntu4.1 [179 kB]
Get:290 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-xml amd64 4:4.8.1-0ubuntu4.1 [91.8 kB]
Get:291 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-sql-sqlite amd64 4:4.8.1-0ubuntu4.1 [22.5 kB]
Get:292 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-sql-mysql amd64 4:4.8.1-0ubuntu4.1 [30.0 kB]
Get:293 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqt4-sql amd64 4:4.8.1-0ubuntu4.1 [96.9 kB]
Get:294 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqtcore4 amd64 4:4.8.1-0ubuntu4.1 [2,022 kB]
Get:295 http://archive.ubuntu.com/ubuntu/ precise/main libvisual-0.4-plugins amd64 0.4.0.dfsg.1-7 [128 kB]
Get:296 http://archive.ubuntu.com/ubuntu/ precise/main libvisual-0.4-0 amd64 0.4.0-4 [107 kB]
Get:297 http://archive.ubuntu.com/ubuntu/ precise/main lightdm amd64 1.2.1-0ubuntu1 [97.6 kB]
Get:298 http://archive.ubuntu.com/ubuntu/ precise-updates/main krb5-locales all 1.10+dfsg~beta1-2ubuntu0.1 [8,826 B]
Get:299 http://archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-atspi-2.0 amd64 2.4.2-0ubuntu0.1 [16.1 kB]
Get:300 http://archive.ubuntu.com/ubuntu/ precise/universe python-pyatspi all 2.4.0+dfsg-0ubuntu3 [1,496 B]
Get:301 http://archive.ubuntu.com/ubuntu/ precise/main python-pyatspi2 all 2.4.0+dfsg-0ubuntu3 [31.9 kB]
Get:302 http://archive.ubuntu.com/ubuntu/ precise/universe at-spi all 2.4.0-1ubuntu2 [1,696 B]
Get:303 http://archive.ubuntu.com/ubuntu/ precise/main libatk-adaptor amd64 2.4.0-1ubuntu2 [120 kB]
Get:304 http://archive.ubuntu.com/ubuntu/ precise-updates/main at-spi2-core amd64 2.4.2-0ubuntu0.1 [43.9 kB]
Get:305 http://archive.ubuntu.com/ubuntu/ precise/main checkbox-gtk all 0.13.7 [20.1 kB]
Get:306 http://archive.ubuntu.com/ubuntu/ precise/main checkbox amd64 0.13.7 [1,439 kB]
Get:307 http://archive.ubuntu.com/ubuntu/ precise/main checkbox-qt amd64 0.13.7 [70.6 kB]
Get:308 http://archive.ubuntu.com/ubuntu/ precise/main compizconfig-backend-gconf amd64 0.9.5.92-0ubuntu5 [32.1 kB]
Get:309 http://archive.ubuntu.com/ubuntu/ precise/main libprotobuf7 amd64 2.4.1-1ubuntu2 [352 kB]
Get:310 http://archive.ubuntu.com/ubuntu/ precise/main compiz-plugins-main amd64 1:0.9.7.0~bzr19-0ubuntu10 [889 kB]
Get:311 http://archive.ubuntu.com/ubuntu/ precise-updates/main compiz-gnome amd64 1:0.9.7.8-0ubuntu1 [300 kB]
Get:312 http://archive.ubuntu.com/ubuntu/ precise-updates/main compiz-plugins amd64 1:0.9.7.8-0ubuntu1 [809 kB]
Get:313 http://archive.ubuntu.com/ubuntu/ precise/main libcompizconfig0 amd64 0.9.7.0~bzr428-0ubuntu6 [149 kB]
Get:314 http://archive.ubuntu.com/ubuntu/ precise-updates/main compiz-core amd64 1:0.9.7.8-0ubuntu1 [369 kB]
Get:315 http://archive.ubuntu.com/ubuntu/ precise/main libboost-serialization1.46.1 amd64 1.46.1-7ubuntu3 [186 kB]
Get:316 http://archive.ubuntu.com/ubuntu/ precise/main compiz-plugins-main-default amd64 1:0.9.7.0~bzr19-0ubuntu10 [750 kB]
Get:317 http://archive.ubuntu.com/ubuntu/ precise-updates/main libdecoration0 amd64 1:0.9.7.8-0ubuntu1 [38.4 kB]
Get:318 http://archive.ubuntu.com/ubuntu/ precise/main metacity amd64 1:2.34.1-1ubuntu11 [281 kB]
Get:319 http://archive.ubuntu.com/ubuntu/ precise/main libmetacity-private0 amd64 1:2.34.1-1ubuntu11 [120 kB]
Get:320 http://archive.ubuntu.com/ubuntu/ precise/main metacity-common all 1:2.34.1-1ubuntu11 [113 kB]
Get:321 http://archive.ubuntu.com/ubuntu/ precise-updates/main compiz-plugins-default amd64 1:0.9.7.8-0ubuntu1 [673 kB]
Get:322 http://archive.ubuntu.com/ubuntu/ precise/universe glabels amd64 2.2.8-3build1 [390 kB]
Get:323 http://archive.ubuntu.com/ubuntu/ precise/universe glabels-data all 2.2.8-3build1 [2,122 kB]
Get:324 http://archive.ubuntu.com/ubuntu/ precise/main gnome-font-viewer amd64 3.4.0-1 [19.1 kB]
Get:325 http://archive.ubuntu.com/ubuntu/ precise/main gnome-online-accounts amd64 3.4.0-0ubuntu1 [76.9 kB]
Get:326 http://archive.ubuntu.com/ubuntu/ precise/main indicator-power amd64 2.0-0ubuntu1 [13.8 kB]
Get:327 http://archive.ubuntu.com/ubuntu/ precise/main libatk-adaptor-schemas amd64 2.4.0-1ubuntu2 [2,104 B]
Get:328 http://archive.ubuntu.com/ubuntu/ precise/main libcdio13 amd64 0.83-1 [61.8 kB]
Get:329 http://archive.ubuntu.com/ubuntu/ precise/main libcdio-cdda1 amd64 0.83-1 [17.3 kB]
Get:330 http://archive.ubuntu.com/ubuntu/ precise/main libcdio-paranoia1 amd64 0.83-1 [16.7 kB]
Get:331 http://archive.ubuntu.com/ubuntu/ precise/main libido3-0.1-0 amd64 0.3.4-0ubuntu1 [24.4 kB]
Get:332 http://archive.ubuntu.com/ubuntu/ precise/main liblightdm-gobject-1-0 amd64 1.2.1-0ubuntu1 [30.7 kB]
Get:333 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-i18n4.0-cil all 2.10.8.1-1ubuntu2.1 [19.7 kB]
Get:334 http://archive.ubuntu.com/ubuntu/ precise-updates/main libmono-i18n-west4.0-cil all 2.10.8.1-1ubuntu2.1 [27.9 kB]
Get:335 http://archive.ubuntu.com/ubuntu/ precise/main libnotify-bin amd64 0.7.5-1 [7,298 B]
Get:336 http://archive.ubuntu.com/ubuntu/ precise-updates/main libnux-2.0-common all 2.12.0-0ubuntu1 [63.8 kB]
Get:337 http://archive.ubuntu.com/ubuntu/ precise-updates/main libnux-2.0-0 amd64 2.12.0-0ubuntu1 [905 kB]
Get:338 http://archive.ubuntu.com/ubuntu/ precise/main libpam-cap amd64 1:2.22-1ubuntu3 [7,704 B]
Get:339 http://archive.ubuntu.com/ubuntu/ precise-updates/main unity-services amd64 5.12-0ubuntu1.1 [37.5 kB]
Get:340 http://archive.ubuntu.com/ubuntu/ precise-updates/main libunity-core-5.0-5 amd64 5.12-0ubuntu1.1 [234 kB]
Get:341 http://archive.ubuntu.com/ubuntu/ precise/main libunity-misc4 amd64 4.0.4-0ubuntu2 [26.8 kB]
Get:342 http://archive.ubuntu.com/ubuntu/ precise/main libwnck-3-common all 3.4.0-0ubuntu1 [18.7 kB]
Get:343 http://archive.ubuntu.com/ubuntu/ precise/main libwnck-3-0 amd64 3.4.0-0ubuntu1 [121 kB]
Get:344 http://archive.ubuntu.com/ubuntu/ precise/main pnm2ppa all 1.13+nondbs-0ubuntu1 [1,648 B]
Get:345 http://archive.ubuntu.com/ubuntu/ precise/main printer-driver-pnm2ppa amd64 1.13+nondbs-0ubuntu1 [210 kB]
Get:346 http://archive.ubuntu.com/ubuntu/ precise/main rtkit amd64 0.10-2 [34.7 kB]
Get:347 http://archive.ubuntu.com/ubuntu/ precise-updates/main unity-greeter amd64 0.2.8-0ubuntu1.1 [85.3 kB]
Get:348 http://archive.ubuntu.com/ubuntu/ precise/main x11-common all 1:7.6+12ubuntu1 [57.7 kB]
Get:349 http://archive.ubuntu.com/ubuntu/ precise-updates/main xdiagnose all 2.5.1 [59.0 kB]
Get:350 http://archive.ubuntu.com/ubuntu/ precise/main libcanberra-gtk3-module amd64 0.28-3ubuntu3 [11.3 kB]
Fetched 170 MB in 1min 6s (2,548 kB/s)                                         
Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23522 package 'rtkit':
 `Depends' field, reference to `libdbus-1-3':
 implicit exact match on version number, suggest using `=' instead
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 23522 package 'rtkit':
 `Depends' field, reference to `libdbus-1-3':
 version value starts with non-alphanumeric, suggest adding a space
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23522 package 'rtkit':
 `Depends' field, reference to `libdbus-1-3': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
jakefish@jakefish-System-Product-Name:~$ 
[/HTML]

---

### Post by nutsy.ben on 2012-07-19
Not solved is it ?

I have a similar problem

---

