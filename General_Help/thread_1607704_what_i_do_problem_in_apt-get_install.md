---
title: "what i do problem in apt-get install"
date: 2010-10-28
forum: General Help
---

### Post by hgltqgs on 2010-10-28
hi all

 i have problem in apt-get 

i went instll compizconfig-settings-manager but
Message Error 

pls help me thank you 




root@skaka-desktop:~# sudo apt-get install [COLOR="Sienna"]compizconfig-settings-manager[/COLOR] 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-compizconfig
The following NEW packages will be installed:
  compizconfig-settings-manager python-compizconfig
0 upgraded, 2 newly installed, 0 to remove and 297 not upgraded.
4 not fully installed or removed.
Need to get 676kB of archives.
After this operation, 4,329kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic/universe python-compizconfig 0.8.2-0ubuntu1 [37.9kB]
Get:2 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic/universe compizconfig-settings-manager 0.8.2-0ubuntu1 [638kB]
Fetched 676kB in 17s (38.0kB/s)                                                        
Selecting previously deselected package python-compizconfig.
(Reading database ... 132219 files and directories currently installed.)
Unpacking python-compizconfig (from .../python-compizconfig_0.8.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up policykit (0.9-4ubuntu1) ...
groupadd: cannot lock /etc/group; [COLOR="Sienna"]try again later[/COLOR].
[COLOR="Sienna"]adduser: `/usr/sbin/groupadd -g 122 polkituser' returned error code 10[/COLOR]. Exiting.
[COLOR="Sienna"]dpkg: error processing policykit (--configure):[/COLOR]
 [COLOR="Sienna"]subprocess installed post-installation script returned error exit status 1[/COLOR]
dpkg: dependency problems prevent configuration of kdebase-workspace-bin:
 kdebase-workspace-bin depends on policykit; however:
  Package policykit is not configured yet.
[COLOR="Sienna"]dpkg: error processing kdebase-workspace-bin (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR="Sienna"]dpkg: dependency problems prevent configuration of k3b:[/COLOR]
 k3b depends on kdebase-workspace-bin; however:
  Package kdebase-workspace-bin is not configured yet.
[COLOR="Sienna"]dpkg: error processing k3b (--configure):[/COLOR]
 dependency problems - leaving unconfigured
Setting up winbind (2:3.4.0-3ubuntu5.6) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                  No apport report written because the error message indicates its a followup error from a previous failure.
                                    groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 122 winbindd_priv' returned error code 10. Exiting.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-compizconfig (0.8.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Setting up compizconfig-settings-manager (0.8.2-0ubuntu1) ...

Errors were encountered while processing:
 policykit
 kdebase-workspace-bin
 k3b
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drz4007 on 2010-10-28
Why don't you upgrade first all those packages? Maybe the problem is somewhere there. Go to System, Administration, Synaptic, and choose Mark All Upgrades.

---

### Post by Hippytaff on 2010-10-28
you can also try doing

```

sudo apt-get update && sudo apt-get upgrade

```
First :-)

---

### Post by Rasa1111 on 2010-10-28
> **Hippytaff said:**
> you can also try doing

```

sudo apt-get update && sudo apt-get upgrade

```
First :-)

that usually works for me also. :KS

---

### Post by andymorton on 2010-10-28
You could try installing it through the software centre.

andy

---

### Post by hgltqgs on 2010-10-28
same problem !!! 


root@skaka-desktop:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50 liblwres50
  linux-generic linux-headers-generic linux-image-generic sreadahead
The following packages will be upgraded:
  adduser aisleriot app-install-data-partner apparmor apparmor-utils apport apport-gtk
  avahi-autoipd avahi-daemon base-files bash-completion binutils bogofilter
  bogofilter-bdb bogofilter-common brasero bzip2 checkbox checkbox-gtk compiz
  compiz-core compiz-gnome compiz-plugins compiz-wrapper cups cups-bsd cups-client
  cups-common devicekit-disks devicekit-power dhcp3-client dhcp3-common dpkg empathy
  empathy-doc erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key
  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evince f-spot
  fglrx-modaliases firefox firefox-branding flashplugin-installer foomatic-filters
  fuse-utils gcalctool gdm ghostscript ghostscript-cups ghostscript-x gimp gimp-data
  glchess glines gnect gnibbles gnobots2 gnome-about gnome-blackjack
  gnome-desktop-data gnome-games gnome-games-common gnome-mahjongg gnome-power-manager
  gnome-screensaver gnome-settings-daemon gnome-sudoku gnometris gnomine gnotravex
  gnotski grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-x gtali gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gzip iagno ibus ibus-gtk ifupdown
  initscripts jockey-common jockey-gtk kerneloops-daemon kolourpaint4 language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base lftp
  libapparmor-perl libapparmor1 libatasmart4 libaudiofile0 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core6 libavahi-glib1
  libavahi-gobject0 libavahi-ui0 libbrasero-media0 libbz2-1.0 libc-bin libc-dev-bin
  libc6 libc6-dev libc6-i686 libcairo2 libclutter-gtk-0.10-0 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0
  libdevkit-power-gobject1 libempathy-common libempathy-gtk-common libempathy-gtk28
  libempathy30 libenchant1c2a libevdocument1 libevview1 libexpat1 libfreetype6
  libfuse2 libgail-common libgail18 libgd2-xpm libgdiplus libgimp2.0 libglib2.0-0
  libglib2.0-data libgnome-desktop-2-11 libgs8 libgssapi-krb5-2
  libgstreamer-plugins-base0.10-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgudev-1.0-0 libhtml-parser-perl libibus1 libindicate-gtk1 libindicate3
  libk5crypto3 libkpathsea4 libkrb5-3 libkrb5support0 libldap-2.4-2 libmetacity0
  libnautilus-extension1 libnspr4-0d libnss3-1d libpam-modules libpam-runtime libpam0g
  libpcsclite1 libpng12-0 libpoppler-glib4 libpoppler5 libpq5 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0 libpython2.6 libsmbclient
  libthai-data libthai0 libtiff4 libudev0 libvorbis0a libvorbisenc2 libvorbisfile3
  libvte-common libvte9 libwbclient0 libwebkit-1.0-2 libwebkit-1.0-common libwww-perl
  libxml2 libxml2-utils linux-firmware linux-libc-dev metacity metacity-common
  nautilus nautilus-data ntpdate nvidia-common obexd-client openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer openssl poppler-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11
  pulseaudio-utils python python-apport python-avahi python-gtkhtml2 python-ibus
  python-libxml2 python-minimal python-problem-report python-ubuntuone-client
  python-ubuntuone-storageprotocol python-uno python-vte python2.6 python2.6-minimal
  rhythmbox rsyslog samba-common samba-common-bin same-gnome smbclient software-center
  sudo system-tools-backends sysv-rc sysvinit-utils telepathy-gabble
  transmission-common transmission-gtk ttf-opensymbol tzdata ubuntu-xsplash-artwork
  ubuntuone-client ubuntuone-client-gnome udev uno-libs3 update-manager
  update-manager-core upstart ure w3m wget winbind x11-common xorg xsane xsane-common
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-video-all xserver-xorg-video-intel xsplash xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support xulrunner-1.9.2 yelp
285 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
4 not fully installed or removed.
Need to get 246MB of archives.
After this operation, 3,875kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libc-bin 2.10.1-0ubuntu18 [714kB]
Get:2 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libc6 2.10.1-0ubuntu18 [3,871kB]
Get:3 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libc6-i686 2.10.1-0ubuntu18 [1,200kB]
Get:4 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libc-dev-bin 2.10.1-0ubuntu18 [206kB]
Get:5 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libc6-dev 2.10.1-0ubuntu18 [4,772kB]
Get:6 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main linux-libc-dev 2.6.31-22.67 [773kB]
Get:7 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main tzdata 2010m-0ubuntu0.9.10 [770kB]
Get:8 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libfreetype6 2.3.9-5ubuntu0.2 [394kB]
Get:9 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libglib2.0-0 2.22.3-0ubuntu1 [913kB]
Get:10 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main base-files 5.0.0ubuntu7.1 [68.4kB]
Get:11 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libpam-modules 1.1.0-2ubuntu1.1 [360kB]
Get:12 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libpam-runtime 1.1.0-2ubuntu1.1 [115kB]
Get:13 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libpam0g 1.1.0-2ubuntu1.1 [124kB]
Get:14 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libpng12-0 1.2.37-1ubuntu0.2 [172kB]
Get:15 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main adduser 3.110ubuntu7 [118kB]   
Get:16 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libgssapi-krb5-2 1.7dfsg~beta3-1ubuntu0.6 [109kB]
Get:17 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libkrb5-3 1.7dfsg~beta3-1ubuntu0.6 [338kB]
Get:18 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libkrb5support0 1.7dfsg~beta3-1ubuntu0.6 [40.2kB]
Get:19 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) karmic-updates/main libk5crypto3 1.7dfsg~beta3-1ubuntu0.6 [103kB]
...........................................
...........................................
............................................
...........................................
tu1.1_i386.deb) ...
Unpacking replacement libpam-modules ...
Processing triggers for man-db ...
Setting up libpam-modules (1.1.0-2ubuntu1.1) ...

(Reading database ... 132436 files and directories currently installed.)
Preparing to replace libpam-runtime 1.1.0-2ubuntu1 (using .../libpam-runtime_1.1.0-2ubuntu1.1_all.deb) ...
Unpacking replacement libpam-runtime ...
Processing triggers for man-db ...
Setting up libpam-runtime (1.1.0-2ubuntu1.1) ...

(Reading database ... 132436 files and directories currently installed.)
Preparing to replace libpam0g 1.1.0-2ubuntu1 (using .../libpam0g_1.1.0-2ubuntu1.1_i386.deb) ...
Unpacking replacement libpam0g ...
Setting up libpam0g (1.1.0-2ubuntu1.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 132436 files and directories currently installed.)
Preparing to replace libpng12-0 1.2.37-1 (using .../libpng12-0_1.2.37-1ubuntu0.2_i386.deb) ...
Unpacking replacement libpng12-0 ...
Preparing to replace adduser 3.110ubuntu6 (using .../adduser_3.110ubuntu7_all.deb) ...
Unpacking replacement adduser ...
Preparing to replace libgssapi-krb5-2 1.7dfsg~beta3-1 (using .../libgssapi-krb5-2_1.7dfsg~beta3-1ubuntu0.6_i386.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.7dfsg~beta3-1 (using .../libkrb5-3_1.7dfsg~beta3-1ubuntu0.6_i386.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.7dfsg~beta3-1 (using .../libkrb5support0_1.7dfsg~beta3-1ubuntu0.6_i386.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libk5crypto3 1.7dfsg~beta3-1 (using .../libk5crypto3_1.7dfsg~beta3-1ubuntu0.6_i386.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace libldap-2.4-2 2.4.18-0ubuntu1 (using .../libldap-2.4-2_2.4.18-0ubuntu1.1_i386.deb) ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace libwbclient0 2:3.4.0-3ubuntu5 (using .../libwbclient0_2%3a3.4.0-3ubuntu5.7_i386.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.4.0-3ubuntu5.6 (using .../smbclient_2%3a3.4.0-3ubuntu5.7_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace winbind 2:3.4.0-3ubuntu5.6 (using .../winbind_2%3a3.4.0-3ubuntu5.7_i386.deb) ...
 * Stopping the Winbind daemon winbind                                           [ OK ] 
Unpacking replacement winbind ...
Preparing to replace samba-common 2:3.4.0-3ubuntu5.6 (using .../samba-common_2%3a3.4.0-3ubuntu5.7_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace dpkg 1.15.4ubuntu2 (using .../dpkg_1.15.4ubuntu2.2_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Setting up dpkg (1.15.4ubuntu2.2) ...

(Reading database ... 132436 files and directories currently installed.)
Preparing to replace gzip 1.3.12-8ubuntu1 (using .../gzip_1.3.12-8ubuntu1.1_i386.deb) ...
Ignoring install-info called from maintainer script
The package gzip should be rebuild with new debhelper to get trigger support
Unpacking replacement gzip ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up gzip (1.3.12-8ubuntu1.1) ...
(Reading database ... 132436 files and directories currently installed.)
Preparing to replace libpython2.6 2.6.4~rc2-0ubuntu1 (using .../libpython2.6_2.6.4-0ubuntu3_i386.deb) ...
Unpacking replacement libpython2.6 ...
Preparing to replace bzip2 1.0.5-3 (using .../bzip2_1.0.5-3ubuntu0.1_i386.deb) ...
Unpacking replacement bzip2 ...
Preparing to replace libbz2-1.0 1.0.5-3 (using .../libbz2-1.0_1.0.5-3ubuntu0.1_i386.deb) ...
Unpacking replacement libbz2-1.0 ...
Preparing to replace python2.6 2.6.4~rc2-0ubuntu1 (using .../python2.6_2.6.4-0ubuntu3_i386.deb) ...
Unpacking replacement python2.6 ...
Preparing to replace python2.6-minimal 2.6.4~rc2-0ubuntu1 (using .../python2.6-minimal_2.6.4-0ubuntu3_i386.deb) ...
Unpacking replacement python2.6-minimal ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up python2.6-minimal (2.6.4-0ubuntu3) ...

(Reading database ... 132436 files and directories currently installed.)
Preparing to replace python 2.6.4~rc1-0ubuntu1 (using .../python_2.6.4-0ubuntu1_all.deb) ...
Unpacking replacement python ...
Preparing to replace python-minimal 2.6.4~rc1-0ubuntu1 (using .../python-minimal_2.6.4-0ubuntu1_all.deb) ...
Unpacking replacement python-minimal ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up python-minimal (2.6.4-0ubuntu1) ...
(Reading database ... 132436 files and directories currently installed.)
Preparing to replace sysvinit-utils 2.87dsf-4ubuntu11 (using .../sysvinit-utils_2.87dsf-4ubuntu12_i386.deb) ...
Unpacking replacement sysvinit-utils ...
Processing triggers for man-db ...
Setting up sysvinit-utils (2.87dsf-4ubuntu12) ...
(Reading database ... 132436 files and directories currently installed.)
Preparing to replace sysv-rc 2.87dsf-4ubuntu11 (using .../sysv-rc_2.87dsf-4ubuntu12_all.deb) ...
Unpacking replacement sysv-rc ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Setting up sysv-rc (2.87dsf-4ubuntu12) ...

(Reading database ... 132436 files and directories currently installed.)
Preparing to replace initscripts 2.87dsf-4ubuntu11 (using .../initscripts_2.87dsf-4ubuntu12_i386.deb) ...
Unpacking replacement initscripts ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Setting up initscripts (2.87dsf-4ubuntu12) ...
Installing new version of config file /etc/init.d/umountfs ...

(Reading database ... 132435 files and directories currently installed.)
Preparing to replace upstart 0.6.3-10 (using .../upstart_0.6.3-11_i386.deb) ...
Unpacking replacement upstart ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Setting up upstart (0.6.3-11) ...
Installing new version of config file /etc/init/rc-sysinit.conf ...

(Reading database ... 132435 files and directories currently installed.)
Preparing to replace x11-common 1:7.4+3ubu
..........................................
............................................
...............................................
...............................................
................................................
....................................................

Setting up fglrx-modaliases (2:8.660-0ubuntu4.1) ...
Setting up gnome-settings-daemon (2.28.1-0ubuntu2) ...

Setting up grub-common (1.97~beta4-1ubuntu4.1) ...
Installing new version of config file /etc/grub.d/30_os-prober ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

Setting up kolourpaint4 (4:4.3.2-0ubuntu1.1) ...

Setting up openoffice.org-emailmerge (1:3.1.1-5ubuntu1.2) ...
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
Copying: mailmerge.py
Enabling: mailmerge.py
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml

unopkg done.

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Setting up apparmor-utils (2.3.1+1403-0ubuntu27.3) ...
Setting up language-pack-en (1:9.10+20100604) ...
Setting up pulseaudio-module-udev (1:0.9.19-0ubuntu4.1) ...
Setting up xserver-xorg (1:7.4+3ubuntu10) ...

Setting up xserver-xorg-core (2:1.6.4-2ubuntu4.3) ...

Setting up xorg (1:7.4+3ubuntu10) ...
Setting up language-pack-en-base (1:9.10+20100604) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

Setting up language-pack-gnome-en (1:9.10+20100604.2) ...
Setting up firefox-branding (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Setting up pulseaudio (1:0.9.19-0ubuntu4.1) ...
 * PulseAudio configured for per-user sessions

Setting up pulseaudio-module-gconf (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio-esound-compat (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio-module-x11 (1:0.9.19-0ubuntu4.1) ...
Setting up xserver-xorg-video-intel (2:2.9.0-1ubuntu2.1) ...

Setting up xserver-xorg-video-all (1:7.4+3ubuntu10) ...
Setting up language-pack-gnome-en-base (1:9.10+20100604.2) ...

Setting up firefox (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 policykit
 kdebase-workspace-bin
 k3b
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Hippytaff on 2010-10-28
which version of ubuntu are you using? how did you install it?
before you do
```

sudo apt-get upgrade

```
you need to do
```

sudo apt-get update

```
you might have already done that though :-s

---

### Post by drz4007 on 2010-10-28
Sometimes when upgrading through the terminal some packages are kept back (The following packages have been kept back:
bind9-host dnsutils libbind9-50 libdns50 libisc50 libisccc50 libisccfg50 liblwres50
linux-generic linux-headers-generic linux-image-generic sreadahead). I dont know why. Try to upgrade through Synaptic (System, Administration, Synaptic, and choose Mark All Upgrades, Apply).

---

### Post by hgltqgs on 2010-10-28
i do that but same problem !!

[ATTACH]173781[/ATTACH]

---

### Post by hgltqgs on 2010-10-29
up

---

### Post by Hippytaff on 2010-10-29
Have you upgraded to 10.10 - just wondering whether this might have caused the problem...anyway

try these
```

sudo apt-get autoclean

```
```

sudo apt-get install -f

```
Then do the update/upgrade thing...if that doesn't do it, make a note of the packages that are held back and try to install them manuall (sudo apt-get install package/dependecy name)

copy and paste the results - also when posting code if you highlight the text then click on the # in the you of the box it wraps it puts it in a box, easier to read :-)

---

### Post by hgltqgs on 2010-11-03
thank you but same problem

[COLOR="Red"]skaka@skaka-desktop:~$ sudo apt-get autoclean[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del xulrunner-1.9.2 1.9.2.11+build3+nobinonly-0ubuntu0.9.10.1 [9,689kB]
Del xulrunner-1.9.1-gnome-support 1.9.1.14+build4+nobinonly-0ubuntu0.9.10.1 [40.3kB]
Del xulrunner-1.9.1 1.9.1.14+build4+nobinonly-0ubuntu0.9.10.1 [8,033kB]
[COLOR="Red"]skaka@skaka-desktop:~$ sudo apt-get install -f[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up policykit (0.9-4ubuntu1) ...
groupadd: cannot lock /etc/group; try again later.
adduser: `/usr/sbin/groupadd -g 122 polkituser' returned error code 10. Exiting.
dpkg: error processing policykit (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kdebase-workspace-bin:
 kdebase-workspace-bin depends on policykit; however:
  Package policykit is not configured yet.
dpkg: error processing kdebase-workspace-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdebase-workspace-bin; however:
  Package kdebase-workspace-bin is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Setting up winbind (2:3.4.0-3ubuntu5.7) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    groupadd: cannot lock /etc/group; try again later.
addgroup: `/usr/sbin/groupadd -g 122 winbindd_priv' returned error code 10. Exiting.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
[COLOR="Green"] policykit
 kdebase-workspace-bin
 k3b
 winbind[/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Hippytaff on 2010-11-03
Out of interest are you using KDE or Gnome?
 
I would suggest uninstalling the packages causing the problem and then relinstalling them, but might be better to do a bit of reading first.

---

### Post by oldos2er on 2010-11-03
Which version of Ubuntu are you using? Was it an upgrade from a previous version, or a clean install?

---

