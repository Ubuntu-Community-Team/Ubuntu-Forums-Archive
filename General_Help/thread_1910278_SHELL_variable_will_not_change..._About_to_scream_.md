---
title: "SHELL variable will not change... About to scream here."
date: 2012-01-16
forum: General Help
---

### Post by StrikerMan780 on 2012-01-16
I'm about to bash my goddamn head into a bloody red paste at this point... Something screwed up my Terminal, and the shell keeps on defaulting to /bin/sh, even though I had set it to /bin/bash in my etc/passwd file.  

When I launch gnome-terminal, I am stuck with only having a # as my prompt, no longer showing my username or current path. Also, arrow keys no longer show history, it just causes retarded ^A ^E ^[MIDDLEFINGER](j/k) things to show up. 

I'm at my wit's end on trying to solve this. Hell, earlier even my PATH variable was screwed up. Something installed must have messed it up, but I don't recall what.  

This is on a VPS, running as root, and has VNC and the default ubuntu desktop. Running on Ubuntu Server 10.04LTS. It is running webmin and has a few cron jobs, used to make sure VNC Launches at boot, etc. Lastly, I have a few startup apps in the gnome desktop that run scripts via xterm.

EDIT: ****! Now the PATH is messed up again... so apt-get doesn't work, among other things... Can someone help, please?

---

### Post by Serpher on 2012-01-16
Try the following:

```
chsh /bin/bash
```

If problems continue to persist try:

```
cp /etc/skel/.bashrc ~
```

---

### Post by StrikerMan780 on 2012-01-17
Neither worked. Still /bin/sh even in the same session (checked by typing echo $SHELL after), and path is still broken after reboot. (echo $PATH only gives me "/usr/bin:/bin")

Something is completely overriding these it seems. I'm about to go absolutely insane at this point. How easily linux installs can get screwed up behind the scenes is partially why I borderline hate Linux. (Not user-friendly at all) The only good thing about it is that it's free/open source. Perhaps I should have just gone for a Windows VPS despite the price.

Of course, APT is broken due to this, not to mention a few other things. (NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.)

Here's the contents of my /etc/passwd file:

```

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
bind:x:101:105::/var/cache/bind:/bin/false
smmta:x:102:106:Mail Transfer Agent,,,:/var/lib/sendmail:/bin/false
smmsp:x:103:107:Mail Submission Program,,,:/var/lib/sendmail:/bin/false
fetchmail:x:104:65534::/var/lib/fetchmail:/bin/false
sshd:x:105:65534::/var/run/sshd:/usr/sbin/nologin
klog:x:106:110::/home/klog:/bin/false
syslog:x:107:111::/home/syslog:/bin/false
postfix:x:108:112::/var/spool/postfix:/bin/false
dovecot:x:109:114:Dovecot mail server,,,:/usr/lib/dovecot:/bin/false
mysql:x:110:115:MySQL Server,,,:/var/lib/mysql:/bin/false
postgres:x:111:116:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
messagebus:x:112:118::/var/run/dbus:/bin/false
usbmux:x:113:46:usbmux daemon,,,:/home/usbmux:/bin/false
avahi:x:114:119:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
festival:x:115:29::/home/festival:/bin/false
speech-dispatcher:x:116:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
pulse:x:117:121:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:118:123:RealtimeKit,,,:/proc:/bin/false
gdm:x:119:124:Gnome Display Manager:/var/lib/gdm:/bin/false
hplip:x:120:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:121:127:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
couchdb:x:122:128:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
haldaemon:x:123:129:Hardware abstraction layer,,,:/var/run/hald:/bin/false
kernoops:x:124:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
saned:x:125:131::/home/saned:/bin/false

```My /etc/environment file:
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```FYI, removing and/or altering ~/.bashrc does nothing for me.

Neither does "sudo dpkg-reconfigure bash". How useless.

---

### Post by StrikerMan780 on 2012-01-17
My apt history.log file:

```

Start-Date: 2012-01-16  03:34:35
Install: eroute-tomcat7 (7.0.12)
End-Date: 2012-01-16  03:34:38

Start-Date: 2012-01-16  03:39:06
Install: postgresql-client-8.4 (8.4.9-0ubuntu0.10.04), postgresql (8.4.9-0ubuntu0.10.04), postgresql-client-common (106ubuntu1), postgresql-common (106ubuntu1), postgresql-8.4 (8.4.9-0ubuntu0.10.04)
End-Date: 2012-01-16  03:39:26

Start-Date: 2012-01-16  04:17:53
Install: policykit-1-gnome (0.96-2ubuntu2), gnome-keyring (2.92.92.is.2.30.3-0ubuntu1.1), libplist1 (1.1-1ubuntu1), aspell-en (6.0-0-5.1ubuntu3), libxcb-aux0 (0.3.6-1build1), libgtk2.0-common (2.20.1-0ubuntu2.1), libatk1.0-0 (1.30.0-0ubuntu2.1), libts-0.0-0 (1.0-7build1), libcdio10 (0.81-4), hdparm (9.15-1ubuntu9), libxfixes3 (4.0.4-1), shared-mime-info (0.71-1ubuntu2), libenchant1c2a (1.6.0-0ubuntu1), notification-daemon (0.4.0-2ubuntu2), libatasmart4 (0.17+git20100219-1git2), libpolkit-gobject-1-0 (0.96-2ubuntu0.1), libarchive1 (2.8.0-2ubuntu0.1), libntfs10 (2.0.0-1ubuntu4), libxcb-render-util0 (0.3.6-1build1), python-support (1.0.4ubuntu1), libgphoto2-port0 (2.4.8-0ubuntu2), liblcms1 (1.18.dfsg-1ubuntu2.10.04.1), libgstreamer0.10-0 (0.10.28-1), libtelepathy-glib0 (0.10.1-1ubuntu2), aspell (0.60.6-3ubuntu1), usbmuxd (1.0.2-1ubuntu2), libxcb-event1 (0.3.6-1build1), libindicator0 (0.3.8-0ubuntu1), obex-data-server (0.4.5-1), indicator-application (0.0.19-0ubuntu4), libgnome-keyring0 (2.30.1-0ubuntu1), libpixman-1-0 (0.16.4-1ubuntu2), libdbusmenu-glib1 (0.2.9-0ubuntu3.1), udisks (1.0.1-1ubuntu1), libdbus-glib-1-2 (0.84-1ubuntu0.2), libproxy0 (0.3.1-1ubuntu1), hunspell-en-us (20070829-4ubuntu1), libpam-gnome-keyring (2.92.92.is.2.30.3-0ubuntu1.1), gconf2 (2.28.1-0ubuntu1), dosfstools (3.0.7-1), libwnck-common (2.30.0-0ubuntu1), libeggdbus-1-0 (0.6-1), libusb-1.0-0 (1.0.6-1), libnotify1 (0.4.5-1ubuntu4), libcairo2 (1.8.10-2ubuntu1), libgvfscommon0 (1.6.1-0ubuntu1build1), policykit-1 (0.96-2ubuntu0.1), libpango1.0-common (1.28.0-0ubuntu2.2), libparted0debian1 (2.2-5ubuntu5.2), libxcb-render0 (1.5-2), libsoup2.4-1 (2.30.2-0ubuntu0.2), libgphoto2-2 (2.4.8-0ubuntu2), hicolor-icon-theme (0.11-1), libsmbclient (3.4.7~dfsg-1ubuntu3.8), libfuse2 (2.8.1-1.1ubuntu3.1), liblzma1 (4.999.9beta+20091116-1), libck-connector0 (0.4.1-3ubuntu2), libdatrie1 (0.2.2-3), libwnck22 (2.30.0-0ubuntu1), libsexy2 (0.1.11-2build2), libxcb-atom1 (0.3.6-1build1), libxfont1 (1.4.1-1ubuntu0.1), libgconf2-4 (2.28.1-0ubuntu1), libffi5 (3.0.9-1), libdirectfb-1.2-0 (1.2.8-5ubuntu2), libxres1 (1.0.4-1), dbus (1.2.16-2ubuntu4.3), libgp11-0 (2.92.92.is.2.30.3-0ubuntu1.1), powermgmt-base (1.31), libstartup-notification0 (0.10-1build1), libgcr0 (2.92.92.is.2.30.3-0ubuntu1.1), libcdio-cdda0 (0.81-4), libhunspell-1.2-0 (1.2.8-6ubuntu1), libpango1.0-0 (1.28.0-0ubuntu2.2), libgdu0 (2.30.1-1), libgtk2.0-bin (2.20.1-0ubuntu2.1), libxft2 (2.1.14-1ubuntu1), libdbusmenu-gtk1 (0.2.9-0ubuntu3.1), libxcomposite1 (0.4.1-1), libice6 (1.0.6-1), libunique-1.0-0 (1.1.6-1ubuntu2), libthai0 (0.1.13-1build1), vino (2.28.2-0ubuntu2.1), python-dbus (0.83.0-1ubuntu3), libidl0 (0.8.13-1), libimobiledevice0 (0.9.7-1ubuntu1.2), libgudev-1.0-0 (151-12.3), libglade2-0 (2.6.4-1build1), libbluetooth3 (4.60-0ubuntu8), libatk1.0-data (1.30.0-0ubuntu2.1), libjson-glib-1.0-0 (0.7.6-0ubuntu2), libxrender1 (0.9.5-1), libmagickcore2 (6.5.7.8-1ubuntu1.1), libsoup-gnome2.4-1 (2.30.2-0ubuntu0.2), libgs8 (8.71.dfsg.1-0ubuntu5.4), gconf2-common (2.28.1-0ubuntu1), libappindicator0 (0.0.19-0ubuntu4), libtiff4 (3.9.2-2ubuntu0.7), libfontenc1 (1.0.5-1), psfontmgr (0.11.10-4ubuntu1), libjasper1 (1.900.1-7ubuntu0.10.04.1), ntfsprogs (2.0.0-1ubuntu4), libusbmuxd1 (1.0.2-1ubuntu2), xfonts-utils (7.5+2), libcdio-paranoia0 (0.81-4), libmagickwand2 (6.5.7.8-1ubuntu1.1), libpam-ck-connector (0.4.1-3ubuntu2), libthai-data (0.1.13-1build1), libxtst6 (1.1.0-2), liborbit2 (2.14.18-0.1), libcupsimage2 (1.4.3-1ubuntu1.5), tsconf (1.0-7build1), ghostscript (8.71.dfsg.1-0ubuntu5.4), libpolkit-backend-1-0 (0.96-2ubuntu0.1), x11-common (7.5+5ubuntu1), libsysfs2 (2.1.0-6), libsgutils2-2 (1.28-2), libsm6 (1.1.1-1), libavahi-glib1 (0.6.25-1ubuntu6.2), libxdamage1 (1.1.2-1), gvfs (1.6.1-0ubuntu1build1), gvfs-backends (1.6.1-0ubuntu1build1), fuse-utils (2.8.1-1.1ubuntu3.1), libexif12 (0.6.19-1), dbus-x11 (1.2.16-2ubuntu4.3), libxi6 (1.3-3), libxcursor1 (1.1.10-1), xfonts-encodings (1.0.3-1), libxt6 (1.0.7-1), libxinerama1 (1.1-2), libxext6 (1.1.1-2), libxrandr2 (1.3.0-3), ntfs-3g (2010.3.6-1ubuntu1), x-ttcidfont-conf (32), libaspell15 (0.60.6-3ubuntu1), libgtk2.0-0 (2.20.1-0ubuntu2.1), libpolkit-agent-1-0 (0.96-2ubuntu0.1), gsfonts (8.11+urwcyr1.0.7~pre44-4), libopenobex1 (1.5-2build1), python-gobject (2.21.1-0ubuntu3), libntfs-3g75 (2010.3.6-1ubuntu1), consolekit (0.4.1-3ubuntu2)
Upgrade: mount (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2)
End-Date: 2012-01-16  04:20:33

Start-Date: 2012-01-16  04:28:26
Install: x11-apps (7.5+1ubuntu2), x11-utils (7.5+3), xbase-clients (7.5+5ubuntu1), x11-xfs-utils (7.4+1build2), libxxf86vm1 (1.1.0-2), xterm (256-1ubuntu1), x11-xserver-utils (7.5+1ubuntu2.1), xauth (1.0.4-1), libxmuu1 (1.0.5-1), xbitmaps (1.1.0-1), libxxf86dga1 (1.1.1-2), libxaw7 (1.0.7-1), xfonts-base (1.0.1), vnc4server (4.1.1+xorg4.3.0-37ubuntu2), libxmu6 (1.0.5-1), xinit (1.2.0-1), x11-session-utils (7.5+1), libfs6 (1.0.2-1build1), libgl1-mesa-dri (7.7.1-1ubuntu3), libgl1-mesa-glx (7.7.1-1ubuntu3), x11-xkb-utils (7.5+1), libxv1 (1.0.5-1), libxkbfile1 (1.0.6-1)
End-Date: 2012-01-16  04:28:56

