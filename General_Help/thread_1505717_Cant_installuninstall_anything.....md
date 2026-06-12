---
title: "Cant install/uninstall anything...."
date: 2010-06-09
forum: General Help
---

### Post by team420 on 2010-06-09
Hi all, 

 I'm having some troubles with ubuntu... I tried to download some files yesterday with ktorrent, about 10 min into the dload, the system hung up, only way to to get her running again, was a hard restart, so I tried to open ktorrent again, and after 10 min, did the same thing, so I then restart(again, with the reset button) and decide to open ktorrent to remove the files, this time, the system hung as soon as I opened ktorrent, so another hard restart, and decided to just uninstall ktorrent all together, and re-install later. Uninstalled just fine, and then reinstalled just fine, but same problem when I tried to open it again, 
 So I decided to just uninstall it completely... and thats when the fun started...

  So I go into terminal and type "sudo apt-get remove ktorrent" ands heres what I get...

```
 jim@jim-desktop:~$ sudo apt-get remove ktorrent
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
jim@jim-desktop:~$ 

```

I am still pretty new to ubuntu, so I have no idea what to do from here.... it seems to be running ok, for now, but I cant install/uninstall anything... so any help would be greatly appreciated!

---

### Post by SlidingHorn on 2010-06-09
open a terminal and run

```
df
``` 

sounds like it's possible thaty ou might be out of disk space

---

### Post by team420 on 2010-06-09
Thanks, but I dont think I'm outta space... Heres what I got from "df"

```
jim@jim-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             24873240  13634756   9974976  58% /
udev                    512660       288    512372   1% /dev
none                    512660      2024    510636   1% /dev/shm
none                    512660        84    512576   1% /var/run
none                    512660         0    512660   0% /var/lock
none                    512660         0    512660   0% /lib/init/rw
jim@jim-desktop:~$ 
 
```

---

### Post by ThesaurusRex on 2010-06-09
This used to happen to me at work. Are you in a situation where you have to go through a proxy server to get internet?

---

### Post by team420 on 2010-06-09
nope... I do go thru my router, but all ports are open for this unit...

---

