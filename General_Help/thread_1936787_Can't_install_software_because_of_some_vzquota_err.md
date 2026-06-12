---
title: "Can't install software because of some vzquota errors"
date: 2012-03-06
forum: General Help
---

### Post by EmilHem on 2012-03-06
So when installing openjdk-6-jre but also vsftpd I get very many errors in the console.
I'm running Debian 6 32 bit.


```
root@vu-rp:/home/castle/mc# apt-get install openjdk-6-jre
Reading package lists... Done
Building dependency tree
Reading state information... Done
openjdk-6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up x11-common (1:7.5+8+squeeze1) ...
insserv: warning: script 'S10vzquota' missing LSB tags and overrides
insserv: warning: script is corrupt or invalid: /etc/init.d/../rc6.d/S00vzreboot
insserv: warning: script 'vzquota' missing LSB tags and overrides
insserv: There is a loop between service vzquota and single if started
insserv:  loop involving service single at depth 13
insserv:  loop involving service vzquota at depth 12
insserv:  loop involving service sysklogd at depth 11
insserv: There is a loop between service vzquota and single if started
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing x11-common (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      configured to not write apport reports
                                                                            dpkg: dependency problems prevent configuration of libice6:
 libice6 depends on x11-common; however:
  Package x11-common is not configured yet.
dpkg: error processing libice6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsm6:
 libsm6 depends on libice6 (>= 1:1.0.0); however:
  Package libice6 is not configured yet.
dpkg: error processing libsm6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxtst6:
 libxtst6 depends on x11-common; however:
  Package x11-common is not configured yet.
dpkg: error processing libxtst6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpulse0:
 libpulse0 depends on libice6 (>= 1:1.0.0); however:
  Package libice6 is not configured yet.
 libpulse0 depends on libsm6; however:
  Package libsm6 is not configured yet.
 libpulse0 depends on libxtst6; however:
  Package libxtconfigured to not write apport reports
                                                     configured to not write apport reports
                                                                                           configured to not write apport reports
                                                                                                                                 configured to not write apport reports
               configured to not write apport reports
                                                     st6 is not configured yet.
dpkg: error processing libpulse0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on libpulse0 (>= 0.9.21); however:
  Package libpulse0 is not configured yet.
 openjdk-6-jre depends on libxtst6; however:
  Package libxtst6 is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaccess-bridge-java:
 libaccess-bridge-java depends on default-jre | openjdk-6-jre | sun-java6-jre; however:
  Package default-jre is not installed.
  Package openjdk-6-jre is not configured yet.
  Package sun-java6-jre is not installed.
dpkg: error processing libaccess-bridge-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaccess-bridge-java-jni:
 libaccess-bridge-java-jni depends on libaccess-bridge-java (>= configured to not write apport reports
                                                                                                      configured to not write apport reports
                                                                                                                                            configured to not write apport reports
                          configured to not write apport reports
                                                                1.26.2-5); however:
  Package libaccess-bridge-java is not configured yet.
dpkg: error processing libaccess-bridge-java-jni (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfonts-encodings:
 xfonts-encodings depends on x11-common; however:
  Package x11-common is not configured yet.
dpkg: error processing xfonts-encodings (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfonts-utils:
 xfonts-utils depends on x11-common; however:
  Package x11-common is not configured yet.
 xfonts-utils depends on xfonts-encodings; however:
  Package xfonts-encodings is not configured yet.
dpkg: error processing xfonts-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x-ttcidfont-conf:
 x-ttcidfont-conf depends on xfonts-utils; however:
  Package xfonts-utils is not configured yet.
dpkg: error processing x-ttcidfont-conf (--configure):
 dependency problems - leaving unconfigured
Setting up vsftpd (2.3.2-3+squeeze2) ...
vsftpd user (ftp) already exists, doing nothing.

vsftpd directory (/srv/ftp) already exists, doing nothing.
insserv: warning: script 'S10vzquota' missing LSB tags and overrides
insserv: warning: script is corrupt or invalid: /etc/init.d/../rc6.d/S00vzreboot
insserv: warning: script 'vzquota' missing LSB tags and overrides
insserv: There is a loop between service vzquota and single if started
insserv:  loop involving service single at depth 13
insserv:  loop involving service vzquota at depth 12
insserv:  loop involving service sysklogd at depth 11
insserv: There is a loop between service vzquota and single if started
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Starting vzquota depends on single and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing vsftpd (--configure):
 subprocess installed post-installation script returned error exit status 1
configured to not write apport reports
                                      Errors were encountered while processing:
 x11-common
 libice6
 libsm6
 libxtst6
 libpulse0
 openjdk-6-jre
 libaccess-bridge-java
 libaccess-bridge-java-jni
 xfonts-encodings
 xfonts-utils
 x-ttcidfont-conf
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is after trying to install it the second time.

---