Start-Date: 2012-01-16  04:41:09
Upgrade: libkrb5-3 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.10), libpam0g (1.1.1-2ubuntu5, 1.1.1-2ubuntu5.4), bzip2 (1.0.5-4ubuntu0.1, 1.0.5-4ubuntu0.2), libc-bin (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.8), libkrb5support0 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.10), bind9 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), apache2-utils (2.2.14-5ubuntu8.4, 2.2.14-5ubuntu8.7), base-files (5.0.0ubuntu20.10.04.2, 5.0.0ubuntu20.10.04.4), bind9-host (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libblkid1 (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), dhcp3-client (3.1.3-2ubuntu3, 3.1.3-2ubuntu3.3), libpam-modules (1.1.1-2ubuntu5, 1.1.1-2ubuntu5.4), libplymouth2 (0.8.2-2ubuntu2.1, 0.8.2-2ubuntu2.2), postfix (2.7.0-1, 2.7.0-1ubuntu0.2), bind9utils (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libbz2-1.0 (1.0.5-4ubuntu0.1, 1.0.5-4ubuntu0.2), libavahi-common-data (0.6.25-1ubuntu6.1, 0.6.25-1ubuntu6.2), libdbus-1-3 (1.2.16-2ubuntu4, 1.2.16-2ubuntu4.3), util-linux (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), perl (5.10.1-8ubuntu2, 5.10.1-8ubuntu2.1), libpam-runtime (1.1.1-2ubuntu5, 1.1.1-2ubuntu5.4), mysql-client-core-5.1 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.10), apache2.2-bin (2.2.14-5ubuntu8.4, 2.2.14-5ubuntu8.7), smbfs (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.8), logrotate (3.7.8-4ubuntu2, 3.7.8-4ubuntu2.2), libdns64 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libapr1 (1.3.8-1build1, 1.3.8-1ubuntu0.3), perl-base (5.10.1-8ubuntu2, 5.10.1-8ubuntu2.1), mysql-client-5.1 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.10), mysql-common (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.10), eroute-java6 (1.6.16, 1.6.24), dhcp3-common (3.1.3-2ubuntu3, 3.1.3-2ubuntu3.3), login (4.1.4.2-1ubuntu2, 4.1.4.2-1ubuntu2.2), apache2-mpm-prefork (2.2.14-5ubuntu8.4, 2.2.14-5ubuntu8.7), php5-gd (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.11), libisccc60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libk5crypto3 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.10), apt-utils (0.7.25.3ubuntu9.3, 0.7.25.3ubuntu9.9), apache2 (2.2.14-5ubuntu8.4, 2.2.14-5ubuntu8.7), openssh-client (5.3p1-3ubuntu4, 5.3p1-3ubuntu7), xkb-data (1.8-1ubuntu8, 1.8-1ubuntu8.1~10.04.1), uuid-runtime (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), udev (151-12.2, 151-12.3), passwd (4.1.4.2-1ubuntu2, 4.1.4.2-1ubuntu2.2), apt (0.7.25.3ubuntu9.3, 0.7.25.3ubuntu9.9), samba-common-bin (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.8), apache2.2-common (2.2.14-5ubuntu8.4, 2.2.14-5ubuntu8.7), liblwres60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libcups2 (1.4.3-1ubuntu1.3, 1.4.3-1ubuntu1.5), libt1-5 (5.1.2-3build1, 5.1.2-3ubuntu0.10.04.1), ifupdown (0.6.8ubuntu29.1, 0.6.8ubuntu29.2), bsdutils (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), sudo (1.7.2p1-1ubuntu5.2, 1.7.2p1-1ubuntu5.3), update-inetd (4.35, 4.35ubuntu0.1), ca-certificates (20090814, 20090814ubuntu0.10.04.1), dpkg (1.15.5.6ubuntu4.4, 1.15.5.6ubuntu4.5), rsync (3.0.7-1ubuntu1, 3.0.7-1ubuntu1.1), libxml2 (2.7.6.dfsg-1ubuntu1.1, 2.7.6.dfsg-1ubuntu1.2), libbind9-60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libwbclient0 (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.8), ldap-utils (2.4.21-0ubuntu5.3, 2.4.21-0ubuntu5.6), perl-modules (5.10.1-8ubuntu2, 5.10.1-8ubuntu2.1), libpng12-0 (1.2.42-1ubuntu2.1, 1.2.42-1ubuntu2.2), libperl5.10 (5.10.1-8ubuntu2, 5.10.1-8ubuntu2.1), libudev0 (151-12.2, 151-12.3), sysvinit-utils (2.87dsf-4ubuntu17, 2.87dsf-4ubuntu17.4), libmysqlclient16 (5.1.41-3ubuntu12.7, 5.1.41-3ubuntu12.10), libldap-2.4-2 (2.4.21-0ubuntu5.3, 2.4.21-0ubuntu5.6), libfreetype6 (2.3.11-1ubuntu2.4, 2.3.11-1ubuntu2.5), libisccfg60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libuuid1 (2.17.2-0ubuntu1, 2.17.2-0ubuntu1.10.04.2), libavahi-client3 (0.6.25-1ubuntu6.1, 0.6.25-1ubuntu6.2), tzdata (2010o-0ubuntu0.10.04, 2011n-0ubuntu0.10.04), apache2-doc (2.2.14-5ubuntu8.4, 2.2.14-5ubuntu8.7), libssl0.9.8 (0.9.8k-7ubuntu8.5, 0.9.8k-7ubuntu8.6), ntpdate (4.2.4p8+dfsg-1ubuntu2, 4.2.4p8+dfsg-1ubuntu2.1), libpq5 (8.4.5-0ubuntu10.04, 8.4.9-0ubuntu0.10.04), openssl (0.9.8k-7ubuntu8.5, 0.9.8k-7ubuntu8.6), samba-common (3.4.7~dfsg-1ubuntu3.2, 3.4.7~dfsg-1ubuntu3.8), php5-mysql (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.11), libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.3, 1.8.1+dfsg-2ubuntu0.10), sysvutils (2.87dsf-4ubuntu17, 2.87dsf-4ubuntu17.4), upstart (0.6.5-7, 0.6.5-8), sysv-rc (2.87dsf-4ubuntu17, 2.87dsf-4ubuntu17.4), libisc60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.4), libc6 (2.11.1-0ubuntu7.5, 2.11.1-0ubuntu7.8), libapache2-mod-php5 (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.11), libavahi-common3 (0.6.25-1ubuntu6.1, 0.6.25-1ubuntu6.2), binutils (2.20.1-3ubuntu7, 2.20.1-3ubuntu7.1), openssh-server (5.3p1-3ubuntu4, 5.3p1-3ubuntu7), portmap (6.0.0-1ubuntu2, 6.0.0-1ubuntu2.1), initscripts (2.87dsf-4ubuntu17, 2.87dsf-4ubuntu17.4), php5-common (5.3.2-1ubuntu4.5, 5.3.2-1ubuntu4.11), dovecot-common (1.2.9-1ubuntu6.1, 1.2.9-1ubuntu6.5), plymouth (0.8.2-2ubuntu2.1, 0.8.2-2ubuntu2.2), dselect (1.15.5.6ubuntu4.4, 1.15.5.6ubuntu4.5)
End-Date: 2012-01-16  05:46:25

Start-Date: 2012-01-16  05:49:39
Install: libswscale0 (0.5.1-1ubuntu1.3), libtwolame0 (0.3.12-1), libavutil49 (0.5.1-1ubuntu1.3), gstreamer0.10-plugins-ugly (0.10.14-1), iso-codes (3.12.1-1), libglu1-mesa (7.7.1-1ubuntu3), libspeex1 (1.2~rc1-1ubuntu1), libpostproc51 (0.5.1-1ubuntu1.3), libvorbisenc2 (1.2.3-3ubuntu1), libavformat52 (0.5.1-1ubuntu1.3), libschroedinger-1.0-0 (1.0.9.is.1.0.8-0ubuntu1), gstreamer0.10-ffmpeg (0.10.10-1), libtheora0 (1.1.1+dfsg.1-3), libcdparanoia0 (3.10.2+debian-9), libasound2 (1.0.22-0ubuntu7), libswfdec-0.8-0 (0.8.4-1build1), libgsm1 (1.0.13-3), libdvdnav4 (4.1.3-6), libdvdread4 (4.1.3-8ubuntu1), libsidplay1 (1.36.59-5), swfdec-mozilla (0.8.2-1ubuntu2), libavcodec52 (0.5.1-1ubuntu1.3), libmad0 (0.15.1b-4ubuntu1), libid3tag0 (0.15.1b-10build2), liboil0.3 (0.3.16-1ubuntu2), libopencore-amrnb0 (0.1.2-1), libvisual-0.4-0 (0.4.0-2.1+ubuntu2), libvorbis0a (1.2.3-3ubuntu1), gstreamer0.10-plugins-base (0.10.28-1), libgstreamer-plugins-base0.10-0 (0.10.28-1), libopencore-amrwb0 (0.1.2-1), libmpeg2-4 (0.4.1-3), libvisual-0.4-plugins (0.4.0.dfsg.1-2ubuntu5), libogg0 (1.1.4~dfsg-2), liba52-0.7.4 (0.7.4-13ubuntu1)
End-Date: 2012-01-16  05:50:24

