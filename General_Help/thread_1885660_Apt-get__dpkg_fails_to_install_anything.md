---
title: "Apt-get / dpkg fails to install anything"
date: 2011-11-23
forum: General Help
---

### Post by fhumayun on 2011-11-23
After successfully updating 11.04 to 11.10 last week.  As of yesterday, I suddenly started to experience the following error while trying to do any apt-get/dpkg installs.   Any clues on how to solve this?

```

Setting up base-files (6.4ubuntu5) ...
+ [ ! -e /etc/dpkg/origins/default ]
+ [ configure = configure ]
+ [  =  ]
+ install_from_default /usr/share/base-files/nsswitch.conf /etc/nsswitch.conf
+ [ ! -f /etc/nsswitch.conf ]
+ install_from_default /usr/share/base-files/dot.profile /root/.profile
+ [ ! -f /root/.profile ]
+ install_from_default /usr/share/base-files/dot.bashrc /root/.bashrc
+ [ ! -f /root/.bashrc ]
+ install_from_default /usr/share/base-files/profile /etc/profile
+ [ ! -f /etc/profile ]
+ install_from_default /usr/share/base-files/networks /etc/networks
+ [ ! -f /etc/networks ]
+ install_directory srv 755 root
+ [ ! -d /srv ]
+ install_directory opt 755 root
+ [ ! -d /opt ]
+ install_directory etc/opt 755 root
+ [ ! -d /etc/opt ]
+ install_directory var/opt 755 root
+ [ ! -d /var/opt ]
+ install_directory media 755 root
+ [ ! -d /media ]
+ install_directory var/mail 2775 mail
+ [ ! -d /var/mail ]
+ [ ! -L /var/spool/mail ]
+ install_directory run/lock 1777 root
+ [ ! -d /run/lock ]
+ migrate_directory /var/run /run
+ [ ! -L /var/run ]
+ rmdir /var/run
rmdir: failed to remove `/var/run': Directory not empty
dpkg: error processing base-files (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 base-files
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 acidbase : Depends: libphp-adodb (>= 4.62) but it is not going to be installed
            Depends: libwww-perl but it is not going to be installed
            Depends: php-mail but it is not going to be installed
 adduser : Depends: passwd (>= 1:4.0.12) but it is not going to be installed
 alien : Depends: rpm2cpio but it is not going to be installed
 apache2.2-bin : Depends: libaprutil1 (>= 1.3.2+dfsg) but it is not going to be installed
                 Depends: libaprutil1-ldap but it is not going to be installed
                 Depends: libpcre3 (>= 8.10) but it is not going to be installed
 apache2.2-common : Depends: apache2-utils but it is not going to be installed
 apachetop : Depends: libadns1 (>= 1.4) but it is not going to be installed
             Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
             Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
             Depends: libreadline6 (>= 6.0) but it is not going to be installed
 apt : Depends: ubuntu-keyring but it is not going to be installed
       Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
       Depends: gnupg but it is not going to be installed
 apt-utils : Depends: libdb5.1 but it is not going to be installed
             Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 awffull : Depends: libpcre3 (>= 7.7) but it is not going to be installed
 bash : PreDepends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 bc : Depends: libncurses5 (>= 5.6+20071006-3) but it is not going to be installed
      Depends: libreadline6 but it is not going to be installed
      Depends: dpkg (>= 1.15.4) but it is not going to be installed or
               install-info but it is not going to be installed
 bind9 : Depends: libdb5.1 but it is not going to be installed
         Depends: liblwres60 (= 1:9.7.3.dfsg-1ubuntu4.1) but it is not going to be installed
         Depends: net-tools but it is not going to be installed
 binutils : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 ccze : Depends: libncurses5 (>= 5.6) but it is not going to be installed
        Depends: libpcre3 (>= 4.5) but it is not going to be installed
 clamav-daemon : Depends: libclamav6 (>= 0.97.3+dfsg) but it is not going to be installed
                 Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
                 Depends: clamav-base (= 0.97.3+dfsg-1ubuntu0.11.10.1) but it is not going to be installed
                 Depends: clamav-freshclam but it is not going to be installed or
                          clamav-data
 comerr-dev : Depends: libcomerr2 (= 1.41.14-1ubuntu3) but it is not going to be installed
              Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                       install-info but it is not going to be installed
 coreutils : PreDepends: libacl1 (>= 2.2.11-1) but it is not going to be installed
             PreDepends: libattr1 (>= 2.4.41-1) but it is not going to be installed
 cpio : Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                 install-info but it is not going to be installed
 cpp-4.5 : Depends: libmpc2 but it is not going to be installed
 cpp-4.6 : Depends: libmpc2 but it is not going to be installed
 cron : Depends: upstart-job
        Depends: libpam-runtime (>= 1.0.1-11) but it is not going to be installed
        PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 dash : Depends: dpkg (>= 1.15.0) but it is not going to be installed
 db5.1-util : Depends: libdb5.1 but it is not going to be installed
 dbus : Depends: libexpat1 (>= 1.95.8) but it is not going to be installed
        Depends: upstart-job
        Depends: upstart (>= 0.6.3-6) but it is not going to be installed
 dnsutils : Depends: liblwres60 (= 1:9.7.3.dfsg-1ubuntu4.1) but it is not going to be installed
            Depends: bind9-host but it is not going to be installed or
                     host
 dovecot-common : Depends: upstart-job
                  Depends: libpam-runtime (>= 0.76-13.1) but it is not going to be installed
 dovecot-imapd : Depends: dovecot-common (= 1:2.0.13-1ubuntu3) but 1:2.0.13-1ubuntu3.1 is to be installed
 dovecot-pop3d : Depends: dovecot-common (= 1:2.0.13-1ubuntu3) but 1:2.0.13-1ubuntu3.1 is to be installed
 dpkg-dev : Depends: xz-utils but it is not going to be installed
            Depends: patch but it is not going to be installed
 fail2ban : Depends: python-central (>= 0.6.11) but it is not going to be installed
 firefox : Depends: libasound2 (> 1.0.24.1)
           Depends: libatk1.0-0 (>= 1.12.4) but it is not going to be installed
           Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
           Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
           Depends: libstartup-notification0 (>= 0.8) but it is not going to be installed
           Depends: libx11-6 but it is not going to be installed
 fontconfig-config : Depends: ttf-dejavu-core but it is not going to be installed or
                              ttf-bitstream-vera but it is not going to be installed or
                              ttf-freefont but it is not going to be installed or
                              gsfonts-x11 but it is not going to be installed
 g++-4.5 : Depends: libmpc2 but it is not going to be installed
 g++-4.6 : Depends: libmpc2 but it is not going to be installed
 gcc-4.4 : Depends: libgcc1 (>= 1:4.4.6-11ubuntu2) but it is not going to be installed
 gcc-4.5 : Depends: libgcc1 (>= 1:4.5.3-9ubuntu1) but it is not going to be installed
           Depends: libmpc2 but it is not going to be installed
 gcc-4.6 : Depends: libgcc1 (>= 1:4.6.1-9ubuntu3) but it is not going to be installed
           Depends: libmpc2 but it is not going to be installed
 gettext : Depends: libcroco3 (>= 0.6.2) but it is not going to be installed
           Depends: libncurses5 (>= 5.7+20100313) but it is not going to be installed
           Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                    install-info but it is not going to be installed
 goaccess : Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 gpgv : Depends: libreadline6 (>= 6.0) but it is not going to be installed
 guile-1.8-libs : Depends: libltdl7 (>= 2.4) but it is not going to be installed
                  Depends: libreadline6 (>= 6.0) but it is not going to be installed
 html2text : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 ifupdown : Depends: iproute (>= 20071016-1) but it is not going to be installed
            Depends: upstart-job
            Depends: initscripts (>= 2.88dsf-13.3) but it is not going to be installed
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.99ubuntu8) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.99ubuntu8.1~) but it is not going to be installed
                   Depends: klibc-utils (>= 1.5.9-1) but it is not going to be installed
                   Depends: busybox-initramfs (>= 1:1.13.3-1ubuntu5) but it is not going to be installed
                   Depends: findutils (>= 4.2.24) but it is not going to be installed
 iptraf : Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 isc-dhcp-client : Depends: iproute but it is not going to be installed
 krb5-multidev : Depends: libkadm5srv-mit8 (= 1.9.1+dfsg-1ubuntu2.1) but it is not going to be installed
                 Depends: libkadm5clnt-mit8 (= 1.9.1+dfsg-1ubuntu2.1) but it is not going to be installed
 ldap-auth-config : Depends: sed (>= 3.95) but it is not going to be installed
                    Depends: ldap-auth-client but it is not going to be installed
                    PreDepends: auth-client-config but it is not going to be installed
 less : Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 libapache2-mod-php5 : Depends: libdb5.1 but it is not going to be installed
                       Depends: libpcre3 (>= 8.10) but it is not going to be installed
                       Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed or
                                apache2-mpm-itk but it is not going to be installed
                       Depends: php5-common (= 5.3.6-13ubuntu3.2) but it is not going to be installed
 libaprutil1-dbd-sqlite3 : Depends: libaprutil1 (= 1.3.12+dfsg-2) but it is not going to be installed
                           Depends: libsqlite3-0 (>= 3.5.9) but it is not going to be installed
 libaprutil1-dev : Depends: libaprutil1 (= 1.3.12+dfsg-2) but it is not going to be installed
                   Depends: libldap2-dev but it is not going to be installed
                   Depends: libapr1-dev (>= 1.2.2-1) but it is not going to be installed
                   Depends: libpq-dev but it is not going to be installed
 libapt-inst1.3 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libapt-pkg-perl : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libapt-pkg4.11 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libatkmm-1.6-1 : Depends: libatk1.0-0 (>= 1.12.4) but it is not going to be installed
                  Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
                  Depends: libglibmm-2.4-1c2a (>= 2.28.0) but it is not going to be installed
                  Depends: libsigc++-2.0-0c2a (>= 2.0.2) but it is not going to be installed
 libavahi-client3 : Depends: libavahi-common3 (>= 0.6.22) but it is not going to be installed
 libberkeleydb-perl : Depends: libdb5.1 but it is not going to be installed
 libboost-iostreams1.42.0 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libboost-iostreams1.46.1 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libc6 : Depends: libgcc1 but it is not going to be installed
 libcairo2 : Depends: libx11-6 but it is not going to be installed
             Depends: libxcb-render0 but it is not going to be installed
 libclass-c3-perl : Depends: libalgorithm-c3-perl but it is not going to be installed
 libcurl3-gnutls : Depends: libgnutls26 (>= 2.9.11-0) but it is not going to be installed
                   Depends: libidn11 (>= 1.13) but it is not going to be installed
                   Depends: librtmp0 (>= 2.3) but it is not going to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.21.6-3ubuntu3) but it is not going to be installed
                        Depends: libssl-dev but it is not going to be installed
                        Depends: libidn11-dev but it is not going to be installed
                        Depends: libldap2-dev but it is not going to be installed
 libcurses-ui-perl : Depends: libcurses-perl but it is not going to be installed
                     Depends: libterm-readkey-perl but it is not going to be installed
 libdevel-globaldestruction-perl : Depends: libsub-exporter-perl but it is not going to be installed
 libdpkg-perl : Depends: dpkg (>= 1.15.8) but it is not going to be installed
 libedit2 : Depends: libbsd0 (>= 0.0) but it is not going to be installed
            Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 libeval-closure-perl : Depends: libsub-exporter-perl but it is not going to be installed
 libexpat1-dev : Depends: libexpat1 (= 2.0.1-7ubuntu3) but it is not going to be installed
 libfontconfig1 : Depends: libexpat1 (>= 1.95.8) but it is not going to be installed
 libfontconfig1-dev : Depends: pkg-config but it is not going to be installed
 libgd2-xpm-dev : Depends: libjpeg62-dev but it is not going to be installed
                  Depends: libpng12-0-dev
 libgdbm3 : Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                     install-info but it is not going to be installed
 libgdk-pixbuf2.0-0 : Depends: libjasper1 (>= 1.900.1) but it is not going to be installed
                      Depends: libtiff4 but it is not going to be installed
                      Depends: libx11-6 but it is not going to be installed
 libglade2-0 : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
               Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
 libglib2.0-0 : Depends: libpcre3 (>= 8.10) but it is not going to be installed
 libglu1-mesa : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
                Depends: libgl1-mesa-glx but it is not going to be installed or
                         libgl1
 libgsasl7 : Depends: libidn11 (>= 1.13) but it is not going to be installed
             Depends: libntlm0 but it is not going to be installed
 libgssapi-krb5-2 : Depends: libcomerr2 (>= 1.34) but it is not going to be installed
                    Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not going to be installed
 libgtk2.0-0 : Depends: libgtk2.0-common but it is not going to be installed
               Depends: libatk1.0-0 (>= 1.12.4) but it is not going to be installed
               Depends: libcups2 (>= 1.4.0) but it is not going to be installed
               Depends: libpango1.0-0 (>= 1.28.3-2~) but it is not going to be installed
               Depends: libx11-6 but it is not going to be installed
               Depends: libxcomposite1 (>= 1:0.3-1) but it is not going to be installed
               Depends: libxdamage1 (>= 1:1.1) but it is not going to be installed
               Depends: libxfixes3 but it is not going to be installed
               Depends: libxi6 but it is not going to be installed
 libgtkmm-2.4-1c2a : Depends: libcairomm-1.0-1 (>= 1.6.4) but it is not going to be installed
                     Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
                     Depends: libglibmm-2.4-1c2a (>= 2.28.0) but it is not going to be installed
                     Depends: libpangomm-1.4-1 (>= 2.27.1) but it is not going to be installed
                     Depends: libsigc++-2.0-0c2a (>= 2.0.2) but it is not going to be installed
 libhttp-cookies-perl : Depends: libhttp-message-perl but it is not going to be installed
 libhttp-negotiate-perl : Depends: libhttp-message-perl but it is not going to be installed
 libice6 : Depends: x11-common but it is not going to be installed
 libicu44 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libk5crypto3 : Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not going to be installed
 libkdb5-5 : Depends: libcomerr2 (>= 1.01) but it is not going to be installed
             Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not going to be installed
 libkrb5-3 : Depends: libcomerr2 (>= 1.34) but it is not going to be installed
             Depends: libkeyutils1 but it is not going to be installed
             Depends: libkrb5support0 (= 1.9.1+dfsg-1ubuntu2.1) but it is not going to be installed
 libldap-2.4-2 : Depends: libgnutls26 (>= 2.9.11-0) but it is not going to be installed
                 Depends: libsasl2-2 but it is not going to be installed
 libmagickcore3 : Depends: libjasper1 (>= 1.900.1) but it is not going to be installed
                  Depends: liblcms1 (>= 1.15-1) but it is not going to be installed
                  Depends: liblqr-1-0 (>= 0.1.0) but it is not going to be installed
                  Depends: libltdl7 (>= 2.4) but it is not going to be installed
                  Depends: libtiff4 but it is not going to be installed
                  Depends: libx11-6 but it is not going to be installed
 libmagickwand3 : Depends: libx11-6 but it is not going to be installed
 libmailutils2 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
                 Depends: libgnutls26 (>= 2.7.14-0) but it is not going to be installed
                 Depends: libltdl7 (>= 2.4) but it is not going to be installed
                 Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
 libmoose-perl : Depends: libdata-optlist-perl (>= 0.107) but it is not going to be installed
                 Depends: libmro-compat-perl but it is not going to be installed
                 Depends: libpackage-deprecationmanager-perl (>= 0.11) but it is not going to be installed
                 Depends: libpackage-stash-perl (>= 0.21) but it is not going to be installed
                 Depends: libsub-exporter-perl (>= 0.980) but it is not going to be installed
                 Depends: libtask-weaken-perl but it is not going to be installed
 libmount1 : Depends: libblkid1 (>= 2.17.2) but it is not going to be installed
 libmysqlclient-dev : Depends: libmysqlclient16 (= 5.1.58-1ubuntu1) but it is not going to be installed
 libnamespace-clean-perl : Depends: libb-hooks-endofscope-perl but it is not going to be installed
                           Depends: libsub-identify-perl (>= 0.04) but it is not going to be installed
                           Depends: libpackage-stash-perl (>= 0.22) but it is not going to be installed
 libnet-imap-client-perl : Depends: libio-socket-ssl-perl but it is not going to be installed
 libnet-ldap-perl : Depends: libwww-perl but it is not going to be installed
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu2) but it is not going to be installed
 libnss-ldap : Depends: libcomerr2 (>= 1.01) but it is not going to be installed
               Depends: libsasl2-2 but it is not going to be installed
 libnss3 : Depends: libnspr4 (>= 4.8.6-0ubuntu1~) but it is not going to be installed
           Depends: libsqlite3-0 (>= 3.5.9) but it is not going to be installed
 libopenvasnasl2 : Depends: libgnutls26 (>= 2.9.11-0) but it is not going to be installed
                   Depends: libgpgme11 (>= 1.2.0) but it is not going to be installed
                   Depends: libopenvas2 (>= 2.0.4) but it is not going to be installed
                   Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
 libpam-modules : PreDepends: libdb5.1 but it is not going to be installed
                  PreDepends: libpam-modules-bin (= 1.1.3-2ubuntu2.1) but it is not going to be installed
 libpam-mysql : Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
 libpcre3-dev : Depends: libpcre3 (= 8.12-3ubuntu2) but it is not going to be installed
 libpcrecpp0 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
               Depends: libpcre3 (>= 8.10) but it is not going to be installed
 libplrpc-perl : Depends: libnet-daemon-perl but it is not going to be installed
 libpq5 : Depends: libcomerr2 (>= 1.01) but it is not going to be installed
 librpm2 : Depends: libdb5.1 but it is not going to be installed
           Depends: rpm-common (= 4.9.0-7) but it is not going to be installed
 librpmio2 : Depends: liblzma2 (>= 4.999.9beta+20091116) but it is not going to be installed
 libsasl2-modules-sql : Depends: libsasl2-modules (= 2.1.24~rc1.dfsg1+cvs2011-05-23-4ubuntu2) but it is not going to be installed
                        Depends: libmysqlclient16 (>= 5.1.50-1) but it is not going to be installed
                        Depends: libsqlite3-0 (>= 3.5.9) but it is not going to be installed
 libsdl1.2debian : Depends: libsdl1.2debian-alsa (= 1.2.14-6.1ubuntu4) but it is not going to be installed or
                            libsdl1.2debian-all (= 1.2.14-6.1ubuntu4) but it is not going to be installed or
                            libsdl1.2debian-esd (= 1.2.14-6.1ubuntu4) but it is not going to be installed or
                            libsdl1.2debian-oss (= 1.2.14-6.1ubuntu4) but it is not going to be installed or
                            libsdl1.2debian-nas (= 1.2.14-6.1ubuntu4) but it is not going to be installed or
                            libsdl1.2debian-pulseaudio (= 1.2.14-6.1ubuntu4) but it is not going to be installed
 libsqlite3-dev : Depends: libsqlite3-0 (= 3.7.7-2ubuntu2) but it is not going to be installed
 libstdc++6 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libt1-5 : Depends: libx11-6 (>= 0) but it is not going to be installed
 libthai0 : Depends: libdatrie1 (>= 0.2.0) but it is not going to be installed
 libuuid1 : Depends: passwd but it is not going to be installed
 libvarnishapi1 : Depends: libpcre3 (>= 8.10) but it is not going to be installed
 libxapian15 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libxapian22 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 libxcb1-dev : Depends: libpthread-stubs0-dev but it is not going to be installed
               Depends: libxau-dev (>= 1:1.0.0-1) but it is not going to be installed
 libxcursor1 : Depends: libx11-6 but it is not going to be installed
               Depends: libxfixes3 but it is not going to be installed
 libxdmcp-dev : Depends: x11proto-core-dev but it is not going to be installed
 libxext6 : Depends: libx11-6 but it is not going to be installed
 libxinerama1 : Depends: libx11-6 but it is not going to be installed
 libxml-libxml-perl : Depends: libxml-namespacesupport-perl but it is not going to be installed
 libxml-parser-perl : Depends: libwww-perl but it is not going to be installed
                      Depends: libexpat1 (>= 1.95.8) but it is not going to be installed
 libxml-sax-perl : Depends: libxml-namespacesupport-perl but it is not going to be installed
 libxpm-dev : Depends: libx11-dev but it is not going to be installed
              Depends: x11proto-core-dev but it is not going to be installed
              PreDepends: x11-common (>= 1:7.0.0) but it is not going to be installed
 libxpm4 : Depends: libx11-6 but it is not going to be installed
 libxrandr2 : Depends: libx11-6 but it is not going to be installed
 libxrender1 : Depends: libx11-6 but it is not going to be installed
 libxt6 : Depends: libx11-6 but it is not going to be installed
 libxtst6 : Depends: libx11-6 but it is not going to be installed
            Depends: x11-common but it is not going to be installed
 libxxf86vm1 : Depends: libx11-6 but it is not going to be installed
 locate : Depends: findutils (> 4.2.31-1) but it is not going to be installed
 login : PreDepends: libpam-runtime but it is not going to be installed
 lsb-base : Depends: sed but it is not going to be installed
 lzma : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 m4 : Depends: dpkg (>= 1.15.4) but it is not going to be installed or
               install-info but it is not going to be installed
 mailutils : Depends: libreadline6 (>= 6.0) but it is not going to be installed
             Depends: default-mta or
                      mail-transport-agent
 makedev : Depends: base-passwd (>= 3.0.4) but it is not going to be installed
 man-db : Depends: groff-base (>= 1.18.1.1-15) but it is not going to be installed
          Depends: bsdmainutils but it is not going to be installed
          Depends: dpkg (>= 1.9.0) but it is not going to be installed
          Depends: libpipeline1 (>= 1.1.0) but it is not going to be installed
 module-init-tools : Depends: upstart-job
                     PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 mountall : Depends: plymouth but it is not going to be installed
            Depends: libnih1 (>= 1.0.0) but it is not going to be installed
            Depends: libplymouth2 (>= 0.8.1-3) but it is not going to be installed
            PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 mutt : Depends: libgnutls26 (>= 2.9.11-0) but it is not going to be installed
        Depends: libgpgme11 (>= 1.2.0) but it is not going to be installed
        Depends: libidn11 (>= 1.13) but it is not going to be installed
        Depends: libncursesw5 (>= 5.6+20070908) but it is not going to be installed
        Depends: libsasl2-2 but it is not going to be installed
 mysql-client-5.1 : Depends: libdbd-mysql-perl (>= 1.2202) but it is not going to be installed
                    Depends: mysql-common (>= 5.1.58-1ubuntu1) but it is not going to be installed
                    Depends: libmysqlclient16 (>= 5.1.58-1ubuntu1) but it is not going to be installed
                    Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 mysql-client-core-5.1 : Depends: libmysqlclient16 (>= 5.1.58-1ubuntu1) but it is not going to be installed
                         Depends: libreadline6 (>= 6.0) but it is not going to be installed
 mysql-server : Depends: mysql-server-5.1 but it is not going to be installed
 mysql-server-core-5.1 : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
                         Depends: libmysqlclient16 (>= 5.1.50-1) but it is not going to be installed
 nagios-plugins-basic : Depends: iputils-ping but it is not going to be installed
 nagios3 : Depends: nagios3-core (= 3.2.3-3) but it is not going to be installed
 nagios3-cgi : Depends: nagios3-common (= 3.2.3-3) but it is not going to be installed
               Depends: apache2-utils but it is not going to be installed
 nano : Depends: libncursesw5 (>= 5.7+20100313) but it is not going to be installed
        Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                 install-info but it is not going to be installed
 ncurses-bin : PreDepends: libncurses5 (>= 5.6+20071013) but it is not going to be installed
 netbase : Depends: initscripts but it is not going to be installed
           Depends: upstart-job
 netcat : Depends: netcat-traditional (>= 1.10-39) but it is not going to be installed
 ntpdate : PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 openssh-client : Depends: dpkg (>= 1.7.0) but it is not going to be installed
                  Depends: passwd but it is not going to be installed
 openvas-plugins-base : Depends: libgnutls26 (>= 2.7.14-0) but it is not going to be installed
                        Depends: libopenvas2 (>= 2.0.4) but it is not going to be installed
                        Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
                        Depends: rsync but it is not going to be installed
 openvas-server : Depends: libgnutls26 (>= 2.7.14-0) but it is not going to be installed
                  Depends: libgpgme11 (>= 1.1.2) but it is not going to be installed
                  Depends: libopenvas2 (>= 2.0.4) but it is not going to be installed
                  Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
 p7zip : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 perl : Depends: libdb5.1 but it is not going to be installed
 perl-base : PreDepends: dpkg (>= 1.14.20) but it is not going to be installed
 php-mail-mime : Depends: php-pear but it is not going to be installed
 php-mail-mimedecode : Depends: php-pear (>= 1.6.0) but it is not going to be installed
 php-mdb2-driver-sqlite : Depends: php-pear (>= 5.2.0-8) but it is not going to be installed
                          Depends: php-mdb2 (>= 2.5.0b2-1) but it is not going to be installed
                          Depends: php5-sqlite but it is not going to be installed
 php5 : Depends: php5-common (>= 5.3.6-13ubuntu3.2) but it is not going to be installed
 php5-cgi : Depends: libdb5.1 but it is not going to be installed
            Depends: libpcre3 (>= 8.10) but it is not going to be installed
            Depends: php5-common (= 5.3.6-13ubuntu3.2) but it is not going to be installed
 php5-cli : Depends: libdb5.1 but it is not going to be installed
            Depends: libpcre3 (>= 8.10) but it is not going to be installed
            Depends: php5-common (= 5.3.6-13ubuntu3.2) but it is not going to be installed
 php5-imap : Depends: libc-client2007e but it is not going to be installed
 php5-intl : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
             Depends: php5-common (= 5.3.6-13ubuntu3.2) but it is not going to be installed
 php5-ldap : Depends: php5-common (= 5.3.6-13ubuntu3.2) but it is not going to be installed
 php5-mcrypt : Depends: libmcrypt4 but it is not going to be installed
 php5-mysql : Depends: libmysqlclient16 (>= 5.1.50-1) but it is not going to be installed
              Depends: php5-common (= 5.3.6-13ubuntu3.2) but it is not going to be installed
 po-debconf : Depends: intltool-debian (>= 0.34.2+20060512) but it is not going to be installed
 postfix-ldap : Depends: postfix (= 2.8.5-2~build1) but it is not going to be installed
 postfix-pcre : Depends: libpcre3 (>= 8.10) but it is not going to be installed
                Depends: postfix (= 2.8.5-2~build1) but it is not going to be installed
 postgrey : Depends: libnet-dns-perl but it is not going to be installed
            Depends: libnet-server-perl (>= 0.87) but it is not going to be installed
 procinfo : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
            Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 procps : Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
          Depends: libncursesw5 (>= 5.6+20070908) but it is not going to be installed
          Depends: upstart-job
          Depends: initscripts but it is not going to be installed
 psmisc : Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
 python-apt : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
 python-gnupginterface : Depends: gnupg (>= 1.2.1) but it is not going to be installed or
                                  gnupg2 but it is not going to be installed
 python-minimal : Depends: python2.7-minimal (>= 2.7.2-3~) but it is not going to be installed
                  Depends: dpkg (>= 1.13.20) but it is not going to be installed
 python-mysqldb : Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
 python-software-properties : Depends: unattended-upgrades but it is not going to be installed
                              Depends: iso-codes but it is not going to be installed
 python-support : Depends: dpkg (>= 1.14.19) but it is not going to be installed
 python2.6 : Depends: python2.6-minimal (= 2.6.7-4ubuntu1) but it is not going to be installed
             Depends: libdb4.8 but it is not going to be installed
             Depends: libexpat1 (>= 1.95.8) but it is not going to be installed
             Depends: libncursesw5 (>= 5.6+20070908) but it is not going to be installed
             Depends: libreadline6 (>= 6.0) but it is not going to be installed
             Depends: libsqlite3-0 (>= 3.5.9) but it is not going to be installed
 python2.7 : Depends: python2.7-minimal (= 2.7.2-5ubuntu1) but it is not going to be installed
             Depends: libdb4.8 but it is not going to be installed
             Depends: libexpat1 (>= 1.95.8) but it is not going to be installed
             Depends: libncursesw5 (>= 5.6+20070908) but it is not going to be installed
             Depends: libreadline6 (>= 6.0) but it is not going to be installed
             Depends: libsqlite3-0 (>= 3.5.9) but it is not going to be installed
 razor : Depends: libnet-dns-perl but it is not going to be installed
 readline-common : Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                            install-info but it is not going to be installed
 rpm : Depends: librpmbuild2 (>= 4.9.0) but it is not going to be installed
       Depends: librpmsign0 (>= 4.9.0) but it is not going to be installed
       Depends: rpm2cpio but it is not going to be installed
       Depends: rpm-common (= 4.9.0-7) but it is not going to be installed
 rrdtool : Depends: librrd4 (>= 1.4~rc2) but it is not going to be installed
 sharutils : Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                      install-info but it is not going to be installed
 snort-common-libraries : Depends: libpcre3 (>= 8.10) but it is not going to be installed
 snort-mysql : Depends: snort-rules-default (>= 2.8.5.2-9.1) but it is not going to be installed
               Depends: rsyslog but it is not going to be installed or
                        system-log-daemon
               Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
               Depends: libpcap0.8 (>= 0.9.8) but it is not going to be installed
               Depends: libpcre3 (>= 8.10) but it is not going to be installed
               Depends: libprelude2 but it is not going to be installed
               Depends: logrotate but it is not going to be installed
 sun-java6-plugin : Depends: libasound2
                    Depends: libx11-6 but it is not going to be installed
                    Depends: libxi6 but it is not going to be installed
 sysutils : Depends: memtester but it is not going to be installed
            Depends: tofrodos but it is not going to be installed
 sysv-rc : Depends: insserv (> 1.12.0-10) but it is not going to be installed
 telnet : Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
          Depends: libncurses5 (>= 5.6+20071006-3) but it is not going to be installed
 tripwire : Depends: postfix but it is not going to be installed or
                     mail-transport-agent
 ttf-dejavu : Depends: ttf-dejavu-core but it is not going to be installed
              Depends: ttf-dejavu-extra but it is not going to be installed
 udev : Depends: libacl1 (>= 2.2.51-3) but it is not going to be installed
        Depends: upstart-job
 unixodbc : Depends: libltdl7 (>= 2.2.6b) but it is not going to be installed
            Depends: libreadline6 (>= 6.0) but it is not going to be installed
            Depends: odbcinst1debian2 (>= 2.2.11-3) but it is not going to be installed
 update-inetd : Depends: libfile-copy-recursive-perl but it is not going to be installed
 util-linux : Depends: dpkg (>= 1.15.4) but it is not going to be installed or
                       install-info but it is not going to be installed
              Depends: upstart-job
              PreDepends: libblkid1 (>= 2.19.1) but it is not going to be installed
              PreDepends: libncurses5 (>= 5.5-5~) but it is not going to be installed
              PreDepends: libslang2 (>= 2.0.7-1) but it is not going to be installed
 varnish : Depends: libncurses5 (>= 5.5-5~) but it is not going to be installed
           Depends: libpcre3 (>= 8.10) but it is not going to be installed
           Depends: gcc (>= 3.3) but it is not going to be installed
 webmin : Depends: libnet-ssleay-perl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not going to be installed
          Depends: libpam-runtime but it is not going to be installed
          Depends: apt-show-versions but it is not going to be installed
 whiptail : Depends: libnewt0.52 (>= 0.52.11) but it is not going to be installed
            Depends: libslang2 (>= 2.0.7-1) but it is not going to be installed
 whois : Depends: libidn11 (>= 1.13) but it is not going to be installed
 x11proto-input-dev : Depends: x11proto-core-dev but it is not going to be installed
 xml-core : Depends: sed (>= 4.1.2-8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
.. install failed!
```


 lsb_release -vr
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Release:        11.10

```
cat /etc/apt/sources.list
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

```

---

### Post by McNils on 2011-11-23
try 
sudo apt-get install -f

---

### Post by fhumayun on 2011-11-23
Results of apt-get -f install   =  fail :(

```
 apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsdl1.2debian libvorbisfile3 g++-4.6 libxxf86vm1 libcdb1 libtdb1 libglu1-mesa libregexp-assemble-perl
  libsqlite3-dev libxslt1.1 liberror-perl libnetaddr-ip-perl libmysqlclient-dev libnamespace-clean-perl
  searchandrescue-data python-markupsafe libatkmm-1.6-1 libmikmod2 searchandrescue-common libpython2.6
  libgtkmm-2.4-1c2a libglade2-0 liblzo2-2 libboost-iostreams1.46.1 uuid-dev libvariable-magic-perl vim-runtime
  libvorbis0a libaprutil1-dev libstdc++6-4.6-dev nginx-common libevtlog0 libnet1 db5.1-util libogg0
  libsigc++-2.0-0c2a libglibmm-2.4-1c2a libgl1-mesa-glx libpangomm-1.4-1 libcairomm-1.0-1 libapr1-dev libpq-dev
  libglapi-mesa libsdl1.2debian-alsa libsub-identify-perl libb-hooks-endofscope-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apt-show-versions auth-client-config base-passwd bind9-host bsdmainutils
  busybox-initramfs clamav-base clamav-freshclam cpp dovecot-common dovecot-imapd dovecot-pop3d dpkg findutils gcc
  gnupg groff-base initramfs-tools-bin initscripts insserv intltool-debian iproute iputils-ping iso-codes
  klibc-utils ldap-auth-client libacl1 libadns1 libalgorithm-c3-perl libapr1-dev libaprutil1 libaprutil1-ldap
  libasound2 libatk1.0-0 libattr1 libauthen-pam-perl libavahi-common-data libavahi-common3
  libb-hooks-endofscope-perl libblkid1 libbsd0 libc-client2007e libcairomm-1.0-1 libclamav6 libcomerr2 libcroco3
  libcups2 libcurl3 libcurses-perl libdata-optlist-perl libdatrie1 libdb4.8 libdb5.1 libdbd-mysql-perl
  libencode-locale-perl libexpat1 libfile-copy-recursive-perl libfile-listing-perl libgcc1 libgl1-mesa-glx
  libglapi-mesa libglibmm-2.4-1c2a libgnutls26 libgpgme11 libgtk2.0-common libhtml-tree-perl libhttp-message-perl
  libidn11 libidn11-dev libio-socket-ssl-perl libjasper1 libjpeg62-dev libkadm5clnt-mit8 libkadm5srv-mit8
  libkeyutils1 libklibc libkrb5support0 liblcms1 libldap2-dev liblqr-1-0 libltdl7 liblwp-protocol-https-perl
  liblwres60 liblzma2 libmcrypt4 libmpc2 libmro-compat-perl libmysqlclient16 libncurses5 libncursesw5
  libnet-daemon-perl libnet-dns-perl libnet-server-perl libnet-ssleay-perl libnewt0.52 libnih1 libnspr4 libntlm0
  libopenvas2 libpackage-deprecationmanager-perl libpackage-stash-perl libpam-ldap libpam-modules-bin
  libpam-runtime libpango1.0-0 libpangomm-1.4-1 libpcap0.8 libpcre3 libphp-adodb libpipeline1 libplymouth2
  libpng12-dev libpq-dev libprelude2 libpthread-stubs0-dev libreadline6 librpmbuild2 librpmsign0 librrd4 librtmp0
  libsasl2-2 libsasl2-modules libsdl1.2debian-alsa libsigc++-2.0-0c2a libslang2 libsqlite3-0 libssl-dev
  libstartup-notification0 libsub-exporter-perl libsub-identify-perl libtask-weaken-perl libterm-readkey-perl
  libtiff4 libtommath0 libwww-perl libx11-6 libx11-dev libxau-dev libxcb-render0 libxcomposite1 libxdamage1
  libxfixes3 libxft2 libxi6 libxml-namespacesupport-perl logrotate memtester mount mysql-common mysql-server-5.1
  nagios3-common nagios3-core net-tools netcat-traditional odbcinst odbcinst1debian2 passwd patch php-mail php-mdb2
  php-pear php5-common php5-sqlite pkg-config plymouth postfix python-central python2.6-minimal python2.7-minimal
  rpm-common rpm2cpio rsync rsyslog sed snort-rules-default tofrodos ttf-dejavu-core ttf-dejavu-extra
  ubuntu-keyring unattended-upgrades upstart x11-common x11proto-core-dev x11proto-kb-dev xz-utils
Suggested packages:
  libpam-cracklib wamerican wordlist vacation clamav-docs apparmor cpp-doc ntp ufw gcc-multilib manpages-dev
  autoconf automake1.9 libtool flex gdb gcc-doc gnupg-curl gnupg-doc libpcsclite1 groff bootchart iproute-doc
  isoquery adns-tools libasound2-plugins libasound2-python uw-mailutils libclamunrar6 cups-common gnutls-bin gpgsm
  libjasper-runtime krb5-doc krb5-user liblcms-utils libcrypt-ssleay-perl libmcrypt-dev mcrypt ttf-japanese-gothic
  ttf-japanese-mincho ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp php5-adodb postgresql-doc-9.1 libsasl2-modules-otp libsasl2-modules-ldap
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal libauthen-ntlm-perl nfs-common tinyca
  nagios-nrpe-plugin ed diffutils-doc php5-suhosin postfix-mysql postfix-pgsql sasl2-bin resolvconf postfix-cdb
  binfmt-support rpm-i18n openssh-server rsyslog-mysql rsyslog-pgsql rsyslog-doc rsyslog-gnutls rsyslog-gssapi
  rsyslog-relp bsd-mailx graphviz bash-completion xz-lzma
Recommended packages:
  clamav e2fsprogs libatm1 libgl1-mesa-dri libclass-c3-xs-perl libgpm2 x-ttcidfont-conf libssl-doc
  libhtml-form-perl libhtml-format-perl libhttp-daemon-perl libhtml-template-perl nagios-plugins php-net-smtp
  php5-dev plymouth-theme-ubuntu-text plymouth-theme oinkmaster
The following NEW packages will be installed:
  apache2-mpm-prefork apache2-utils apt-show-versions auth-client-config base-passwd bind9-host bsdmainutils
  busybox-initramfs clamav-base clamav-freshclam cpp dpkg findutils gcc gnupg groff-base initramfs-tools-bin
  initscripts insserv intltool-debian iproute iputils-ping iso-codes klibc-utils ldap-auth-client libacl1 libadns1
  libalgorithm-c3-perl libapr1-dev libaprutil1 libaprutil1-ldap libasound2 libatk1.0-0 libattr1 libauthen-pam-perl
  libavahi-common-data libavahi-common3 libb-hooks-endofscope-perl libblkid1 libbsd0 libc-client2007e
  libcairomm-1.0-1 libclamav6 libcomerr2 libcroco3 libcups2 libcurl3 libcurses-perl libdata-optlist-perl libdatrie1
  libdb4.8 libdb5.1 libdbd-mysql-perl libencode-locale-perl libexpat1 libfile-copy-recursive-perl
  libfile-listing-perl libgcc1 libgl1-mesa-glx libglapi-mesa libglibmm-2.4-1c2a libgnutls26 libgpgme11
  libgtk2.0-common libhtml-tree-perl libhttp-message-perl libidn11 libidn11-dev libio-socket-ssl-perl libjasper1
  libjpeg62-dev libkadm5clnt-mit8 libkadm5srv-mit8 libkeyutils1 libklibc libkrb5support0 liblcms1 libldap2-dev
  liblqr-1-0 libltdl7 liblwp-protocol-https-perl liblwres60 liblzma2 libmcrypt4 libmpc2 libmro-compat-perl
  libmysqlclient16 libncurses5 libncursesw5 libnet-daemon-perl libnet-dns-perl libnet-server-perl
  libnet-ssleay-perl libnewt0.52 libnih1 libnspr4 libntlm0 libopenvas2 libpackage-deprecationmanager-perl
  libpackage-stash-perl libpam-ldap libpam-modules-bin libpam-runtime libpango1.0-0 libpangomm-1.4-1 libpcap0.8
  libpcre3 libphp-adodb libpipeline1 libplymouth2 libpng12-dev libpq-dev libprelude2 libpthread-stubs0-dev
  libreadline6 librpmbuild2 librpmsign0 librrd4 librtmp0 libsasl2-2 libsasl2-modules libsdl1.2debian-alsa
  libsigc++-2.0-0c2a libslang2 libsqlite3-0 libssl-dev libstartup-notification0 libsub-exporter-perl
  libsub-identify-perl libtask-weaken-perl libterm-readkey-perl libtiff4 libtommath0 libwww-perl libx11-6
  libx11-dev libxau-dev libxcb-render0 libxcomposite1 libxdamage1 libxfixes3 libxft2 libxi6
  libxml-namespacesupport-perl logrotate memtester mount mysql-common mysql-server-5.1 nagios3-common nagios3-core
  net-tools netcat-traditional odbcinst odbcinst1debian2 passwd patch php-mail php-mdb2 php-pear php5-common
  php5-sqlite pkg-config plymouth postfix python-central python2.6-minimal python2.7-minimal rpm-common rpm2cpio
  rsync rsyslog sed snort-rules-default tofrodos ttf-dejavu-core ttf-dejavu-extra ubuntu-keyring
  unattended-upgrades upstart x11-common x11proto-core-dev x11proto-kb-dev xz-utils
The following packages will be upgraded:
  dovecot-common dovecot-imapd dovecot-pop3d
3 upgraded, 184 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/89.6 MB of archives.
After this operation, 216 MB of additional disk space will be used.
Do you want to continue [Y/n]?Y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up base-files (6.4ubuntu5) ...
+ [ ! -e /etc/dpkg/origins/default ]
+ [ configure = configure ]
+ [  =  ]
+ install_from_default /usr/share/base-files/nsswitch.conf /etc/nsswitch.conf
+ [ ! -f /etc/nsswitch.conf ]
+ install_from_default /usr/share/base-files/dot.profile /root/.profile
+ [ ! -f /root/.profile ]
+ install_from_default /usr/share/base-files/dot.bashrc /root/.bashrc
+ [ ! -f /root/.bashrc ]
+ install_from_default /usr/share/base-files/profile /etc/profile
+ [ ! -f /etc/profile ]
+ install_from_default /usr/share/base-files/networks /etc/networks
+ [ ! -f /etc/networks ]
+ install_directory srv 755 root
+ [ ! -d /srv ]
+ install_directory opt 755 root
+ [ ! -d /opt ]
+ install_directory etc/opt 755 root
+ [ ! -d /etc/opt ]
+ install_directory var/opt 755 root
+ [ ! -d /var/opt ]
+ install_directory media 755 root
+ [ ! -d /media ]
+ install_directory var/mail 2775 mail
+ [ ! -d /var/mail ]
+ [ ! -L /var/spool/mail ]
+ install_directory run/lock 1777 root
+ [ ! -d /run/lock ]
+ migrate_directory /var/run /run
+ [ ! -L /var/run ]
+ rmdir /var/run
rmdir: failed to remove `/var/run': Directory not empty
dpkg: error processing base-files (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by oldtimer7777 on 2011-11-23
> **McNils said:**
> try 
sudo apt-get install -f

Don't do upgrades if you want a production system. Do fresh installations with a guide like this:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

You really can't go wrong that way..  Back up your work first, naturally.

---

### Post by fhumayun on 2011-11-23
This is the heart of the problem


 **dpkg --configure -a**
Setting up base-files (6.4ubuntu5) ...
+ [ ! -e /etc/dpkg/origins/default ]
+ [ configure = configure ]
+ [  =  ]
+ install_from_default /usr/share/base-files/nsswitch.conf /etc/nsswitch.conf
+ [ ! -f /etc/nsswitch.conf ]
+ install_from_default /usr/share/base-files/dot.profile /root/.profile
+ [ ! -f /root/.profile ]
+ install_from_default /usr/share/base-files/dot.bashrc /root/.bashrc
+ [ ! -f /root/.bashrc ]
+ install_from_default /usr/share/base-files/profile /etc/profile
+ [ ! -f /etc/profile ]
+ install_from_default /usr/share/base-files/networks /etc/networks
+ [ ! -f /etc/networks ]
+ install_directory srv 755 root
+ [ ! -d /srv ]
+ install_directory opt 755 root
+ [ ! -d /opt ]
+ install_directory etc/opt 755 root
+ [ ! -d /etc/opt ]
+ install_directory var/opt 755 root
+ [ ! -d /var/opt ]
+ install_directory media 755 root
+ [ ! -d /media ]
+ install_directory var/mail 2775 mail
+ [ ! -d /var/mail ]
+ [ ! -L /var/spool/mail ]
+ install_directory run/lock 1777 root
+ [ ! -d /run/lock ]
+ migrate_directory /var/run /run
+ [ ! -L /var/run ]
+ rmdir /var/run
**rmdir: failed to remove `/var/run': Directory not empty**
dpkg: error processing base-files (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 base-files

---

### Post by sladner84 on 2011-11-23
Try sudo dpkg --configure -a

---

### Post by T.exe on 2011-11-23
I too had the same problem after installing CodeBlocks from source. Nothing worked.. not even 
**sudo apt-get install -f**
Since I could not fix this even after solutions provided in numerous forums, I did a fresh install of 11.10 and the first thing I got installed in my new system was** Synaptic** (pity Canonical didn't include this by default in 11.10). Later if I faced such installation problems, I could easily remove the broken packages using synaptic.

However, i am still curious to know the solution of the problem mentioned above as fresh OS installation is always a 'Last Resort Solution'. Any help???

---

### Post by fhumayun on 2011-11-23
Guess it's a confirmed  [bug]("https://bugs.launchpad.net/ubuntu/+source/multistrap/+bug/874505")

Luckily its just a stand-alone web server.  I'll walk away for now to see if there's a way to patch this problem later; but if the box needs to be blown away, then I'm going Fedora 15/CentOS.

---

### Post by oldtimer7777 on 2011-11-23
I recommend a fresh install.  Upgrading just blows.

> **fhumayun said:**
> Guess it's a confirmed  [bug]("https://bugs.launchpad.net/ubuntu/+source/multistrap/+bug/874505")

Luckily its just a stand-alone web server.  I'll walk away for now to see if there's a way to patch this problem later; but if the box needs to be blown away, then I'm going Fedora 15/CentOS.

---

### Post by achim_59 on 2012-08-26
> **oldtimer7777 said:**
> I recommend a fresh install.  Upgrading just blows.

You may be right about it being s safer way to update the O/S, however, there are good reasons for doing upgrades.

I recently had the less than enjoyable experience of doing 2 days battle with a fresh install to get all the settings back the way I wanted them. If you use anything which requires a variety of settings and script changes, then a fresh install is going to give you headaches, since some of the settings which need to be transferred are occasionally in different places on the new O/S. A good upgrade (and Ubuntu upgrades are usually, though not always, good) will automatically make the necessary adjustments. Of course, this has the disadvantage, that you won't find the changes yourself until you've done a bit of research. A bit of a problem if you subsequently want to make further changes.

Cheers
Achim

---

### Post by psyllex on 2012-12-31
> **achim_59 said:**
> You may be right about it being s safer way to update the O/S, however, there are good reasons for doing upgrades.

I recently had the less than enjoyable experience of doing 2 days battle with a fresh install to get all the settings back the way I wanted them. If you use anything which requires a variety of settings and script changes, then a fresh install is going to give you headaches, since some of the settings which need to be transferred are occasionally in different places on the new O/S. A good upgrade (and Ubuntu upgrades are usually, though not always, good) will automatically make the necessary adjustments. Of course, this has the disadvantage, that you won't find the changes yourself until you've done a bit of research. A bit of a problem if you subsequently want to make further changes.

Cheers
Achim


I agree...doing a fresh install after you've spent months getting your distro just perfect is such a downer.  One suggestion I would make is before you update use VirtualBox and make a copy of your distro then load into the VM then do an update from there....see if there are going to be any problems first.  If not or if they are minor, then go ahead in update.  If there are a host of problems, this way, you can sort them out or make the decision to do a fresh install.

---