### Post by ThesaurusRex on 2010-06-09
Did you get the same errors when trying to do this in Synaptic Package Manager? Or did you try using aptitude instead of apt-get (shouldn't have any effect)?

---

### Post by team420 on 2010-06-09
yes getting same errors thru package manager.

I hope I dont have to install a fresh copy to make this better, otherwise, its not better for me than windows... and I really dont wanna go back to windows!

---

### Post by SlidingHorn on 2010-06-09
Hmmm...try this:

```
sudo dpkg --clear-avail
sudo apt-get update
```

if no dice, check this response: [http://ubuntuforums.org/showpost.php?p=7943852&postcount=6](http://ubuntuforums.org/showpost.php?p=7943852&postcount=6)

---

### Post by team420 on 2010-06-09
Thanks... heres what I got...

[HTML] jim@jim-desktop:~$ sudo dpkg --clear-avail
[sudo] password for jim: 
jim@jim-desktop:~$ sudo apt-get updatep
E: Invalid operation updatep
jim@jim-desktop:~$ 
[/HTML]

Will check that link

---

### Post by ThesaurusRex on 2010-06-09
> **team420 said:**
> yes getting same errors thru package manager.

I hope I dont have to install a fresh copy to make this better, otherwise, its not better for me than windows... and I really dont wanna go back to windows!

The problem sounds like an inability to access the web, in my opinion. I wouldn't blame Ubuntu for such tricky tasks. Do you have wget? Try:

```
wget http://google.com
```

If wget is installed and you get an error, your problem is most-likely internet-related.

---

### Post by team420 on 2010-06-09
Heres what I got... I dont think its net related, cuz I'm on the machine, viewing this site.....



```
jim@jim-desktop:~$ wget http://google.com
--2010-06-09 14:09:10--  http://google.com/
Resolving google.com... 72.14.204.103, 72.14.204.104, 72.14.204.147, ...
Connecting to google.com|72.14.204.103|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.google.com/ [following]
--2010-06-09 14:09:10--  http://www.google.com/
Resolving www.google.com... 72.14.204.104, 72.14.204.147, 72.14.204.99, ...
Reusing existing connection to google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 8,109       --.-K/s   in 0.03s   

2010-06-09 14:09:10 (234 KB/s) - `index.html' saved [8109]
 
```

---

### Post by SlidingHorn on 2010-06-09
> **team420 said:**
> Thanks... heres what I got...

[HTML] jim@jim-desktop:~$ sudo dpkg --clear-avail
[sudo] password for jim: 
jim@jim-desktop:~$ sudo apt-get updatep
E: Invalid operation updatep
jim@jim-desktop:~$ 
[/HTML]

Will check that link

sorry, had a typo in there...I edited the 2nd command

---

### Post by team420 on 2010-06-09
> **SlidingHorn said:**
> sorry, had a typo in there...I edited the 2nd command

Ya, i just figure that out...lol  Same errors tho... guess Ill try whats in that link...

---

### Post by team420 on 2010-06-09
> **SlidingHorn said:**
> Hmmm...try this:
: [http://ubuntuforums.org/showpost.php?p=7943852&postcount=6](http://ubuntuforums.org/showpost.php?p=7943852&postcount=6)

I think this did the trick! I'll report when I know for sure, 

THANK YOU!!!:guitar:

---

### Post by team420 on 2010-06-09
ok... no more hanging, but when I try to re-install ktorrent, I get this error...

```
 jim@jim-desktop:~$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adduser apt apt-utils arora aspell aspell-en base-files base-passwd
  busybox-initramfs ca-certificates console-setup console-terminus consolekit
  coreutils cpio cpp cpp-4.4 dbus dbus-x11 debconf debconf-i18n debianutils
  defoma dictionaries-common dmsetup dpkg e2fslibs e2fsprogs eject exiv2 file
  findutils fontconfig fontconfig-config gawk gcc-4.4-base geoip-database
  ghostscript gnupg gpgv gsfonts hal hal-info hdparm hicolor-icon-theme
  hunspell-en-us ifupdown initramfs-tools initscripts insserv kbd
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data kdepimlibs-data kdepimlibs5 khelpcenter4 klibc-utils
  ktorrent-data libaa1 libacl1 libakonadiprivate1 libasound2 libaspell15
  libattr1 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3
  libblkid1 libboost-program-options1.38.0 libbz2-1.0 libc-bin libc6
  libc6-i686 libcaca0 libcairo2 libcap2 libck-connector0 libclucene0ldbl
  libcomerr2 libcups2 libcupsimage2 libcurl3-gnutls libdatrie1 libdb4.7
  libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1 libdirectfb-1.2-0
  libdjvulibre-text libdjvulibre21 libdrm-intel1 libdrm-radeon1 libdrm2
  libeggdbus-1-0 libenchant1c2a libexiv2-5 libexpat1 libflac8 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libgcc1 libgcrypt11 libgd2-noxpm
  libgdbm3 libgeoip1 libgif4 libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0
  libglib2.0-data libglu1-mesa libgmp3c2 libgnutls26 libgomp1 libgpg-error0
  libgpgme11 libgpm2 libgraphviz4 libgs8 libgssapi-krb5-2 libhal-storage1
  libhal1 libhunspell-1.2-0 libical0 libice6 libidn11 libilmbase6 libjasper1
  libjpeg62 libk5crypto3 libkeyutils1 libklibc libknotificationitem1 libkrb5-3
  libkrb5support0 liblcms1 libldap-2.4-2 liblocale-gettext-perl libltdl7
  liblzma0 libmagic1 libmagickcore2 libmagickwand2 libmng1 libmodplug0c2
  libmpcdec3 libmpfr1ldbl libmysqlclient16 libncurses5 libncursesw5
  libnewt0.52 libogg0 libopenexr6 libpam-ck-connector libpam-modules
  libpam-runtime libpam0g libpango1.0-0 libpango1.0-common libpaper-utils
  libpaper1 libpci3 libpciaccess0 libpcre3 libpixman-1-0 libplasma3 libpng12-0
  libpolkit-gobject-1-0 libpopt0 libpq5 libpth20 libpulse0 libpython2.6
  libqca2 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-phonon libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-webkit libqt4-xml libqtcore4 libqtgui4 libraptor1
  librasqal1 librdf0 libreadline6 libsasl2-2 libsasl2-modules libsdl1.2debian
  libsdl1.2debian-alsa libselinux1 libsepol1 libslang2 libslp1 libsm6
  libsmbclient libsndfile1 libsoprano4 libspeex1 libsqlite3-0 libss2
  libssl0.9.8 libstdc++6 libstreamanalyzer0 libstreams0 libsysfs2
  libtag1-vanilla libtag1c2a libtalloc1 libtasn1-3 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtheora0
  libtiff4 libts-0.0-0 libudev0 libusb-0.1-4 libuuid1 libvorbis0a
  libvorbisenc2 libwavpack1 libwbclient0 libwmf0.2-7 libwrap0 libx11-6
  libx11-data libx86-1 libxau6 libxaw7 libxcb-render-util0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcursor1 libxdamage1
  libxdmcp6 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxine1 libxine1-bin
  libxine1-console libxine1-misc-plugins libxine1-x libxinerama1 libxml2
  libxml2-utils libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxslt1.1
  libxt6 libxtrap6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86misc1
  libxxf86vm1 lsb-base lzma make mime-support module-init-tools mount mountall
  mysql-common ncurses-bin net-tools netbase openssl passwd pciutils perl
  perl-base perl-modules phonon-backend-xine pm-utils powermgmt-base procps
  psfontmgr psmisc python2.6 python2.6-minimal radeontool raptor-utils
  readline-common redland-utils sed sgml-base shared-mime-info smartdimmer
  soprano-daemon sysv-rc sysvinit-utils tcpd tsconf ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra tzdata ubuntu-keyring ucf udev upstart usbutils util-linux
  uuid-runtime vbetool whiptail x-ttcidfont-conf x11-common x11-utils
  x11-xserver-utils xauth xdg-utils xfonts-encodings xfonts-utils xkb-data
  xml-core zlib1g
Suggested packages:
  ecryptfs-utils aptitude synaptic gnome-apt wajig dpkg-dev apt-doc bzip2
  python-apt aspell-doc spellutils locales cpp-doc gcc-4.4-locales debconf-doc
  debconf-utils libterm-readline-gnu-perl libgnome2-perl libqt-perl
  libnet-ldap-perl defoma-doc dfontmgr libft-perl ispell emacsen-common
  jed-extra gpart parted e2fsck-static cdtool setcd mlocate locate slocate
  ghostscript-cups ghostscript-x hpijs gnupg-doc xloadimage imagemagick eog
  libpcsclite1 gnome-device-manager apmd hunspell openoffice.org-hunspell
  openoffice.org-core iproute dhcp3-client dhcp-client ppp bootchart kdebase
  djvulibre-bin plasma-widget-ktorrent akonadi-server libasound2-plugins nas
  glibc-doc cups-common libenchant-voikko rng-tools libgd-tools geoip-bin
  libglide3 gnutls-bin gpgsm gpm krb5-doc krb5-user libjasper-runtime
  liblcms-utils libpam-doc ttf-japanese-gothic ttf-japanese-mincho
  ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp pulseaudio libqca2-plugin-cyrus-sasl
  libqca2-plugin-gnupg libqca2-plugin-ossl libqca2-plugin-pkcs11 libqt4-dev
  qt4-qtconfig libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal slpd openslp-doc
  speex libwmf0.2-7-gtk gxine xine-ui libxine1-doc libxine-doc libxine1-ffmpeg
  make-doc nfs-common openssl-doc wget curl lynx perl-doc cpufrequtils
  python2.6-doc python2.6-profiler binutils binfmt-support sgml-base-doc
  sysv-rc-conf bum sash watershed util-linux-locales dosfstools mesa-utils
  nickle cairo-5c desktop-file-utils libgnome2-0 exo-utils libgnomevfs2-bin
  kdelibs4c2a konqueror libgtk2.0-bin debhelper
Recommended packages:
  iceweasel www-browser
The following NEW packages will be installed:
  adduser apt apt-utils arora aspell aspell-en base-files base-passwd
  busybox-initramfs ca-certificates console-setup console-terminus consolekit
  coreutils cpio cpp cpp-4.4 dbus dbus-x11 debconf debconf-i18n debianutils
  defoma dictionaries-common dmsetup dpkg e2fslibs e2fsprogs eject exiv2 file
  findutils fontconfig fontconfig-config gawk gcc-4.4-base geoip-database
  ghostscript gnupg gpgv gsfonts hal hal-info hdparm hicolor-icon-theme
  hunspell-en-us ifupdown initramfs-tools initscripts insserv kbd
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data kdepimlibs-data kdepimlibs5 khelpcenter4 klibc-utils ktorrent
  ktorrent-data libaa1 libacl1 libakonadiprivate1 libasound2 libaspell15
  libattr1 libaudio2 libavahi-client3 libavahi-common-data libavahi-common3
  libblkid1 libboost-program-options1.38.0 libbz2-1.0 libc-bin libc6
  libc6-i686 libcaca0 libcairo2 libcap2 libck-connector0 libclucene0ldbl
  libcomerr2 libcups2 libcupsimage2 libcurl3-gnutls libdatrie1 libdb4.7
  libdbus-1-3 libdbus-glib-1-2 libdevmapper1.02.1 libdirectfb-1.2-0
  libdjvulibre-text libdjvulibre21 libdrm-intel1 libdrm-radeon1 libdrm2
  libeggdbus-1-0 libenchant1c2a libexiv2-5 libexpat1 libflac8 libfontconfig1
  libfontenc1 libfreetype6 libfribidi0 libgcc1 libgcrypt11 libgd2-noxpm
  libgdbm3 libgeoip1 libgif4 libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0
  libglib2.0-data libglu1-mesa libgmp3c2 libgnutls26 libgomp1 libgpg-error0
  libgpgme11 libgpm2 libgraphviz4 libgs8 libgssapi-krb5-2 libhal-storage1
  libhal1 libhunspell-1.2-0 libical0 libice6 libidn11 libilmbase6 libjasper1
  libjpeg62 libk5crypto3 libkeyutils1 libklibc libknotificationitem1 libkrb5-3
  libkrb5support0 liblcms1 libldap-2.4-2 liblocale-gettext-perl libltdl7
  liblzma0 libmagic1 libmagickcore2 libmagickwand2 libmng1 libmodplug0c2
  libmpcdec3 libmpfr1ldbl libmysqlclient16 libncurses5 libncursesw5
  libnewt0.52 libogg0 libopenexr6 libpam-ck-connector libpam-modules
  libpam-runtime libpam0g libpango1.0-0 libpango1.0-common libpaper-utils
  libpaper1 libpci3 libpciaccess0 libpcre3 libpixman-1-0 libplasma3 libpng12-0
  libpolkit-gobject-1-0 libpopt0 libpq5 libpth20 libpulse0 libpython2.6
  libqca2 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-phonon libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-webkit libqt4-xml libqtcore4 libqtgui4 libraptor1
  librasqal1 librdf0 libreadline6 libsasl2-2 libsasl2-modules libsdl1.2debian
  libsdl1.2debian-alsa libselinux1 libsepol1 libslang2 libslp1 libsm6
  libsmbclient libsndfile1 libsoprano4 libspeex1 libsqlite3-0 libss2
  libssl0.9.8 libstdc++6 libstreamanalyzer0 libstreams0 libsysfs2
  libtag1-vanilla libtag1c2a libtalloc1 libtasn1-3 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libthai-data libthai0 libtheora0
  libtiff4 libts-0.0-0 libudev0 libusb-0.1-4 libuuid1 libvorbis0a
  libvorbisenc2 libwavpack1 libwbclient0 libwmf0.2-7 libwrap0 libx11-6
  libx11-data libx86-1 libxau6 libxaw7 libxcb-render-util0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcursor1 libxdamage1
  libxdmcp6 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxine1 libxine1-bin
  libxine1-console libxine1-misc-plugins libxine1-x libxinerama1 libxml2
  libxml2-utils libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxslt1.1
  libxt6 libxtrap6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86misc1
  libxxf86vm1 lsb-base lzma make mime-support module-init-tools mount mountall
  mysql-common ncurses-bin net-tools netbase openssl passwd pciutils perl
  perl-base perl-modules phonon-backend-xine pm-utils powermgmt-base procps
  psfontmgr psmisc python2.6 python2.6-minimal radeontool raptor-utils
  readline-common redland-utils sed sgml-base shared-mime-info smartdimmer
  soprano-daemon sysv-rc sysvinit-utils tcpd tsconf ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra tzdata ubuntu-keyring ucf udev upstart usbutils util-linux
  uuid-runtime vbetool whiptail x-ttcidfont-conf x11-common x11-utils
  x11-xserver-utils xauth xdg-utils xfonts-encodings xfonts-utils xkb-data
  xml-core zlib1g
0 upgraded, 346 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/155MB of archives.
After this operation, 538MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on libattr1
jim@jim-desktop:~$ 

```

BTW, its not just ktorrent, I cant install anything....

---

### Post by SlidingHorn on 2010-06-09
Dont know if these will help, but here's a couple things I found on the error:

[http://ubuntuforums.org/showpost.php?p=8975428&postcount=7](http://ubuntuforums.org/showpost.php?p=8975428&postcount=7)

[http://ubuntuforums.org/showthread.php?t=1440108](http://ubuntuforums.org/showthread.php?t=1440108)

[My Google search]("http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+%22E%3A+Internal+Error%2C+Could+not+perform+immediate+configuration+%282%29+on+libattr1%22&ie=utf-8&oe=utf-8")

---

### Post by team420 on 2010-06-09
No luck...still getting same error.   Looks like I have to re-install? Anyone got another way around a fresh install?

---

### Post by team420 on 2010-06-09
Also... when I try to run update manager, I get this error...

```
"You have 1 broken package on your system!

Use the "Broken" filter to locate it." 
```

What is this "broken" filter, and how do I use it?

---

### Post by team420 on 2010-06-09
Ok... so I got to the point where I could install/un-install packages again, so tried re-installing ktorrent, and am right back to square 1... what gives here...  Ktorrent was just fine the other day, then all of a sudden it takes a poop?

O, I had to command...

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update 
```

In order to install/un-install

---