Start-Date: 2012-01-16  06:25:33
Install: xserver-xorg (7.5+5ubuntu1), python-crypto (2.0.1+dfsg1-4ubuntu2), libpci3 (3.0.0-4ubuntu17), gstreamer0.10-alsa (0.10.28-1), evolution-common (2.28.3-0ubuntu10.3), libsdl1.2debian (1.2.14-4ubuntu1.1), xserver-xorg-video-rendition (4.2.3-1), desktop-base (5.0.5), libgnomekbd4 (2.30.2-0ubuntu0.1), libpurple0 (2.6.6-1ubuntu4.4), libsdl1.2debian-alsa (1.2.14-4ubuntu1.1), liblaunchpad-integration1 (0.1.35), libical0 (0.44-3), libglib-perl (1.222-1), evolution-webcal (2.28.0-1), ekiga (3.2.6-1ubuntu1), espeak (1.43.03-0ubuntu1), python-opengl (3.0.0-0ubuntu1), libpt2.6.5-plugins (2.6.5-1ubuntu1), python-gst0.10 (0.10.18-1), libcanberra-gtk-module (0.22-1ubuntu2), xsltproc (1.1.26-1ubuntu1), libgnomevfs2-0 (2.24.2-1ubuntu2), gcalctool (5.30.0.is.5.28.2-0ubuntu3), gnome-desktop-environment (2.28+1ubuntu3), xserver-xorg-input-evdev (2.3.2-5ubuntu1), gstreamer0.10-x (0.10.28-1), libpango-perl (1.221-2), libgail18 (2.20.1-0ubuntu2.1), telepathy-salut (0.3.11-1), python-beagle (0.3.9-1build1), libpth20 (2.0.7-14), python-gnome2 (2.28.0-1ubuntu1), gnome-nettool (2.30.0-0ubuntu1), gnome-media (2.30.0-0ubuntu1), libv4l-0 (0.6.4-1ubuntu1), xserver-xorg-video-s3virge (1.10.4-1), metacity (2.30.1-0ubuntu1.1), epiphany-browser (2.30.2-1ubuntu1.1), gnome-desktop-data (2.30.2-0ubuntu1), libgtk-vnc-1.0-0 (0.3.10-2ubuntu2.1), nautilus (2.30.1-0ubuntu1.2), aisleriot (2.30.0-0ubuntu6), libgnome2-0 (2.30.0-0ubuntu1), gtali (2.30.0-0ubuntu6), python-notify (0.1.1-2build3), libgail-gnome-module (1.20.1-2), gamin (0.1.10-1ubuntu3), libgtop2-common (2.26.1-0ubuntu2), libportaudio2 (19+svn20090620-0ubuntu2), xulrunner-1.9.2 (1.9.2.24+build2+nobinonly-0ubuntu0.10.04.1), xserver-xorg-video-all (7.5+5ubuntu1), glchess (2.30.0-0ubuntu6), pkg-config (0.22-1build2), xserver-xorg-video-apm (1.2.2-1), libcaca0 (0.99.beta16-3), xserver-xorg-video-ark (0.7.2-1), libiec61883-0 (1.2.0-0.1build1), genisoimage (1.1.10-1ubuntu1), xserver-xorg-video-ati (6.13.0-1ubuntu5), libdjvulibre21 (3.5.22-1ubuntu4.1), gnome-settings-daemon (2.30.1-0ubuntu1.1), libicu42 (4.2.1-3), libgnome-mag2 (0.16.1-0ubuntu1), libbrasero-media0 (2.30.2-0ubuntu1.1), brasero-common (2.30.2-0ubuntu1.1), libvorbisfile3 (1.2.3-3ubuntu1), xserver-xorg-video-tdfx (1.4.3-1), libgnomeui-common (2.24.3-1), gucharmap (2.30.0-0ubuntu1), python-evince (2.30.0-0ubuntu1.1), python-gnomecanvas (2.28.0-1ubuntu1), zenity (2.30.0-0ubuntu1), libseed0 (2.28.1-1), avahi-daemon (0.6.25-1ubuntu6.2), libdiscid0 (0.2.2-1), gnome-games (2.30.0-0ubuntu6), libgail-common (2.20.1-0ubuntu2.1), xserver-xorg-video-trident (1.3.3-1), xscreensaver-gl (5.10-3ubuntu4), cheese (2.30.1-0ubuntu2), liburi-perl (1.52-1), upower (0.9.1-1ubuntu1), quadrapassel (2.30.0-0ubuntu6), pulseaudio (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), gnome-bluetooth (2.30.0-0ubuntu3), evolution (2.28.3-0ubuntu10.3), dnsutils (9.7.0.dfsg.P1-1ubuntu0.4), libspectre1 (0.2.3-2), libsilc-1.1-2 (1.1.10-2build1), xserver-xorg-video-fbdev (0.4.1-1ubuntu1), xserver-xorg-input-wacom (0.10.5-0ubuntu4), gnobots2 (2.30.0-0ubuntu6), libgnome-media0 (2.30.0-0ubuntu1), libart-2.0-2 (2.3.20-2build1), app-install-data (0.10.04.7), libbeagle1 (0.3.9-1build1), gnome-power-manager (2.30.0-0ubuntu1.1), libexchange-storage1.2-3 (2.28.3.1-0ubuntu5), gnome-mahjongg (2.30.0-0ubuntu6), totem-plugins (2.30.2-0ubuntu1), epiphany-browser-data (2.30.2-1ubuntu1.1), gnome-screensaver (2.30.0-0ubuntu2.1), gnome-mag (0.16.1-0ubuntu1), xserver-xorg-video-v4l (0.2.0-4), libgstfarsight0.10-0 (0.0.17-2ubuntu2), libpst4 (0.6.41-0ubuntu4), libjack0 (0.118+svn3796-1ubuntu2), gnome-themes-selected (2.30.0-0ubuntu1), alacarte (0.13.1-0ubuntu1), xserver-xorg-video-mga (1.4.11.dfsg-2ubuntu1), python-libxml2 (2.7.6.dfsg-1ubuntu1.2), gedit (2.30.3-0ubuntu0.1), libnm-util1 (0.8-0ubuntu3.2), gnome-menus (2.30.0-0ubuntu4), liblircclient0 (0.8.6-0ubuntu4.2), python-gtksourceview2 (2.10.1-0ubuntu1), gtk2-engines-pixbuf (2.20.1-0ubuntu2.1), xserver-xorg-input-vmmouse (12.6.5-4ubuntu2), libtdb1 (1.2.0-1), libevview2 (2.30.3-0ubuntu1.2), scrollkeeper (0.8.1-4ubuntu1), dvd+rw-tools (7.1-6), libfont-afm-perl (1.20-1), docbook-xml (4.5-7), libmailtools-perl (2.05-1), libindicate-gtk2 (0.3.6-0ubuntu1), gir1.0-pango-1.0 (1.28.0-0ubuntu2.2), xserver-xorg-input-mouse (1.5.0-1), xserver-xorg-video-r128 (6.8.1-2ubuntu1), rarian-compat (0.8.1-4ubuntu1), libwebkit-1.0-2 (1.2.7-0ubuntu0.10.04.1), cheese-common (2.30.1-0ubuntu2), xserver-common (1.7.6-2ubuntu7.10), python-gtkglext1 (1.1.0-4), libx86-1 (1.1+ds1-6), libhtml-parser-perl (3.64-1), gnome-control-center (2.30.1-0ubuntu2), libsasl2-modules (2.1.23.dfsg1-5ubuntu1), libbonoboui2-common (2.24.3-0ubuntu1), libpisock9 (0.12.4-7ubuntu1), lightsoff (2.30.0-0ubuntu6), libcamel1.2-14 (2.28.3.1-0ubuntu5), libbonoboui2-0 (2.24.3-0ubuntu1), libupower-glib1 (0.9.1-1ubuntu1), xserver-xorg-video-openchrome (0.2.904+svn827-1), gnome-themes (2.30.0-0ubuntu1), libxslt1.1 (1.1.26-1ubuntu1), metacity-common (2.30.1-0ubuntu1.1), seahorse (2.30.0-0ubuntu2), xserver-xorg-video-vesa (2.3.0-1ubuntu1), libgnome2-perl (1.042-2build1), ubuntu-system-service (0.1.20.1), empathy (2.30.3-0ubuntu1.1), python-apt (0.7.94.2ubuntu6.4), libxml-twig-perl (3.32-3ubuntu1), libnspr4-0d (4.8.6-0ubuntu0.10.04.2), xserver-xorg-video-siliconmotion (1.7.3-1), libgtkhtml-editor0 (3.29.6.is.3.28.3-0ubuntu2), xserver-xorg-video-mach64 (6.8.2-2), esound-common (0.2.41-6ubuntu1), xserver-xorg-video-sis (0.10.2-2), libtotem-plparser17 (2.30.0git201000413-0ubuntu1), python-pyorbit (2.24.0-5ubuntu3), totem-common (2.30.2-0ubuntu1), python-telepathy (0.15.17-1), indicator-applet (0.3.7-0ubuntu1), python-gconf (2.28.0-1ubuntu1), gvfs-bin (1.6.1-0ubuntu1build1), vinagre (2.30.2-0ubuntu1), swfdec-gnome (2.28.0-1), libpulse-mainloop-glib0 (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), libedata-cal1.2-6 (2.28.3.1-0ubuntu5), libraw1394-11 (2.0.4-1ubuntu2), libdevkit-power-gobject1 (0.9.1-1ubuntu1), xserver-xorg-video-s3 (0.6.3-1), seed (2.28.1-1), xml-core (0.13), gnome-media-common (2.30.0-0ubuntu1), seahorse-plugins (2.30.0-0ubuntu2), nautilus-data (2.30.1-0ubuntu1.2), gir1.0-gtk-2.0 (2.20.1-0ubuntu2.1), bluez (4.60-0ubuntu8), libgnome-menu2 (2.30.0-0ubuntu4), gstreamer0.10-plugins-good (0.10.21-1ubuntu3), xserver-xorg-video-nv (2.1.15-1ubuntu3), gnibbles (2.30.0-0ubuntu6), libgadu3 (1.9.0~rc2-1), gnome-terminal (2.30.2-0ubuntu1), xserver-xorg-core (1.7.6-2ubuntu7.10), libwavpack1 (4.60.1-1), libxml-parser-perl (2.36-1.1build3), gnome-user-share (2.30.0-0ubuntu2), gir1.0-gstreamer-0.10 (0.10.28-1), nautilus-sendto-empathy (2.30.3-0ubuntu1.1), libtelepathy-farsight0 (0.0.13-1), system-tools-backends (2.9.4-0ubuntu1.1), festlex-cmu (1.4.0-6), xserver-xorg-video-tseng (1.2.3-1), libgweather1 (2.30.0-0ubuntu1.1), libpciaccess0 (0.11.0-1), dasher (4.10.1-2), libgnome-bluetooth7 (2.30.0-0ubuntu3), libxxf86misc1 (1.0.2-1), libgamin0 (0.1.10-1ubuntu3), gconf-defaults-service (2.28.1-0ubuntu1), libpanel-applet2-0 (2.30.2-0ubuntu0.2), guile-1.8-libs (1.8.7+1-3ubuntu1), libloudmouth1-0 (1.4.3-5), libnss-mdns (0.10-3ubuntu4), libpolkit-gtk-1-0 (0.96-2ubuntu2), libgnomekbd-common (2.30.2-0ubuntu0.1), gedit-common (2.30.3-0ubuntu0.1), gnome-utils (2.30.0-0ubuntu1.1), vbetool (1.1-2), libcairomm-1.0-1 (1.8.4-0ubuntu1), libido-0.1-0 (0.1.6-0ubuntu1), python-gnomedesktop (2.30.0-0ubuntu1.1), libopal3.6.6 (3.6.6~dfsg-4ubuntu1), xserver-xorg-video-savage (2.3.1-1ubuntu1), python-openssl (0.10-1), libgnome-pilot2 (2.0.17-0ubuntu5), libgssdp-1.0-2 (0.7.1-1), libcryptui0 (2.30.0-0ubuntu2), libbrlapi0.5 (4.1-2ubuntu6), libgdu-gtk0 (2.30.1-1), gnome-games-common (2.30.0-0ubuntu6), libatspi1.0-0 (1.30.1-0ubuntu1), libglibmm-2.4-1c2a (2.24.2-0ubuntu1), indicator-messages (0.3.6-0ubuntu2), gnome-orca (2.30.2-0ubuntu1), libnet-dbus-perl (0.33.6-1build3), python-pyatspi (1.30.1-0ubuntu1), libgnome2-common (2.30.0-0ubuntu1), rtkit (0.6-0ubuntu1), gnome-about (2.30.2-0ubuntu1), telepathy-haze (0.3.4-1), libexempi3 (2.1.1-1build2), gtk2-engines (2.20.0-0ubuntu1), libgnomeprint2.2-data (2.18.6-1build2), swell-foop (2.30.0-0ubuntu6), libgtksourceview2.0-common (2.10.4-0ubuntu1), libkpathsea5 (2009-5ubuntu0.2), xserver-xorg-input-all (7.5+5ubuntu1), python-speechd (0.6.8~unofficial~rc2-0ubuntu3), libhal1 (0.5.14-0ubuntu6), libtag1-vanilla (1.6.3-0ubuntu1), eog (2.30.0-0ubuntu1), gdm (2.30.2.is.2.30.0-0ubuntu5.2), libavc1394-0 (0.5.3-1build4), libgtksourceview2.0-0 (2.10.4-0ubuntu1), libsigc++-2.0-0c2a (2.2.4.2-1), capplets-data (2.30.1-0ubuntu2), libpangomm-1.4-1 (2.26.2-0ubuntu1), gnotski (2.30.0-0ubuntu6), libgnome2-vfs-perl (1.081-1build1), libavahi-gobject0 (0.6.25-1ubuntu6.2), python-farsight (0.0.17-2ubuntu2), gnome-disk-utility (2.30.1-1), libesd0 (0.2.41-6ubuntu1), libgnomecanvas2-0 (2.30.1-0ubuntu1), liblouis0 (1.7.0-2), python-gnomeprint (2.30.0-0ubuntu1.1), python-glade2 (2.17.0-0ubuntu2), gnome-backgrounds (2.30.0-1), dasher-data (4.10.1-2), libegroupwise1.2-13 (2.28.3.1-0ubuntu5), python-brlapi (4.1-2ubuntu6), gok (2.30.0-0ubuntu1), obexd-client (0.22-0ubuntu2), python-xdg (0.18-1ubuntu2), espeak-data (1.43.03-0ubuntu1), launchpad-integration (0.1.35), kbd (1.15-1ubuntu3), libnm-glib2 (0.8-0ubuntu3.2), libvte9 (0.23.5-0ubuntu1.1), libgsf-1-common (1.14.16-1ubuntu1), libgnomeui-0 (2.24.3-1), gnome-doc-utils (0.20.0-0ubuntu2), libclutter-1.0-0 (1.2.4-0ubuntu1), libgtk2-perl (1.221-4ubuntu2), gnome-session-bin (2.30.0-0ubuntu1), python-metacity (2.30.0-0ubuntu1.1), libgweather-common (2.30.0-0ubuntu1.1), libecal1.2-7 (2.28.3.1-0ubuntu5), festlex-poslex (1.4.0-5), xserver-xorg-video-nouveau (0.0.15+git20100219+9b4118d-0ubuntu5), at-spi (1.30.1-0ubuntu1), gstreamer0.10-pulseaudio (0.10.21-1ubuntu3), libpoppler5 (0.12.4-0ubuntu5.2), xserver-xorg-video-vmware (10.16.9-1), librarian0 (0.8.1-4ubuntu1), libgmime-2.4-2 (2.4.14-1+nmu1), libaa1 (1.4p5-38build1), pulseaudio-module-x11 (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), bogofilter-bdb (1.2.1-0ubuntu1.1), gir1.0-clutter-1.0 (1.2.4-0ubuntu1), libgirepository1.0-0 (0.6.8-1), wodim (1.1.10-1ubuntu1), python-louis (1.7.0-2), libgdata1.2-1 (2.28.3.1-0ubuntu5), libedataserver1.2-11 (2.28.3.1-0ubuntu5), libhal-storage1 (0.5.14-0ubuntu6), mousetweaks (2.30.0-0ubuntu1), gnome-system-monitor (2.28.0-1ubuntu2), libgtkmm-2.4-1c2a (2.20.3-0ubuntu1), libcanberra-gtk0 (0.22-1ubuntu2), gir1.0-atk-1.0 (1.30.0-0ubuntu2.1), libsamplerate0 (0.1.7-3), libbonobo2-0 (2.24.3-0ubuntu1), evince (2.30.3-0ubuntu1.2), bogofilter (1.2.1-0ubuntu1.1), festvox-kallpc16k (1.4.0-5), libevdocument2 (2.30.3-0ubuntu1.2), iagno (2.30.0-0ubuntu6), python-rsvg (2.30.0-0ubuntu1.1), libgdata-google1.2-1 (2.28.3.1-0ubuntu5), glines (2.30.0-0ubuntu6), pm-utils (1.3.0-1ubuntu3), telepathy-mission-control-5 (5.3.2-3), libspeechd2 (0.6.8~unofficial~rc2-0ubuntu3), libglib2.0-data (2.24.1-0ubuntu1), pulseaudio-utils (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), gnome-user-guide (2.30.0+git20100403ubuntu3), libflac8 (1.2.1-2build2), python-gnomeapplet (2.30.0-0ubuntu1.1), libclutter-gtk-0.10-0 (0.10.4-0ubuntu1), gnome-sudoku (2.30.0-0ubuntu6), libebook1.2-9 (2.28.3.1-0ubuntu5), gnome-js-common (0.1.1-1), evolution-plugins (2.28.3-0ubuntu10.3), libespeak1 (1.43.03-0ubuntu1), libaudiofile0 (0.2.6-8ubuntu1), libgnomecanvas2-common (2.30.1-0ubuntu1), libshout3 (2.2.2-5ubuntu1), telepathy-gabble (0.8.12-0ubuntu1.1), sgml-base (1.26), libdv4 (1.0.0-2ubuntu2), libtimedate-perl (1.1900-1), python-mediaprofiles (2.30.0-0ubuntu1.1), libedataserverui1.2-8 (2.28.3.1-0ubuntu5), libgnome-window-settings1 (2.30.1-0ubuntu2), python-launchpad-integration (0.1.35), libedata-book1.2-2 (2.28.3.1-0ubuntu5), evolution-data-server (2.28.3.1-0ubuntu5), python-gnomekeyring (2.30.0-0ubuntu1.1), libgdata6 (0.5.2-0ubuntu1), libxss1 (1.2.0-2), libgnomevfs2-extra (2.24.2-1ubuntu2), liblpint-bonobo0 (0.1.35), libgnome-speech7 (0.4.25-1ubuntu1), gstreamer0.10-nice (0.0.10-2build1), libgtop2-7 (2.26.1-0ubuntu2), libtie-ixhash-perl (1.21-2), gir1.0-gconf-2.0 (0.6.5-5ubuntu2), xserver-xorg-video-i128 (1.3.3-1), libgtkhtml-editor-common (3.29.6.is.3.28.3-0ubuntu2), xserver-xorg-video-neomagic (1.2.4-2), yelp (2.30.0-0ubuntu2), python-bugbuddy (2.30.0-0ubuntu1.1), xserver-xorg-video-chips (1.2.2-1), libxml-xpath-perl (1.13-7), xserver-xorg-video-voodoo (1.2.3-1), libpt2.6.5 (2.6.5-1ubuntu1), console-setup (1.34ubuntu15), libcanberra0 (0.22-1ubuntu2), python-totem-plparser (2.30.0-0ubuntu1.1), gksu (2.0.2-2ubuntu2), libdaemon0 (0.14-2), gnome-icon-theme (2.28.0-1ubuntu1), libasound2-plugins (1.0.22-0ubuntu6), libxvmc1 (1.0.5-1ubuntu1), libhtml-format-perl (2.04-2), zip (3.0-2), libgupnp-1.0-3 (0.13.2-1ubuntu1), python-gdbm (2.6.5-0ubuntu2), gnome-mime-data (2.18.0-1), gnome-core (2.28+1ubuntu3), gnotravex (2.30.0-0ubuntu6), screen-resolution-extra (0.13), libcheese-gtk18 (2.30.1-0ubuntu2), libpurple-bin (2.6.6-1ubuntu4.4), gnome-netstatus-applet (2.28.0-1ubuntu1), gnect (2.30.0-0ubuntu6), dmz-cursor-theme (0.4.1), python-evolution (2.30.0-0ubuntu1.1), libtag1c2a (1.6.3-0ubuntu1), librsvg2-2 (2.26.3-0ubuntu1.1), libxklavier16 (5.0-0ubuntu1), xserver-xorg-video-geode (2.11.11-1~lucid1), libbonobo2-common (2.24.3-0ubuntu1), gnome-terminal-data (2.30.2-0ubuntu1), liboobs-1-4 (2.30.0-0ubuntu1), libmeanwhile1 (1.0.2-3build2), libgucharmap7 (2.30.0-0ubuntu1), gnome-applets (2.30.0-0ubuntu2), libgksu2-0 (2.0.13~pre1-1ubuntu4.2), sgml-data (2.0.4), gir1.0-clutter-gtk-0.10 (0.10.4-0ubuntu1), indicator-sound (0.2.6-0ubuntu1), xserver-xorg-video-i740 (1.3.2-1), python-pkg-resources (0.6.10-4ubuntu1), libsilcclient-1.1-3 (1.1.10-2build1), festival (1.96~beta-10ubuntu1), libgpgme11 (1.2.0-1.2ubuntu1), python-gmenu (2.30.0-0ubuntu4), libindicate4 (0.3.6-0ubuntu1), libgdict-1.0-6 (2.30.0-0ubuntu1.1), gconf-editor (2.30.0-0ubuntu1), radeontool (1.6.1-0ubuntu1), libzephyr4 (3.0-1), gnome-system-tools (2.30.0-0ubuntu3), python-wnck (2.30.0-0ubuntu1.1), libpulse0 (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), libhtml-tree-perl (3.23-1), brasero (2.30.2-0ubuntu1.1), telepathy-butterfly (0.5.11-0ubuntu1), libebackend1.2-0 (2.28.3.1-0ubuntu5), speech-dispatcher (0.6.8~unofficial~rc2-0ubuntu3), libxml2-utils (2.7.6.dfsg-1ubuntu1.2), libpulse-browse0 (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), gnome-panel (2.30.2-0ubuntu0.2), gnome-accessibility (2.28+1ubuntu3), gir1.0-freedesktop (0.6.8-1), libcairo-perl (1.061-1build1), libwww-perl (5.834-1ubuntu0.1), libgnome-desktop-2-17 (2.30.2-0ubuntu1), hamster-applet (2.30.2-0ubuntu1), libgsl0ldbl (1.13+dfsg-1), python-papyon (0.4.8-0ubuntu2.1), python-xkit (0.4.2.2), esound-clients (0.2.41-6ubuntu1), intel-gpu-tools (1.0.2+git20100324-0ubuntu1), gir1.0-glib-2.0 (0.6.8-1), libnice0 (0.0.10-2build1), totem (2.30.2-0ubuntu1), bogofilter-common (1.2.1-0ubuntu1.1), gnome-accessibility-themes (2.30.0-0ubuntu1), deskbar-applet (2.30.0-0ubuntu1), liblouis-data (1.7.0-2), python-gnome2-desktop (2.30.0-0ubuntu1.1), libnautilus-extension1 (2.30.1-0ubuntu1.2), xserver-xorg-input-synaptics (1.2.2-1ubuntu4), evolution-data-server-common (2.28.3.1-0ubuntu5), gnome-applets-data (2.30.0-0ubuntu2), libgnomeprint2.2-0 (2.18.6-1build2), libdjvulibre-text (3.5.22-1ubuntu4.1), libhtml-tagset-perl (3.20-2), desktop-file-utils (0.16-0ubuntu2), libwebkit-1.0-common (1.2.7-0ubuntu0.10.04.1), libvte-common (0.23.5-0ubuntu1.1), libavahi-ui0 (0.6.25-1ubuntu6.2), xserver-xorg-video-sisusb (0.9.3-1), gnome-session (2.30.0-0ubuntu1), libgtkglext1 (1.2.0-1ubuntu1), libestools1.2 (1.2.96~beta-6), eject (2.1.5+deb1+cvs20081104-7), libnss3-1d (3.12.9+ckbi-1.82-0ubuntu0.10.04.3), gstreamer0.10-tools (0.10.28-1), libavahi-core6 (0.6.25-1ubuntu6.2), librsvg2-common (2.26.3-0ubuntu1.1), python-gtk2 (2.17.0-0ubuntu2), xscreensaver-data (5.10-3ubuntu4), freeglut3 (2.6.0-0ubuntu2), libsndfile1 (1.0.21-2ubuntu0.10.04.1), libgnomeprintui2.2-0 (2.18.4-1build1), libgupnp-igd-1.0-2 (0.1.3-4ubuntu1), xserver-xorg-video-radeon (6.13.0-1ubuntu5), totem-mozilla (2.30.2-0ubuntu1), python-cairo (1.8.8-1), python-httplib2 (0.6.0-1), pulseaudio-esound-compat (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), libgnome2-canvas-perl (1.002-2build1), libgtkhtml3.14-19 (3.29.6.is.3.28.3-0ubuntu2), libgsf-1-114 (1.14.16-1ubuntu1), libgnomeprintui2.2-common (2.18.4-1build1), file-roller (2.30.1.1-0ubuntu2), libspeexdsp1 (1.2~rc1-1ubuntu1), libneon27-gnutls (0.29.0-1), nautilus-sendto (2.28.4-0ubuntu1), python-rdflib (2.4.2-1), gnome-panel-data (2.30.2-0ubuntu0.2), libgdata-common (0.5.2-0ubuntu1), empathy-common (2.30.3-0ubuntu1.1), libpoppler-glib4 (0.12.4-0ubuntu5.2), xserver-xorg-video-cirrus (1.3.2-1ubuntu1), python-gtop (2.30.0-0ubuntu1.1), sound-juicer (2.28.1-2ubuntu0.1), xserver-xorg-video-intel (2.9.1-3ubuntu5), libgnomecups1.0-1 (0.2.3-3build2), libpisync1 (0.12.4-7ubuntu1), libgnomevfs2-common (2.24.2-1ubuntu2), libdotconf1.0 (1.0.13-3), libmetacity-private0 (2.30.1-0ubuntu1.1), libmusicbrainz3-6 (3.0.2-2), gnomine (2.30.0-0ubuntu6)
Remove: console-tools (0.2.3dbs-65.1ubuntu2), swfdec-mozilla (0.8.2-1ubuntu2)
End-Date: 2012-01-16  06:37:15

