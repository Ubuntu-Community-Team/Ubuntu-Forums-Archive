---
title: "What packages depend on the gcc-4.2-base package?"
date: 2010-12-13
forum: General Help
---

### Post by vfclists on 2010-12-13
I was paring down my installation and did a ```
apt-get purge gcc-4.2-base
``` and the command more or less threatened to wipe out everything on the server.

Is that the norm, or is it due to a corrupted package database?

> root@sys-1275:~# apt-get purge gcc-4.2-base
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns35 linux-libc-dev autotools-dev openvpn-blacklist
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdns35
The following packages will be REMOVED:
  adduser* ajaxterm* apache2* apache2-mpm-prefork* apache2-utils* apache2.2-common* apt* apt-show-versions* apt-utils*
  aptitude* base-files* base-passwd* bash* belocs-locales-bin* bind9* binutils* bsdmainutils* bsdutils*
  build-essential* bzip2* comerr-dev* console-setup* console-terminus* console-tools* coreutils* cpio* cpp* cpp-4.2*
  cron* curl* dash* debconf* debconf-i18n* debianutils* debootstrap* defoma* dhcp3-client* dhcp3-common* dhcp3-server*
  diff* dmidecode* dpkg* dpkg-dev* e2fslibs* e2fsprogs* eject* ethtool* fail2ban* file* findutils* fontconfig*
  fontconfig-config* g++* g++-4.2* gcc* gcc-4.2* gcc-4.2-base* gettext-base* gnupg* gpgv* grep* groff-base* gzip*
  hostname* ifupdown* initramfs-tools* initscripts* iproute* iptables* iputils-ping* klogd* laptop-detect* less*
  libacl1* libapache2-mod-php5* libapr1* libaprutil1* libapt-pkg-perl* libatm1* libattr1* libaudio2*
  libauthen-pam-perl* libbind9-30* libblkid1* libbz2-1.0* libc6* libc6-dev* libc6-i686* libcap1* libck-connector0*
  libcomerr2* libconsole* libcupsys2* libcurl3* libcurl3-gnutls* libcwidget3* libdb4.6* libdbd-mysql-perl*
  libdbd-pg-perl* libdbi-perl* libdbus-1-3* libdevmapper1.02.1* libedit2* libexpat1* libfontconfig1* libfreetype6*
  libfribidi0* libgcc1* libgcrypt11* libgdbm3* libgnutls13* libgomp1* libgpg-error0* libice6* libidn11*
  libio-pty-perl* libisc35* libisccc30* libisccfg30* libiw29* libjpeg62* libkadm55* libkeyutils1* libkrb5-dev*
  libkrb53* liblcms1* libldap-2.4-2* liblocale-gettext-perl* libltdl3* libltdl3-dev* liblwres30* liblzo2-2* libmagic1*
  libmd5-perl* libmng1* libmyodbc* libmysqlclient15-dev* libmysqlclient15off* libncurses5* libncurses5-dev*
  libncursesw5* libnet-daemon-perl* libnet-ssleay-perl* libnewt0.52* libodbcinstq1c2* libopencdk10* libossp-uuid15*
  libpam-modules* libpam-smbpass* libpam0g* libpcap0.8* libpcre3* libplrpc-perl* libpng12-0* libpopt0* libpq-dev*
  libpq5* libqt3-mt* libreadline5* libsamplerate0* libsasl2-2* libsasl2-modules* libselinux1* libsepol1*
  libsigc++-2.0-0c2a* libslang2* libsm6* libsox0* libsqlite0* libsqlite3-0* libss2* libssl-dev* libssl0.9.8*
  libstdc++6* libstdc++6-4.2-dev* libsysfs2* libtasn1-3* libtext-charwidth-perl* libtext-iconv-perl*
  libtext-wrapi18n-perl* libtimedate-perl* libtool* libusb-0.1-4* libuuid1* libvolume-id0* libwrap0* libx11-6*
  libx11-data* libxau6* libxcb-xlib0* libxcb1* libxcursor1* libxdmcp6* libxext6* libxfixes3* libxft2* libxi6*
  libxinerama1* libxml2* libxrandr2* libxrender1* libxslt1.1* libxt6* locales* login* logrotate* lsb-base*
  lsb-release* lynx* lzma* make* makedev* man-db* mawk* mii-diag* mktemp* module-init-tools* mount* mysql-client*
  mysql-client-5.0* mysql-server* mysql-server-5.0* nano* ncurses-base* ncurses-bin* net-tools* netbase* netcat*
  netcat-traditional* ntpdate* odbc-postgresql* odbcinst1debian1* openssh-client* openssh-server* openssl*
  openssl-blacklist* openvpn* passwd* patch* pciutils* pcmciautils* perl* perl-base* perl-modules* php5-cgi* php5-cli*
  php5-common* php5-mysql* php5-pgsql* postgresql* postgresql-8.3* postgresql-client* postgresql-client-8.3*
  postgresql-client-8.4* postgresql-client-common* postgresql-common* postgresql-contrib* postgresql-contrib-8.3*
  postgresql-server-dev-8.3* procps* psmisc* python* python-central* python-minimal* python-support* python2.5*
  python2.5-minimal* resolvconf* samba* samba-common* sed* smbclient* smbfs* sox* sqlite* ssh* ssl-cert*
  startup-tasks* sudo* sysklogd* system-services* sysvutils* tar* tasksel* tasksel-data* tcpd* telnet* traceroute*
  ttf-dejavu* ttf-dejavu-core* ttf-dejavu-extra* tzdata* ubuntu-keyring* ubuntu-minimal* ucf* udev* unixodbc*
  unixodbc-dev* update-inetd* upstart* upstart-compat-sysv* upstart-logd* usbutils* util-linux* util-linux-locales*
  uuid-runtime* vim-common* vim-tiny* webmin* wget* whiptail* winbind* wireless-tools* wpasupplicant* x11-common*
  zlib1g* zlib1g-dev*
The following packages will be upgraded:
  libdns35
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) base-files base-passwd (due to base-files)
  libpam-modules (due to base-files) bash debianutils (due to bash) libncurses5 (due to bash) bsdutils coreutils
  libacl1 (due to coreutils) libselinux1 (due to coreutils) dash mktemp (due to debianutils) diff dpkg lzma (due to
  dpkg) e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2 (due
  to e2fsprogs) libuuid1 (due to e2fsprogs) findutils grep gzip hostname login libpam0g (due to login) mount
  ncurses-base ncurses-bin perl-base python-minimal python2.5-minimal (due to python-minimal) sed sysvutils libsepol1
  (due to sysvutils) tar util-linux lsb-base (due to util-linux) tzdata (due to util-linux) libslang2 (due to
  util-linux) zlib1g (due to util-linux)
1 upgraded, 0 newly installed, 317 to remove and 8 not upgraded.
Need to get 11.3kB of archives.
After this operation, 643MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]


Was that the norm or could it be the result of a corrupted package database?

---

### Post by mc4man on 2010-12-13
you might want to post what release of ubuntu you're using, for 8.04 quite  the "norm"

---

### Post by vfclists on 2010-12-13
Yes it is Ubuntu Hardy 8.04

> **mc4man said:**
> you might want to post what release of ubuntu you're using, for 8.04 quite  the "norm"

---