Start-Date: 2012-01-16  06:51:35
Install: swfdec-mozilla (0.8.2-1ubuntu2)
Remove: gnome-desktop-environment (2.28+1ubuntu3), epiphany-browser (2.30.2-1ubuntu1.1)
End-Date: 2012-01-16  06:51:39

Start-Date: 2012-01-16  07:20:07
Install: ubuntuone-client (1.2.2-0ubuntu2), libmono-addins-gui0.2-cil (0.4-6), mono-2.0-gac (2.4.4~svn151842-1ubuntu4), sane-utils (1.0.20-13ubuntu2), f-spot (0.6.1.5-2ubuntu7), branding-ubuntu (0.4-0ubuntu1), python-fstab (1.4-1), libstlport4.6ldbl (4.6.2-7), bluez-alsa (4.60-0ubuntu8), xorg-docs-core (1.5-1), python-lazr.restfulclient (0.9.11-1ubuntu1.1), netcat-traditional (1.10-38), python-twisted-names (10.0.0-1), apturl-common (0.4.1ubuntu4.1), libwpd8c2a (0.8.14-1build1), tomboy (1.2.2-0ubuntu1), python-twisted-core (10.0.0-2ubuntu2), python-pygoocanvas (0.14.1-0ubuntu1), computer-janitor-gtk (1.14.1-0ubuntu2), libmono2.0-cil (2.4.4~svn151842-1ubuntu4), python-desktopcouch-records (0.6.4-0ubuntu3.3), openoffice.org-gnome (3.2.0-7ubuntu4.2), libmtp8 (1.0.2-1ubuntu1), gwibber-service (2.30.3-0ubuntu2), pnm2ppa (1.13-0ubuntu1), libcolamd2.7.1 (3.4.0-1ubuntu3), lp-solve (5.5.0.13-7), libcompizconfig0 (0.8.4-0ubuntu2), openoffice.org-core (3.2.0-7ubuntu4.2), update-manager (0.134.11.1), openoffice.org-writer (3.2.0-7ubuntu4.2), libglitz-glx1 (0.5.6-1build1), libmono-data-tds2.0-cil (2.4.4~svn151842-1ubuntu4), python-pyinotify (0.8.9-1ubuntu2), libevent-1.4-2 (1.4.13-stable-1), libgnomepanel2.24-cil (2.26.0-2ubuntu1), python-pexpect (2.3-1build1), cdparanoia (3.10.2+debian-9), bluez-gstreamer (4.60-0ubuntu8), xfonts-scalable (1.0.1-1), openoffice.org-impress (3.2.0-7ubuntu4.2), desktopcouch (0.6.4-0ubuntu3.3), libglade2.0-cil (2.12.9-4), network-manager-pptp-gnome (0.8-0ubuntu3), gvfs-fuse (1.6.1-0ubuntu1build1), libmono-system-data2.0-cil (2.4.4~svn151842-1ubuntu4), ubuntu-docs (10.04.3), erlang-inets (13.b.3-dfsg-2ubuntu2.1), ttf-punjabi-fonts (0.5.8ubuntu2), python-mako (0.2.5-2ubuntu1.3), linux-headers-generic (2.6.32.37.43), libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1.1), python-debian (0.1.14ubuntu2), libcupscgi1 (1.4.3-1ubuntu1.5), mobile-broadband-provider-info (20100716-1ubuntu0.1), python-zope.interface (3.5.3-1ubuntu2), linux-headers-2.6.32-37 (2.6.32-37.81), libglib2.0-cil (2.12.9-4), m17n-contrib (1.1.10-1), libwmf0.2-7 (0.2.8.4-6.1ubuntu2), evolution-indicator (0.2.8-0ubuntu1), wireless-tools (30~pre9-3ubuntu4), librdf0 (1.0.10-1ubuntu1), apport-symptoms (0.9), openoffice.org-draw (3.2.0-7ubuntu4.2), network-manager-pptp (0.8-0ubuntu3), python-software-properties (0.75.10.1), smbclient (3.4.7~dfsg-1ubuntu3.8), libilmbase6 (1.0.1-3build2), python-protobuf (2.2.0a-0.1ubuntu1), ttf-thai-tlwg (0.4.13-4ubuntu0.1), libotf0 (0.9.10-1), pxljr (1.1-0ubuntu7), plymouth-x11 (0.8.2-2ubuntu2.2), doc-base (0.9.5), python-ubuntuone-storageprotocol (1.2.0-0ubuntu1), brltty-x11 (4.1-2ubuntu6), erlang-syntax-tools (13.b.3-dfsg-2ubuntu2.1), network-manager (0.8-0ubuntu3.2), gnome-session-canberra (0.22-1ubuntu2), gdebi (0.6.0ubuntu2), libgconf2.0-cil (2.24.1-6ubuntu1), evolution-exchange (2.28.3-0ubuntu1), python-twisted-web (10.0.0-1), ubufox (0.9~rc2-0ubuntu2.1), python-aptdaemon-gtk (0.11+bzr345-0ubuntu4.1), openoffice.org-gtk (3.2.0-7ubuntu4.2), update-manager-core (0.134.11.1), python-wadllib (1.1.4-1ubuntu1), gnome-codec-install (0.4.2ubuntu2), libsane (1.0.20-13ubuntu2), python-aptdaemon (0.11+bzr345-0ubuntu4.1), ttf-khmeros-core (5.0-3ubuntu1), libgraphite3 (2.3.1-0.2), python-pycurl (7.19.0-3), libhyphen0 (2.4-6ubuntu1), cli-common (0.7), libwpg-0.1-1 (0.1.3-1build1), rhythmbox (0.12.8-0ubuntu7), libibus1 (1.2.0.20091215-1ubuntu4), ibus-gtk (1.2.0.20091215-1ubuntu4), system-config-printer-gnome (1.2.0+20100408-0ubuntu5.2), manpages-dev (3.23-1), libdecoration0 (0.8.4-0ubuntu15.3), plymouth-label (0.8.2-2ubuntu2.2), xdg-user-dirs-gtk (0.8-1ubuntu1), bluez-cups (4.60-0ubuntu8), libsctp1 (1.0.11+dfsg-1), hpijs (3.10.2-2ubuntu2.2), protobuf-compiler (2.2.0a-0.1ubuntu1), erlang-mnesia (13.b.3-dfsg-2ubuntu2.1), ttf-takao-pgothic (003.02.01-2ubuntu1), cups-client (1.4.3-1ubuntu1.5), inputattach (20051019-9), brltty (4.1-2ubuntu6), libieee1284-3 (0.2.11-5ubuntu3), libcupsmime1 (1.4.3-1ubuntu1.5), libc-dev-bin (2.11.1-0ubuntu7.8), libgoocanvas-common (0.15-0ubuntu2), ubuntu-artwork (53.5), libart2.0-cil (2.24.1-6ubuntu1), libmono-system-runtime2.0-cil (2.4.4~svn151842-1ubuntu4), bc (1.06.95-2), hplip (3.10.2-2ubuntu2.2), libjs-jquery (1.3.3-2ubuntu1), bcmwl-modaliases (5.60.48.36+bdcom-0ubuntu3), dc (1.06.95-2), compizconfig-backend-gconf (0.8.4-0ubuntu2.1), update-notifier-common (0.99.3ubuntu0.1), gbrainy (1.41-1ubuntu1), libcouchdb-glib-1.0-2 (0.6.3-0ubuntu2), ubuntu-desktop (1.197), system-config-printer-udev (1.2.0+20100408-0ubuntu5.2), python-virtkey (0.50ubuntu3), libmagickcore2-extra (6.5.7.8-1ubuntu1.1), apt-xapian-index (0.25ubuntu2), libsqlite0 (2.8.17-6build2), libslp1 (1.2.1-7.6ubuntu0.1), ubuntu-sounds (0.12), ubuntu-wallpapers (0.31.3), gdebi-core (0.6.0ubuntu2), ghostscript-x (8.71.dfsg.1-0ubuntu5.4), light-themes (0.1.6.6), checkbox (0.9.2), python-simplejson (2.0.9-1build1), computer-janitor (1.14.1-0ubuntu2), update-notifier (0.99.3ubuntu0.1), libgnome2.24-cil (2.24.1-6ubuntu1), apport (1.13.3-0ubuntu2.1), libndesk-dbus1.0-cil (0.6.0-4), pm-utils-powersave-policy (0.3.1), linux-libc-dev (2.6.32-37.81), librasqal2 (0.9.17-1), libgpod4 (0.7.93-0ubuntu1), ubuntuone-client-gnome (1.2.2-0ubuntu2), libcurl3-gnutls (7.19.7-1ubuntu1.1), ttf-lao (0.0.20060226-6), cups-driver-gutenprint (5.2.5-0ubuntu1.1), dcraw (8.86-1build1), xdg-user-dirs (0.12-0ubuntu2), foomatic-db-engine (4.0.4-0ubuntu1), humanity-icon-theme (0.5.2.1), openoffice.org-style-human (3.2.0-7ubuntu4.2), libmono-cairo2.0-cil (2.4.4~svn151842-1ubuntu4), libfribidi0 (0.19.2-1), pptp-linux (1.7.2-4), gcc-4.4 (4.4.3-4ubuntu5), avahi-utils (0.6.25-1ubuntu6.2), m17n-db (1.5.5-1), toshset (1.75-2), network-manager-gnome (0.8-0ubuntu3), cpu-checker (0.1-0ubuntu2), python-gtkspell (2.25.3-4.1ubuntu4), libpcsclite1 (1.5.3-1ubuntu4.2), dnsmasq-base (2.52-1ubuntu0.1), couchdb-bin (0.10.0-1ubuntu2), jockey-common (0.5.8-0ubuntu8.1), python-serial (2.3-1), xfonts-75dpi (1.0.1), libgmime2.4-cil (2.4.14-1+nmu1), ttf-liberation (1.05.2.20091019-4), software-center (2.0.7), python-couchdb (0.6-1), python-pam (0.4.2-12.1ubuntu1), libflickrnet2.2-cil (2.2.0-3), compiz-plugins (0.8.4-0ubuntu15.3), liblaunchpad-integration1.0-cil (0.1.35), notify-osd (0.9.29-0ubuntu2), xinput (1.5.0-2ubuntu1), openoffice.org-style-galaxy (3.2.0-7ubuntu4.2), libmono-i18n-west2.0-cil (2.4.4~svn151842-1ubuntu4), rhythmbox-ubuntuone-music-store (0.0.9-0ubuntu1), acpid (1.0.10-5ubuntu2.5), simple-scan (1.0.3-0ubuntu1), libcupsppdc1 (1.4.3-1ubuntu1.5), python-lazr.uri (1.0.2-1), libmono-addins0.2-cil (0.4-6), libmusicbrainz4c2a (2.1.5-4), checkbox-gtk (0.9.2), firefox (3.6.24+build2+nobinonly-0ubuntu0.10.04.1), python-webkit (1.1.7-1), cups-common (1.4.3-1ubuntu1.5), uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4.2), python-avahi (0.6.25-1ubuntu6.2), libmono-posix2.0-cil (2.4.4~svn151842-1ubuntu4), rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu7), libhpmud0 (3.10.2-2ubuntu2.2), python-imaging (1.1.7-1ubuntu0.1), netcat (1.10-38), openoffice.org-math (3.2.0-7ubuntu4.2), libijs-0.35 (0.35-7build1), erlang-xmerl (13.b.3-dfsg-2ubuntu2.1), libmono-security2.0-cil (2.4.4~svn151842-1ubuntu4), gcc (4.4.3-1ubuntu1), gdb (7.1-1ubuntu2), libcurl3 (7.19.7-1ubuntu1.1), screensaver-default-images (0.2-1), hal (0.5.14-0ubuntu6), linux-headers-2.6.32-37-generic (2.6.32-37.81), libprotobuf5 (2.2.0a-0.1ubuntu1), libubuntuone-1.0-1 (0.3.1-0ubuntu1), libept0 (0.5.30), openoffice.org-common (3.2.0-7ubuntu4.2), python-uno (3.2.0-7ubuntu4.2), libgif4 (4.1.6-9), pciutils (3.0.0-4ubuntu17), libgtk2.0-cil (2.12.9-4), pulseaudio-module-bluetooth (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), telepathy-idle (0.1.6-1), mono-gac (2.4.4~svn151842-1ubuntu4), libgutenprint2 (5.2.5-0ubuntu1.1), usb-creator-gtk (0.2.22.3), python-vte (0.23.5-0ubuntu1.1), unattended-upgrades (0.55ubuntu6), usb-creator-common (0.2.22.3), language-selector (0.5.8), splix (2.0.0-2ubuntu3), alsa-utils (1.0.22-0ubuntu5), ttf-opensymbol (3.2.0-7ubuntu4.2), indicator-me (0.2.6-0ubuntu1), python-xapian (1.0.17-1ubuntu1), python-smbc (1.0.6-0ubuntu3), libopenexr6 (1.6.1-4.1), app-install-data-partner (12.10.04.5), avahi-autoipd (0.6.25-1ubuntu6.2), tsclient (0.150-3ubuntu1), rdesktop (1.6.0-2ubuntu3.1), aptdaemon (0.11+bzr345-0ubuntu4.1), system-config-printer-common (1.2.0+20100408-0ubuntu5.2), libmldbm-perl (2.01-3), python-gnupginterface (0.3.2-9.1), libxapian15 (1.0.18-1), libglitz1 (0.5.6-1build1), libuuid-perl (0.02-3build2), firefox-gnome-support (3.6.24+build2+nobinonly-0ubuntu0.10.04.1), libmono-sqlite2.0-cil (2.4.4~svn151842-1ubuntu4), cups (1.4.3-1ubuntu1.5), python-problem-report (1.13.3-0ubuntu2.1), openoffice.org-base-core (3.2.0-7ubuntu4.2), plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2.2), media-player-info (12-1~lucid1), notify-osd-icons (0.6), libcupsdriver1 (1.4.3-1ubuntu1.5), fglrx-modaliases (8.723.1-0ubuntu5), libmono-system-web2.0-cil (2.4.4~svn151842-1ubuntu4), libnunit2.4-cil (2.4.7+dfsg-5), apturl (0.4.1ubuntu4.1), im-switch (1.19), python-launchpadlib (1.6.0-0ubuntu1), ibus-m17n (1.2.0.20091217-1), ppp (2.4.5~git20081126t100229-0ubuntu3), xdg-utils (1.0.2-6.1ubuntu3.1), ubuntu-mono (0.0.18), python-appindicator (0.0.19-0ubuntu4), lksctp-tools (1.0.11+dfsg-1), libwps-0.1-1 (0.1.2-1build1), libmono-sharpzip2.84-cil (2.4.4~svn151842-1ubuntu4), indicator-applet-session (0.3.7-0ubuntu1), nvidia-current-modaliases (195.36.24-0ubuntu1~10.04.1), python-oauth (1.0a~svn1124-0ubuntu2), nautilus-share (0.7.2-12build1), nvidia-173-modaliases (173.14.22-0ubuntu11), libmono-corlib2.0-cil (2.4.4~svn151842-1ubuntu4), openprinting-ppds (20100216-0ubuntu3), pcmciautils (014-4ubuntu4), libgpod-common (0.7.93-0ubuntu1), ttf-kacst-one (3.0-1ubuntu2), rhythmbox-plugins (0.12.8-0ubuntu7), xfonts-100dpi (1.0.1), xcursor-themes (1.0.2-1), libiw30 (30~pre9-3ubuntu4), acpi-support (0.136.1), openoffice.org-emailmerge (3.2.0-7ubuntu4.2), cups-bsd (1.4.3-1ubuntu1.5), tcl8.4 (8.4.19-4), python-ubuntuone (0.3.1-0ubuntu1), foo2zjs (20100210-0ubuntu4), ure (1.6.0+OOo3.2.0-7ubuntu4.2), software-properties-gtk (0.75.10.1), erlang-crypto (13.b.3-dfsg-2ubuntu2.1), libm17n-0 (1.5.5-1), python-egenix-mxdatetime (3.1.3-2ubuntu1), mono-runtime (2.4.4~svn151842-1ubuntu4), wpasupplicant (0.6.9-3ubuntu3), synaptic (0.63.1ubuntu7), laptop-detect (0.13.7ubuntu2), usbutils (0.86-2ubuntu1), libfreezethaw-perl (0.45-1), smartdimmer (0.8b4-1ubuntu3), libdesktopcouch-glib-1.0-2 (0.6.3-0ubuntu2), python-cups (1.9.49-0ubuntu1), alsa-base (1.0.22.1+dfsg-0ubuntu3), ibus (1.2.0.20091215-1ubuntu4), libc6-dev (2.11.1-0ubuntu7.8), apparmor (2.5.1-0ubuntu0.10.04.3), ttf-indic-fonts-core (0.5.8ubuntu2), tk8.4 (8.4.19-4), policykit-desktop-privileges (0.1), python-configglue (0.2dev-0ubuntu2), libanthy0 (9100h-0ubuntu2), libwmf0.2-7-gtk (0.2.8.4-6.1ubuntu2), language-selector-common (0.5.8), nvidia-common (0.2.23), pulseaudio-module-gconf (0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14), ibus-table (1.2.0.20100111-1), python-egenix-mxtools (3.1.3-2ubuntu1), foomatic-filters (4.0.4-0ubuntu1.1), onboard (0.93.0-0ubuntu4), ttf-wqy-microhei (0.2.0-beta-1), gnome-themes-ubuntu (0.6.1), poppler-utils (0.12.4-0ubuntu5.2), gstreamer0.10-plugins-base-apps (0.10.28-1), jockey-gtk (0.5.8-0ubuntu8.1), pitivi (0.13.4-0ubuntu3), libcanberra-pulse (0.22-1ubuntu2), xorg (7.5+5ubuntu1), foomatic-db (20100216-0ubuntu3), libndesk-dbus-glib1.0-cil (0.4.1-3), gtk2-engines-murrine (0.90.3+git20100323-0ubuntu3), libraptor1 (1.4.21-1ubuntu1), indicator-session (0.2.8-0ubuntu2), imagemagick (6.5.7.8-1ubuntu1.1), erlang-ssl (13.b.3-dfsg-2ubuntu2.1), linux-sound-base (1.0.22.1+dfsg-0ubuntu3), adium-theme-ubuntu (0.1-0ubuntu1), libgnome-keyring1.0-cil (1.0.0-3), firefox-branding (3.6.24+build2+nobinonly-0ubuntu0.10.04.1), hal-info (20091130-1), libgtkspell0 (2.0.16-1), compiz (0.8.4-0ubuntu15.3), python-ubuntuone-client (1.2.2-0ubuntu2), xfonts-mathml (4ubuntu1), ttf-unfonts-core (1.0.1-7ubuntu1), python-desktopcouch (0.6.4-0ubuntu3.3), gwibber (2.30.3-0ubuntu2), python-apport (1.13.3-0ubuntu2.1), erlang-runtime-tools (13.b.3-dfsg-2ubuntu2.1), compiz-core (0.8.4-0ubuntu15.3), binfmt-support (1.2.18), openoffice.org-calc (3.2.0-7ubuntu4.2), python-cupshelpers (1.2.0+20100408-0ubuntu5.2), libxp6 (1.0.0.xsf1-2build1), compiz-fusion-plugins-main (0.8.4-0ubuntu3), libgnome-vfs2.0-cil (2.24.1-6ubuntu1), python-ibus (1.2.0.20091215-1ubuntu4), openoffice.org-help-en-us (3.2.0-7ubuntu1), libgraphviz4 (2.20.2-8ubuntu3), min12xxw (0.0.9-3ubuntu2), apport-gtk (1.13.3-0ubuntu2.1), transmission-common (1.93-0ubuntu0.10.04.1), mscompress (0.3-3build1), libprotoc5 (2.2.0a-0.1ubuntu1), gdm-guest-session (0.15), gstreamer0.10-gnonlin (0.10.15-1), nvidia-96-modaliases (96.43.17-0ubuntu1.1), python-twisted-bin (10.0.0-2ubuntu2), libgoocanvas3 (0.15-0ubuntu2), evolution-couchdb (0.4.5-0ubuntu1), dmidecode (2.9-1.2), modemmanager (0.3-0ubuntu2.2), kerneloops-daemon (0.12+git20090217-1ubuntu7), libmono-system2.0-cil (2.4.4~svn151842-1ubuntu4), example-content (41), libgdiplus (2.4.2-1ubuntu0.10.04.1), compiz-gnome (0.8.4-0ubuntu15.3), transmission-gtk (1.93-0ubuntu0.10.04.1), ssh-askpass-gnome (5.3p1-3ubuntu7), hplip-data (3.10.2-2ubuntu2.2), erlang-base (13.b.3-dfsg-2ubuntu2.1), lftp (4.0.2-1ubuntu0.1), erlang-public-key (13.b.3-dfsg-2ubuntu2.1), ghostscript-cups (8.71.dfsg.1-0ubuntu5.4), python-indicate (0.3.0-0ubuntu1)
Remove: libsdl1.2debian-alsa (1.2.14-4ubuntu1.1)
End-Date: 2012-01-16  07:31:26

Start-Date: 2012-01-16  07:42:53
Remove: desktop-base (5.0.5), ekiga (3.2.6-1ubuntu1), python-opengl (3.0.0-0ubuntu1), libpt2.6.5-plugins (2.6.5-1ubuntu1), python-beagle (0.3.9-1build1), gtali (2.30.0-0ubuntu6), glchess (2.30.0-0ubuntu6), libseed0 (2.28.1-1), libdiscid0 (0.2.2-1), gnome-games (2.30.0-0ubuntu6), cheese (2.30.1-0ubuntu2), gnobots2 (2.30.0-0ubuntu6), epiphany-browser-data (2.30.2-1ubuntu1.1), gir1.0-pango-1.0 (1.28.0-0ubuntu2.2), cheese-common (2.30.1-0ubuntu2), python-gtkglext1 (1.1.0-4), lightsoff (2.30.0-0ubuntu6), gnome-themes (2.30.0-0ubuntu1), swfdec-gnome (2.28.0-1), seed (2.28.1-1), seahorse-plugins (2.30.0-0ubuntu2), gir1.0-gtk-2.0 (2.20.1-0ubuntu2.1), gnibbles (2.30.0-0ubuntu6), gir1.0-gstreamer-0.10 (0.10.28-1), festlex-cmu (1.4.0-6), dasher (4.10.1-2), libopal3.6.6 (3.6.6~dfsg-4ubuntu1), swell-foop (2.30.0-0ubuntu6), gnotski (2.30.0-0ubuntu6), gnome-backgrounds (2.30.0-1), dasher-data (4.10.1-2), gok (2.30.0-0ubuntu1), festlex-poslex (1.4.0-5), gir1.0-clutter-1.0 (1.2.4-0ubuntu1), libgirepository1.0-0 (0.6.8-1), gir1.0-atk-1.0 (1.30.0-0ubuntu2.1), festvox-kallpc16k (1.4.0-5), iagno (2.30.0-0ubuntu6), glines (2.30.0-0ubuntu6), gnome-js-common (0.1.1-1), libgnome-speech7 (0.4.25-1ubuntu1), gir1.0-gconf-2.0 (0.6.5-5ubuntu2), libpt2.6.5 (2.6.5-1ubuntu1), gnome-core (2.28+1ubuntu3), gnotravex (2.30.0-0ubuntu6), libcheese-gtk18 (2.30.1-0ubuntu2), gnome-netstatus-applet (2.28.0-1ubuntu1), gnect (2.30.0-0ubuntu6), gir1.0-clutter-gtk-0.10 (0.10.4-0ubuntu1), festival (1.96~beta-10ubuntu1), gnome-accessibility (2.28+1ubuntu3), gir1.0-freedesktop (0.6.8-1), hamster-applet (2.30.2-0ubuntu1), gir1.0-glib-2.0 (0.6.8-1), deskbar-applet (2.30.0-0ubuntu1), libgtkglext1 (1.2.0-1ubuntu1), libestools1.2 (1.2.96~beta-6), freeglut3 (2.6.0-0ubuntu2), sound-juicer (2.28.1-2ubuntu0.1), libmusicbrainz3-6 (3.0.2-2)
End-Date: 2012-01-16  07:44:24

Start-Date: 2012-01-16  08:03:49
Remove: vnc4server (4.1.1+xorg4.3.0-37ubuntu2)
End-Date: 2012-01-16  08:03:51

Start-Date: 2012-01-16  08:04:45
Remove: ubuntu-desktop (1.197)
End-Date: 2012-01-16  08:04:46

Start-Date: 2012-01-16  08:04:57
Remove: python-crypto (2.0.1+dfsg1-4ubuntu2), libsdl1.2debian (1.2.14-4ubuntu1.1), libpurple0 (2.6.6-1ubuntu4.4), espeak (1.43.03-0ubuntu1), gcalctool (5.30.0.is.5.28.2-0ubuntu3), telepathy-salut (0.3.11-1), libpth20 (2.0.7-14), gnome-nettool (2.30.0-0ubuntu1), libgtk-vnc-1.0-0 (0.3.10-2ubuntu2.1), aisleriot (2.30.0-0ubuntu6), libgail-gnome-module (1.20.1-2), libportaudio2 (19+svn20090620-0ubuntu2), libgnome-mag2 (0.16.1-0ubuntu1), gucharmap (2.30.0-0ubuntu1), libgail-common (2.20.1-0ubuntu2.1), xscreensaver-gl (5.10-3ubuntu4), liburi-perl (1.52-1), quadrapassel (2.30.0-0ubuntu6), gnome-bluetooth (2.30.0-0ubuntu3), dnsutils (9.7.0.dfsg.P1-1ubuntu0.4), libspectre1 (0.2.3-2), libsilc-1.1-2 (1.1.10-2build1), libbeagle1 (0.3.9-1build1), gnome-power-manager (2.30.0-0ubuntu1.1), gnome-mahjongg (2.30.0-0ubuntu6), totem-plugins (2.30.2-0ubuntu1), gnome-screensaver (2.30.0-0ubuntu2.1), gnome-mag (0.16.1-0ubuntu1), libgstfarsight0.10-0 (0.0.17-2ubuntu2), gnome-themes-selected (2.30.0-0ubuntu1), gedit (2.30.3-0ubuntu0.1), python-gtksourceview2 (2.10.1-0ubuntu1), dvd+rw-tools (7.1-6), libfont-afm-perl (1.20-1), libmailtools-perl (2.05-1), libhtml-parser-perl (3.64-1), seahorse (2.30.0-0ubuntu2), empathy (2.30.3-0ubuntu1.1), libxml-twig-perl (3.32-3ubuntu1), totem-common (2.30.2-0ubuntu1), python-telepathy (0.15.17-1), vinagre (2.30.2-0ubuntu1), bluez (4.60-0ubuntu8), libgadu3 (1.9.0~rc2-1), libxml-parser-perl (2.36-1.1build3), gnome-user-share (2.30.0-0ubuntu2), nautilus-sendto-empathy (2.30.3-0ubuntu1.1), libtelepathy-farsight0 (0.0.13-1), system-tools-backends (2.9.4-0ubuntu1.1), gconf-defaults-service (2.28.1-0ubuntu1), guile-1.8-libs (1.8.7+1-3ubuntu1), libloudmouth1-0 (1.4.3-5), libpolkit-gtk-1-0 (0.96-2ubuntu2), gedit-common (2.30.3-0ubuntu0.1), gnome-utils (2.30.0-0ubuntu1.1), libgssdp-1.0-2 (0.7.1-1), libcryptui0 (2.30.0-0ubuntu2), libgdu-gtk0 (2.30.1-1), gnome-games-common (2.30.0-0ubuntu6), gnome-orca (2.30.2-0ubuntu1), libnet-dbus-perl (0.33.6-1build3), python-pyatspi (1.30.1-0ubuntu1), telepathy-haze (0.3.4-1), libgtksourceview2.0-common (2.10.4-0ubuntu1), libkpathsea5 (2009-5ubuntu0.2), python-speechd (0.6.8~unofficial~rc2-0ubuntu3), eog (2.30.0-0ubuntu1), libgtksourceview2.0-0 (2.10.4-0ubuntu1), libavahi-gobject0 (0.6.25-1ubuntu6.2), python-farsight (0.0.17-2ubuntu2), gnome-disk-utility (2.30.1-1), liblouis0 (1.7.0-2), python-brlapi (4.1-2ubuntu6), obexd-client (0.22-0ubuntu2), espeak-data (1.43.03-0ubuntu1), libclutter-1.0-0 (1.2.4-0ubuntu1), at-spi (1.30.1-0ubuntu1), wodim (1.1.10-1ubuntu1), python-louis (1.7.0-2), evince (2.30.3-0ubuntu1.2), telepathy-mission-control-5 (5.3.2-3), libspeechd2 (0.6.8~unofficial~rc2-0ubuntu3), libclutter-gtk-0.10-0 (0.10.4-0ubuntu1), gnome-sudoku (2.30.0-0ubuntu6), libespeak1 (1.43.03-0ubuntu1), telepathy-gabble (0.8.12-0ubuntu1.1), libtimedate-perl (1.1900-1), libgdata6 (0.5.2-0ubuntu1), gstreamer0.10-nice (0.0.10-2build1), libtie-ixhash-perl (1.21-2), libxml-xpath-perl (1.13-7), libhtml-format-perl (2.04-2), zip (3.0-2), libgupnp-1.0-3 (0.13.2-1ubuntu1), libpurple-bin (2.6.6-1ubuntu4.4), dmz-cursor-theme (0.4.1), liboobs-1-4 (2.30.0-0ubuntu1), libmeanwhile1 (1.0.2-3build2), libsilcclient-1.1-3 (1.1.10-2build1), libgpgme11 (1.2.0-1.2ubuntu1), libgdict-1.0-6 (2.30.0-0ubuntu1.1), gconf-editor (2.30.0-0ubuntu1), libzephyr4 (3.0-1), gnome-system-tools (2.30.0-0ubuntu3), libhtml-tree-perl (3.23-1), brasero (2.30.2-0ubuntu1.1), telepathy-butterfly (0.5.11-0ubuntu1), speech-dispatcher (0.6.8~unofficial~rc2-0ubuntu3), libwww-perl (5.834-1ubuntu0.1), python-papyon (0.4.8-0ubuntu2.1), libnice0 (0.0.10-2build1), totem (2.30.2-0ubuntu1), gnome-accessibility-themes (2.30.0-0ubuntu1), liblouis-data (1.7.0-2), libhtml-tagset-perl (3.20-2), libavahi-ui0 (0.6.25-1ubuntu6.2), libgupnp-igd-1.0-2 (0.1.3-4ubuntu1), totem-mozilla (2.30.2-0ubuntu1), file-roller (2.30.1.1-0ubuntu2), nautilus-sendto (2.28.4-0ubuntu1), python-rdflib (2.4.2-1), libgdata-common (0.5.2-0ubuntu1), empathy-common (2.30.3-0ubuntu1.1), libpoppler-glib4 (0.12.4-0ubuntu5.2), libdotconf1.0 (1.0.13-3), gnomine (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:06:44

Start-Date: 2012-01-16  08:08:07
Install: python-crypto (2.0.1+dfsg1-4ubuntu2), libsdl1.2debian (1.2.14-4ubuntu1.1), libpurple0 (2.6.6-1ubuntu4.4), espeak (1.43.03-0ubuntu1), gcalctool (5.30.0.is.5.28.2-0ubuntu3), telepathy-salut (0.3.11-1), libpth20 (2.0.7-14), gnome-nettool (2.30.0-0ubuntu1), libgtk-vnc-1.0-0 (0.3.10-2ubuntu2.1), aisleriot (2.30.0-0ubuntu6), libgail-gnome-module (1.20.1-2), libportaudio2 (19+svn20090620-0ubuntu2), libgnome-mag2 (0.16.1-0ubuntu1), gucharmap (2.30.0-0ubuntu1), libgail-common (2.20.1-0ubuntu2.1), xscreensaver-gl (5.10-3ubuntu4), liburi-perl (1.52-1), quadrapassel (2.30.0-0ubuntu6), gnome-bluetooth (2.30.0-0ubuntu3), dnsutils (9.7.0.dfsg.P1-1ubuntu0.4), libspectre1 (0.2.3-2), libsilc-1.1-2 (1.1.10-2build1), libbeagle1 (0.3.9-1build1), gnome-power-manager (2.30.0-0ubuntu1.1), gnome-mahjongg (2.30.0-0ubuntu6), totem-plugins (2.30.2-0ubuntu1), gnome-screensaver (2.30.0-0ubuntu2.1), gnome-mag (0.16.1-0ubuntu1), libgstfarsight0.10-0 (0.0.17-2ubuntu2), gnome-themes-selected (2.30.0-0ubuntu1), gedit (2.30.3-0ubuntu0.1), python-gtksourceview2 (2.10.1-0ubuntu1), dvd+rw-tools (7.1-6), libfont-afm-perl (1.20-1), libmailtools-perl (2.05-1), libhtml-parser-perl (3.64-1), ubuntu-desktop (1.197), seahorse (2.30.0-0ubuntu2), empathy (2.30.3-0ubuntu1.1), libxml-twig-perl (3.32-3ubuntu1), totem-common (2.30.2-0ubuntu1), python-telepathy (0.15.17-1), vinagre (2.30.2-0ubuntu1), bluez (4.60-0ubuntu8), libgadu3 (1.9.0~rc2-1), libxml-parser-perl (2.36-1.1build3), gnome-user-share (2.30.0-0ubuntu2), nautilus-sendto-empathy (2.30.3-0ubuntu1.1), libtelepathy-farsight0 (0.0.13-1), system-tools-backends (2.9.4-0ubuntu1.1), gconf-defaults-service (2.28.1-0ubuntu1), guile-1.8-libs (1.8.7+1-3ubuntu1), libloudmouth1-0 (1.4.3-5), libpolkit-gtk-1-0 (0.96-2ubuntu2), gedit-common (2.30.3-0ubuntu0.1), gnome-utils (2.30.0-0ubuntu1.1), libgssdp-1.0-2 (0.7.1-1), libcryptui0 (2.30.0-0ubuntu2), libgdu-gtk0 (2.30.1-1), gnome-games-common (2.30.0-0ubuntu6), gnome-orca (2.30.2-0ubuntu1), libnet-dbus-perl (0.33.6-1build3), python-pyatspi (1.30.1-0ubuntu1), telepathy-haze (0.3.4-1), libgtksourceview2.0-common (2.10.4-0ubuntu1), libkpathsea5 (2009-5ubuntu0.2), python-speechd (0.6.8~unofficial~rc2-0ubuntu3), eog (2.30.0-0ubuntu1), libgtksourceview2.0-0 (2.10.4-0ubuntu1), libavahi-gobject0 (0.6.25-1ubuntu6.2), python-farsight (0.0.17-2ubuntu2), gnome-disk-utility (2.30.1-1), liblouis0 (1.7.0-2), python-brlapi (4.1-2ubuntu6), obexd-client (0.22-0ubuntu2), espeak-data (1.43.03-0ubuntu1), libclutter-1.0-0 (1.2.4-0ubuntu1), at-spi (1.30.1-0ubuntu1), wodim (1.1.10-1ubuntu1), python-louis (1.7.0-2), evince (2.30.3-0ubuntu1.2), telepathy-mission-control-5 (5.3.2-3), libspeechd2 (0.6.8~unofficial~rc2-0ubuntu3), libclutter-gtk-0.10-0 (0.10.4-0ubuntu1), gnome-sudoku (2.30.0-0ubuntu6), libespeak1 (1.43.03-0ubuntu1), telepathy-gabble (0.8.12-0ubuntu1.1), libtimedate-perl (1.1900-1), libgdata6 (0.5.2-0ubuntu1), gstreamer0.10-nice (0.0.10-2build1), libtie-ixhash-perl (1.21-2), libxml-xpath-perl (1.13-7), libhtml-format-perl (2.04-2), zip (3.0-2), libgupnp-1.0-3 (0.13.2-1ubuntu1), libpurple-bin (2.6.6-1ubuntu4.4), dmz-cursor-theme (0.4.1), liboobs-1-4 (2.30.0-0ubuntu1), libmeanwhile1 (1.0.2-3build2), libsilcclient-1.1-3 (1.1.10-2build1), libgpgme11 (1.2.0-1.2ubuntu1), libgdict-1.0-6 (2.30.0-0ubuntu1.1), gconf-editor (2.30.0-0ubuntu1), libzephyr4 (3.0-1), gnome-system-tools (2.30.0-0ubuntu3), libhtml-tree-perl (3.23-1), brasero (2.30.2-0ubuntu1.1), telepathy-butterfly (0.5.11-0ubuntu1), speech-dispatcher (0.6.8~unofficial~rc2-0ubuntu3), libwww-perl (5.834-1ubuntu0.1), python-papyon (0.4.8-0ubuntu2.1), libnice0 (0.0.10-2build1), totem (2.30.2-0ubuntu1), gnome-accessibility-themes (2.30.0-0ubuntu1), liblouis-data (1.7.0-2), libhtml-tagset-perl (3.20-2), libavahi-ui0 (0.6.25-1ubuntu6.2), libgupnp-igd-1.0-2 (0.1.3-4ubuntu1), totem-mozilla (2.30.2-0ubuntu1), file-roller (2.30.1.1-0ubuntu2), nautilus-sendto (2.28.4-0ubuntu1), python-rdflib (2.4.2-1), libgdata-common (0.5.2-0ubuntu1), empathy-common (2.30.3-0ubuntu1.1), libpoppler-glib4 (0.12.4-0ubuntu5.2), libdotconf1.0 (1.0.13-3), gnomine (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:10:01

Start-Date: 2012-01-16  08:11:11
Install: vnc4server (4.1.1+xorg4.3.0-37ubuntu2)
End-Date: 2012-01-16  08:11:13

Start-Date: 2012-01-16  08:29:50
Install: launchpad-getkeys (0.3.2-1~webupd8~lucid)
End-Date: 2012-01-16  08:29:52

Start-Date: 2012-01-16  08:35:12
Install: libopenal1 (1.12.854-0ubuntu1~lucid1), ttf-umefont (411-1), wine1.3-gecko (1.4.0+1), wine1.3 (1.3.36-0ubuntu1~ppa1~lucid1), winetricks (0.0+20110629~ppa1), ttf-symbol-replacement-wine1.3 (1.3.36-0ubuntu1~ppa1~lucid1), icoutils (0.29.1-0ubuntu1~lucid), cabextract (1.2-3+lenny1build0.10.04.1), libmpg123-0 (1.12.1-0ubuntu1), winbind (3.4.7~dfsg-1ubuntu3.8), gnome-exe-thumbnailer (0.7-0ubuntu1~lucid1), ttf-droid (1.00~b112+dfsg+1-0ubuntu1)
End-Date: 2012-01-16  08:35:43

Start-Date: 2012-01-16  08:36:22
Install: furiusisomount (0.11.1.2-1), fuseiso9660 (0.2b-1build1), libiso9660-7 (0.81-4), fuseiso (20070708-1), libumlib0 (0.6-1)
End-Date: 2012-01-16  08:36:31

Start-Date: 2012-01-16  08:36:36
Remove: aisleriot (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:36:40

Start-Date: 2012-01-16  08:36:45
Remove: brasero (2.30.2-0ubuntu1.1)
End-Date: 2012-01-16  08:36:46

Start-Date: 2012-01-16  08:37:14
Remove: evolution-indicator (0.2.8-0ubuntu1), evolution-exchange (2.28.3-0ubuntu1), evolution (2.28.3-0ubuntu10.3), evolution-plugins (2.28.3-0ubuntu10.3), evolution-couchdb (0.4.5-0ubuntu1)
End-Date: 2012-01-16  08:37:26

Start-Date: 2012-01-16  08:38:08
Remove: f-spot (0.6.1.5-2ubuntu7)
End-Date: 2012-01-16  08:38:10

Start-Date: 2012-01-16  08:38:18
Remove: gnome-mahjongg (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:38:23

Start-Date: 2012-01-16  08:38:27
Remove: gnomine (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:38:32

Start-Date: 2012-01-16  08:38:37
Remove: totem-plugins (2.30.2-0ubuntu1), totem (2.30.2-0ubuntu1), totem-mozilla (2.30.2-0ubuntu1)
End-Date: 2012-01-16  08:38:39

Start-Date: 2012-01-16  08:38:50
Remove: quadrapassel (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:38:55

Start-Date: 2012-01-16  08:38:59
Remove: gnome-sudoku (2.30.0-0ubuntu6)
End-Date: 2012-01-16  08:39:01

Start-Date: 2012-01-16  08:39:26
Remove: gbrainy (1.41-1ubuntu1)
End-Date: 2012-01-16  08:39:28

Start-Date: 2012-01-16  08:39:51
Remove: openoffice.org-writer (3.2.0-7ubuntu4.2), openoffice.org-help-en-us (3.2.0-7ubuntu1)
End-Date: 2012-01-16  08:39:53

Start-Date: 2012-01-16  08:40:13
Remove: openoffice.org-impress (3.2.0-7ubuntu4.2), openoffice.org-draw (3.2.0-7ubuntu4.2)
End-Date: 2012-01-16  08:40:15

Start-Date: 2012-01-16  08:40:19
Remove: openoffice.org-math (3.2.0-7ubuntu4.2)
End-Date: 2012-01-16  08:40:21

Start-Date: 2012-01-16  08:40:36
Remove: openoffice.org-calc (3.2.0-7ubuntu4.2)
End-Date: 2012-01-16  08:40:38

Start-Date: 2012-01-16  08:44:46
Install: p7zip (9.04~dfsg.1-1)
End-Date: 2012-01-16  08:44:48

Start-Date: 2012-01-16  08:47:06
Install: unrar (3.9.3-1), rar (3.9.b2-1)
End-Date: 2012-01-16  08:47:10

Start-Date: 2012-01-16  08:52:10
Install: brasero (2.30.2-0ubuntu1.1)
End-Date: 2012-01-16  08:52:13

Start-Date: 2012-01-16  08:54:25
Install: gmountiso (0.4-0ubuntu3)
End-Date: 2012-01-16  08:54:29

Start-Date: 2012-01-16  08:54:34
Install: gisomount (1.0.1-0ubuntu2)
End-Date: 2012-01-16  08:54:39

Start-Date: 2012-01-16  08:54:45
Install: casper (1.236.3), lupin-casper (0.29.1), user-setup (1.28ubuntu7), localechooser-data (2.12ubuntu3)
End-Date: 2012-01-16  08:54:53

Start-Date: 2012-01-16  09:00:18
Install: pinentry-gtk2 (0.7.6-1), libxine1-x (1.1.17-1ubuntu3), libqt4-dbus (4.6.2-0ubuntu5.3), libxine1-misc-plugins (1.1.17-1ubuntu3), libxcb-xv0 (1.5-2), phonon (4.6.2-0ubuntu5.3), libxine1-bin (1.1.17-1ubuntu3), libqt4-xmlpatterns (4.6.2-0ubuntu5.3), libqt4-webkit (4.6.2-0ubuntu5.3), acetoneiso (2.2.1-1), libqtcore4 (4.6.2-0ubuntu5.3), libxcb-shape0 (1.5-2), libksba8 (1.0.7-2), gnupg-agent (2.0.14-1ubuntu1.2), libao2 (0.8.8-5ubuntu2), libphonon4 (4.6.2-0ubuntu5.3), libqt4-xml (4.6.2-0ubuntu5.3), cdrdao (1.2.2-18ubuntu4), libqt4-network (4.6.2-0ubuntu5.3), phonon-backend-xine (4.4.0-0ubuntu2), libqt4-designer (4.6.2-0ubuntu5.3), libqtgui4 (4.6.2-0ubuntu5.3), libmodplug0c2 (0.8.7-1ubuntu0.3), libqt4-script (4.6.2-0ubuntu5.3), libaudio2 (1.9.2-3), libxcb-shm0 (1.5-2), p7zip-full (9.04~dfsg.1-1), libmpcdec3 (1.2.2-2.1ubuntu1), gnupg2 (2.0.14-1ubuntu1.2), pinentry-qt4 (0.7.6-1), libmng1 (1.0.9-1ubuntu1), libxine1-console (1.1.17-1ubuntu3), libxine1 (1.1.17-1ubuntu3)
End-Date: 2012-01-16  09:00:53

Start-Date: 2012-01-16  09:00:58
Remove: gmountiso (0.4-0ubuntu3)
End-Date: 2012-01-16  09:00:59

Start-Date: 2012-01-16  09:01:04
Remove: gisomount (1.0.1-0ubuntu2)
End-Date: 2012-01-16  09:01:05

Start-Date: 2012-01-16  09:05:10
Remove: furiusisomount (0.11.1.2-1), fuseiso9660 (0.2b-1build1), libiso9660-7 (0.81-4), libumlib0 (0.6-1)
End-Date: 2012-01-16  09:05:13

Start-Date: 2012-01-16  13:31:10
Remove: evolution-common (2.28.3-0ubuntu10.3), libwpd8c2a (0.8.14-1build1), libmono2.0-cil (2.4.4~svn151842-1ubuntu4), libcolamd2.7.1 (3.4.0-1ubuntu3), lp-solve (5.5.0.13-7), libglitz-glx1 (0.5.6-1build1), libmono-data-tds2.0-cil (2.4.4~svn151842-1ubuntu4), libmono-system-data2.0-cil (2.4.4~svn151842-1ubuntu4), libexchange-storage1.2-3 (2.28.3.1-0ubuntu5), libwpg-0.1-1 (0.1.3-1build1), libpst4 (0.6.41-0ubuntu4), libmono-system-runtime2.0-cil (2.4.4~svn151842-1ubuntu4), libpisock9 (0.12.4-7ubuntu1), libcouchdb-glib-1.0-2 (0.6.3-0ubuntu2), libsqlite0 (2.8.17-6build2), libgtkhtml-editor0 (3.29.6.is.3.28.3-0ubuntu2), totem-common (2.30.2-0ubuntu1), gvfs-bin (1.6.1-0ubuntu1build1), dcraw (8.86-1build1), guile-1.8-libs (1.8.7+1-3ubuntu1), libflickrnet2.2-cil (2.2.0-3), libgnome-pilot2 (2.0.17-0ubuntu5), gnome-games-common (2.30.0-0ubuntu6), python-uno (3.2.0-7ubuntu4.2), libgif4 (4.1.6-9), libclutter-1.0-0 (1.2.4-0ubuntu1), libglitz1 (0.5.6-1build1), libmono-sqlite2.0-cil (2.4.4~svn151842-1ubuntu4), openoffice.org-base-core (3.2.0-7ubuntu4.2), libmono-system-web2.0-cil (2.4.4~svn151842-1ubuntu4), libnunit2.4-cil (2.4.7+dfsg-5), libclutter-gtk-0.10-0 (0.10.4-0ubuntu1), libwps-0.1-1 (0.1.2-1build1), libgdata6 (0.5.2-0ubuntu1), openoffice.org-emailmerge (3.2.0-7ubuntu4.2), liblpint-bonobo0 (0.1.35), libgtkhtml-editor-common (3.29.6.is.3.28.3-0ubuntu2), libdesktopcouch-glib-1.0-2 (0.6.3-0ubuntu2), libgnome-keyring1.0-cil (1.0.0-3), libgtkhtml3.14-19 (3.29.6.is.3.28.3-0ubuntu2), libgdiplus (2.4.2-1ubuntu0.10.04.1), python-rdflib (2.4.2-1), libgdata-common (0.5.2-0ubuntu1), libpisync1 (0.12.4-7ubuntu1)
End-Date: 2012-01-16  13:31:35

Start-Date: 2012-01-16  13:33:01
Upgrade: mono-2.0-gac (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), mobile-broadband-provider-info (20100716-1ubuntu0.1, 20111113-1ubuntu0.10.04), wine1.3 (1.3.36-0ubuntu1~ppa1~lucid1, 1.3.37-0ubuntu1~ppa1~lucid1), postgresql-client-8.4 (8.4.9-0ubuntu0.10.04, 8.4.10-0ubuntu0.10.04.1), libmono-cairo2.0-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), libmono-i18n-west2.0-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), libmono-posix2.0-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), libmono-security2.0-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), ttf-symbol-replacement-wine1.3 (1.3.36-0ubuntu1~ppa1~lucid1, 1.3.37-0ubuntu1~ppa1~lucid1), mono-gac (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), postgresql (8.4.9-0ubuntu0.10.04, 8.4.10-0ubuntu0.10.04.1), libmono-sharpzip2.84-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), libmono-corlib2.0-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), mono-runtime (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1), libpq5 (8.4.9-0ubuntu0.10.04, 8.4.10-0ubuntu0.10.04.1), postgresql-8.4 (8.4.9-0ubuntu0.10.04, 8.4.10-0ubuntu0.10.04.1), libmono-system2.0-cil (2.4.4~svn151842-1ubuntu4, 2.6.7-3ubuntu1~dhx1)

Start-Date: 2012-01-16  14:15:59
Install: menu (2.1.43ubuntu1), grub-pc (1.98-1ubuntu12), startupmanager (1.9.13-4ubuntu1), os-prober (1.38), grub-common (1.98-1ubuntu12)
End-Date: 2012-01-16  14:16:24

Start-Date: 2012-01-16  14:39:21
Install: libcurses-perl (1.28-1), sysv-rc-conf (0.99-6), libterm-readkey-perl (2.30-4build1), libcurses-ui-perl (0.9607-1)
End-Date: 2012-01-16  14:39:25

Start-Date: 2012-01-16  15:57:04
Install: update-java (0.5-2~webupd8)
End-Date: 2012-01-16  15:57:07

Start-Date: 2012-01-16  16:10:00
Install: filezilla (3.3.1-1ubuntu2), libwxgtk2.8-0 (2.8.10.1-0ubuntu1.2), libwxbase2.8-0 (2.8.10.1-0ubuntu1.2), filezilla-common (3.3.1-1ubuntu2)
End-Date: 2012-01-16  16:10:10

Start-Date: 2012-01-16  16:18:52
Remove: filezilla (3.3.1-1ubuntu2), libwxgtk2.8-0 (2.8.10.1-0ubuntu1.2), libwxbase2.8-0 (2.8.10.1-0ubuntu1.2), filezilla-common (3.3.1-1ubuntu2)
End-Date: 2012-01-16  16:18:56

Start-Date: 2012-01-16  16:19:18
Install: gftp-gtk (2.0.19-2ubuntu1), gftp-common (2.0.19-2ubuntu1)
End-Date: 2012-01-16  16:19:22

Start-Date: 2012-01-16  16:20:48
Remove: gftp-gtk (2.0.19-2ubuntu1), gftp-common (2.0.19-2ubuntu1)
End-Date: 2012-01-16  16:20:50

Start-Date: 2012-01-16  16:20:55
Install: filezilla (3.3.1-1ubuntu2), libwxgtk2.8-0 (2.8.10.1-0ubuntu1.2), libwxbase2.8-0 (2.8.10.1-0ubuntu1.2), filezilla-common (3.3.1-1ubuntu2)
End-Date: 2012-01-16  16:21:02

Start-Date: 2012-01-16  16:26:58
Install: compizconfig-settings-manager (0.8.2-0ubuntu1), python-compizconfig (0.8.2-0ubuntu1)
End-Date: 2012-01-16  16:27:08

Start-Date: 2012-01-16  16:27:28
Remove: gnome-bluetooth (2.30.0-0ubuntu3), gnome-user-share (2.30.0-0ubuntu2)
End-Date: 2012-01-16  16:27:37

Start-Date: 2012-01-16  16:28:04
Remove: empathy (2.30.3-0ubuntu1.1)
End-Date: 2012-01-16  16:28:09

Start-Date: 2012-01-16  16:28:20
Remove: gwibber (2.30.3-0ubuntu2)
End-Date: 2012-01-16  16:28:22

Start-Date: 2012-01-16  16:28:51
Remove: tomboy (1.2.2-0ubuntu1)
End-Date: 2012-01-16  16:28:57

Start-Date: 2012-01-16  16:29:50
Remove: simple-scan (1.0.3-0ubuntu1)
End-Date: 2012-01-16  16:29:54

Start-Date: 2012-01-17  05:14:40
Remove: ubuntu-desktop (1.197), gnome-terminal (2.30.2-0ubuntu1)
End-Date: 2012-01-17  05:14:43

Start-Date: 2012-01-17  05:15:03
Remove: libmono-addins-gui0.2-cil (0.4-6), python-crypto (2.0.1+dfsg1-4ubuntu2), mono-2.0-gac (2.6.7-3ubuntu1~dhx1), libpurple0 (2.6.6-1ubuntu4.4), evolution-webcal (2.28.0-1), python-desktopcouch-records (0.6.4-0ubuntu3.3), gwibber-service (2.30.3-0ubuntu2), telepathy-salut (0.3.11-1), libgnomepanel2.24-cil (2.26.0-2ubuntu1), desktopcouch (0.6.4-0ubuntu3.3), libglade2.0-cil (2.12.9-4), erlang-inets (13.b.3-dfsg-2ubuntu2.1), libglib2.0-cil (2.12.9-4), erlang-syntax-tools (13.b.3-dfsg-2ubuntu2.1), libgconf2.0-cil (2.24.1-6ubuntu1), libsilc-1.1-2 (1.1.10-2build1), python-pycurl (7.19.0-3), cli-common (0.7), libgstfarsight0.10-0 (0.0.17-2ubuntu2), libsctp1 (1.0.11+dfsg-1), erlang-mnesia (13.b.3-dfsg-2ubuntu2.1), libindicate-gtk2 (0.3.6-0ubuntu1), libart2.0-cil (2.24.1-6ubuntu1), python-telepathy (0.15.17-1), libgnome2.24-cil (2.24.1-6ubuntu1), libndesk-dbus1.0-cil (0.6.0-4), libgadu3 (1.9.0~rc2-1), libmono-cairo2.0-cil (2.6.7-3ubuntu1~dhx1), nautilus-sendto-empathy (2.30.3-0ubuntu1.1), libtelepathy-farsight0 (0.0.13-1), python-gtkspell (2.25.3-4.1ubuntu4), libloudmouth1-0 (1.4.3-5), couchdb-bin (0.10.0-1ubuntu2), libgmime2.4-cil (2.4.14-1+nmu1), python-couchdb (0.6-1), liblaunchpad-integration1.0-cil (0.1.35), libmono-i18n-west2.0-cil (2.6.7-3ubuntu1~dhx1), libgssdp-1.0-2 (0.7.1-1), libmono-addins0.2-cil (0.4-6), python-avahi (0.6.25-1ubuntu6.2), libmono-posix2.0-cil (2.6.7-3ubuntu1~dhx1), telepathy-haze (0.3.4-1), erlang-xmerl (13.b.3-dfsg-2ubuntu2.1), libmono-security2.0-cil (2.6.7-3ubuntu1~dhx1), libcurl3 (7.19.7-1ubuntu1.1), python-farsight (0.0.17-2ubuntu2), obexd-client (0.22-0ubuntu2), libgtk2.0-cil (2.12.9-4), mono-gac (2.6.7-3ubuntu1~dhx1), bogofilter-bdb (1.2.1-0ubuntu1.1), bogofilter (1.2.1-0ubuntu1.1), telepathy-mission-control-5 (5.3.2-3), telepathy-gabble (0.8.12-0ubuntu1.1), lksctp-tools (1.0.11+dfsg-1), libmono-sharpzip2.84-cil (2.6.7-3ubuntu1~dhx1), libmono-corlib2.0-cil (2.6.7-3ubuntu1~dhx1), gstreamer0.10-nice (0.0.10-2build1), erlang-crypto (13.b.3-dfsg-2ubuntu2.1), python-egenix-mxdatetime (3.1.3-2ubuntu1), mono-runtime (2.6.7-3ubuntu1~dhx1), libgupnp-1.0-3 (0.13.2-1ubuntu1), python-gdbm (2.6.5-0ubuntu2), libpurple-bin (2.6.6-1ubuntu4.4), python-egenix-mxtools (3.1.3-2ubuntu1), gnome-terminal-data (2.30.2-0ubuntu1), libmeanwhile1 (1.0.2-3build2), libsilcclient-1.1-3 (1.1.10-2build1), libndesk-dbus-glib1.0-cil (0.4.1-3), libzephyr4 (3.0-1), erlang-ssl (13.b.3-dfsg-2ubuntu2.1), telepathy-butterfly (0.5.11-0ubuntu1), libgtkspell0 (2.0.16-1), python-desktopcouch (0.6.4-0ubuntu3.3), libgsl0ldbl (1.13+dfsg-1), python-papyon (0.4.8-0ubuntu2.1), erlang-runtime-tools (13.b.3-dfsg-2ubuntu2.1), libnice0 (0.0.10-2build1), bogofilter-common (1.2.1-0ubuntu1.1), libgnome-vfs2.0-cil (2.24.1-6ubuntu1), libgupnp-igd-1.0-2 (0.1.3-4ubuntu1), libmono-system2.0-cil (2.6.7-3ubuntu1~dhx1), empathy-common (2.30.3-0ubuntu1.1), erlang-base (13.b.3-dfsg-2ubuntu2.1), erlang-public-key (13.b.3-dfsg-2ubuntu2.1), python-indicate (0.3.0-0ubuntu1)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2012-01-17  05:15:03

Start-Date: 2012-01-17  05:16:50
Purge: gnome-terminal-data (2.30.2-0ubuntu1)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2012-01-17  05:16:51

Start-Date: 2012-01-17  05:31:25
Purge: gnome-terminal-data (2.30.2-0ubuntu1)
End-Date: 2012-01-17  05:31:29

Start-Date: 2012-01-17  05:31:45
Install: gnome-terminal (2.30.2-0ubuntu1), gnome-terminal-data (2.30.2-0ubuntu1)
End-Date: 2012-01-17  05:31:53

Start-Date: 2012-01-17  05:45:22
Purge: gnome-terminal (2.30.2-0ubuntu1)
End-Date: 2012-01-17  05:45:24

Start-Date: 2012-01-17  05:45:40
Install: gnome-terminal (2.30.2-0ubuntu1)
End-Date: 2012-01-17  05:45:44

Start-Date: 2012-01-17  06:30:22
Upgrade: phpmyadmin (3.3.2-1, 3.3.2-1ubuntu1)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2012-01-17  06:30:23

Start-Date: 2012-01-17  10:48:51
Remove: menu (2.1.43ubuntu1), grub-pc (1.98-1ubuntu12), startupmanager (1.9.13-4ubuntu1), os-prober (1.38), grub-common (1.98-1ubuntu12)
End-Date: 2012-01-17  10:48:56

Start-Date: 2012-01-17  11:19:35
Remove: libgtk-vnc-1.0-0 (0.3.10-2ubuntu2.1), vinagre (2.30.2-0ubuntu1), libavahi-gobject0 (0.6.25-1ubuntu6.2)
End-Date: 2012-01-17  11:19:42

Start-Date: 2012-01-17  11:22:38
Install: libavahi-gobject0 (0.6.25-1ubuntu6.2)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2012-01-17  11:22:38

Start-Date: 2012-01-17  11:50:01
Install: libavahi-gobject0 (0.6.25-1ubuntu6.2)
End-Date: 2012-01-17  11:50:03

```

---

### Post by gsgleason on 2012-01-17
From man bash:

> When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists. After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in that order, and reads and executes commands from the first one that exists and is readable. The --noprofile option may be used when the shell is started to inhibit this behavior. When a login shell exits, bash reads and executes commands from the file ~/.bash_logout, if it exists.

When an interactive shell that is not a login shell is started, bash reads and executes commands from ~/.bashrc, if that file exists. This may be inhibited by using the --norc option. The --rcfile file option will force bash to read and execute commands from file instead of ~/.bashrc.

When bash is started non-interactively, to run a shell script, for example, it looks for the variable BASH_ENV in the environment, expands its value if it appears there, and uses the expanded value as the name of a file to read and execute. Bash behaves as if the following command were executed:

    if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi 
but the value of the PATH variable is not used to search for the file name. 

Try looking in those files for the culprit.  It will only use the first one it finds readable.  Also, check 'env|grep BASH_ENV' and 'ls -l /bin/bash' to make sure it's not a symlink to something else.

If you run 'bash --login' does it work?

---

### Post by StrikerMan780 on 2012-01-17
BASH itself runs fine, I can invoke it in my terminal, but, it isn't my default shell like it should be. CHSH doesn't work, among other things I've attempted.

I also inspected those files, but, nothing seems out of the usual.

---

### Post by gsgleason on 2012-01-17
Striker, how are you accessing the terminal in the first place? (ssh, etc)

[edit]

Nevermind. I see you're launching gnome-terminal.

I wonder if gnome terminal itself is doing something?  I know it has a lot of configuration options.

If, from the gnome-terminal, you run 'xterm -ls' does the resulting xterm seem okay?

---

### Post by StrikerMan780 on 2012-01-17
It works, but, I see this on the top: expr: syntax error

---

### Post by gsgleason on 2012-01-17
So one thing is generating an error and another is causing the gnome-terminal to run sh instead of bash.

In gnome terminal, if you edit the profile, look at the 'title and command' tab to see if it's running a custom command instead of your shell.

As far as xterm, what if you don't run it as a login shell?  just xterm with no args?

What to you mean 'at the top?'  The title bar?

---

### Post by StrikerMan780 on 2012-01-17
No, first line in the terminal.

Also, the title and command tab is all at the defaults. So no, it is not running any custom commands, as far as I am aware.

xterm without args launches with just a # sign, showing it is running sh, rather than BASH.

---

### Post by gsgleason on 2012-01-18
Unfortunately I'm out of ideas for you.  If this were mine, I think I'd be able to find the issue, though.  

If you want to give me ssh access, which I'm sure you don't, I'd try to help further.

---

### Post by QLee on 2012-01-18
One thing that you might ask him is how did he logon as root because root is not supposed to have a password.

Another thing that might be of interest is why there are no users shown in the password file, not even the first (sudo capable) user that should have been part of the install.

---

### Post by StrikerMan780 on 2012-01-19
The root account was assigned a pre-determined password when I purchased the VPS, this isn't an ubuntu desktop install. This is Ubuntu Server 10.04LTS with the Ubuntu Desktop installed after in order to have a GUI to use with VNC. Root was the only user at the start, and even then, things worked right at first, and I don't know what happened to change that.

If I use SSH, the terminal is fine, uses BASH as it should. Any other terminal program, such as GNOME Terminal, or xterm, do not run with normal BASH, but in SH(which is bash in a special compatibility mode to function like the old SH).

Also, my PATH environment variable sticks, just like the shell variable... not sure what is causing this.

---

### Post by StrikerMan780 on 2012-01-26
I've about given up on the terminal part... now I just want to know why my PATH variable will not stay the way it should be.

Also, this:

```

dpkg: warning: 'ldconfig' not found on PATH.
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: warning: 'update-rc.d' not found on PATH.
dpkg: 3 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: warning: 'ldconfig' not found on PATH.
dpkg: warning: 'start-stop-daemon' not found on PATH.
dpkg: warning: 'update-rc.d' not found on PATH.
dpkg: 3 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

```

My path is this, despite seeming correct in all of the files I have checked: "/usr/bin:/bin"

---

### Post by StrikerMan780 on 2012-07-25
Still having these issues, and I'm freaking out...  There must be SOMETHING screwing up up the $PATH variable, but everywhere I checked, the path seems correct.

---

