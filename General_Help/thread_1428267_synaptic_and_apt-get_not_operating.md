---
title: "synaptic and apt-get not operating"
date: 2010-03-12
forum: General Help
---

### Post by nkbatsi on 2010-03-12
[SIZE="2"]I have this problem with synaptic and apt-get.
seems i cannot install or uninstall anything.

i already did

sudo apt-get update

worked fine

sudo apt-get clean

i think it worked ok cause it returned no messages at all

and then i did autoremove and this is what i got[/SIZE]

nkbatsi@kavourdistiri:~$ sudo apt-get autoremove
[sudo] password for nkbatsi: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nkbatsi@kavourdistiri:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
26 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libqt4-svg (4.5.3really4.5.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-svg (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libclucene0ldbl (0.9.20-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libclucene0ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsoprano4:
 libsoprano4 depends on libclucene0ldbl (>= 0.9.20-1); however:
  Package libclucene0ldbl is not configured yet.
dpkg: error processing libsoprano4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of soprano-daemon:
 soprano-daemon depends on libsoprano4 (>= 2.3.0); however:
  Package libsoprano4 is not configured yet.
dpkg: error processing soprano-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up libexiv2-5 (0.18.2-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libexiv2-5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libstreams0 (0.7.0-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libstreams0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libstreamanalyzer0:
 libstreamanalyzer0 depends on libclucene0ldbl (>= 0.9.20-1); however:
  Package libclucene0ldbl is not configured yet.
 libstreamanalyzer0 depends on libexiv2-5; however:
  Package libexiv2-5 is not configured yet.
 libstreamanalyzer0 depends on libstreams0 (= 0.7.0-1); however:
  Package libstreams0 is not configured yet.
dpkg: error processing libstreamanalyzer0 (--configure):
 dependency problems - leaving unconfigured
Setting up kdelibs5-data (4:4.3.5-0ubuntu1~karmic1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdelibs5-data (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdelibs5:
 kdelibs5 depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
 kdelibs5 depends on libsoprano4 (>= 2.2.69); however:
  Package libsoprano4 is not configured yet.
 kdelibs5 depends on libstreamanalyzer0 (>= 0.7.0); however:
  Package libstreamanalyzer0 is not configured yet.
 kdelibs5 depends on kdelibs5-data (>= 4:4.3.5-0ubuntu1~karmic1); however:
  Package kdelibs5-data is not configured yet.
dpkg: error processing kdelibs5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on kdelibs5 (= 4:4.3.5-0ubuntu1~karmic1); however:
  Package kdelibs5 is not configured yet.
 kdelibs-bin depends on liNo apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                bsoprano4 (>= 2.1.67); however:
  Package libsoprano4 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exiv2:
 exiv2 depends on libexiv2-5; however:
  Package libexiv2-5 is not configured yet.
dpkg: error processing exiv2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotificationitem1:
 libknotificationitem1 depends on kdelibs5 (>= 4:4.3.4); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libknotificationitem1 (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-opengl (4.5.3really4.5.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-opengl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-webkit (4.5.3really4.5.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-webkit (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on kdelibs5 (>= 4:4.3.5); however:
  Package kdelibs5 is not configured yet.
 libplasma3 depends on libqt4-opengl (>= 4.5.1); however:
  Package libqt4-opengl is not configured yet.
 libplasma3 depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
 libplasma3 depends on libqt4-webkit (>= 4.5.1); however:
  Package libqt4-webkit is not configured yet.
 libplasma3 depends on kdelibs5-data (= 4:4.3.5-0ubuntu1~karmic1); however:
  Package kdelibs5-data is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
Setting up libxine1-bin (1.1.16.3-0ubuntu4) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxine1-bin (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1-misc-plugins:
 libxine1-misc-plugins depends on libxine1-bin (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-bin is not configured yet.
dpkg: error processing libxine1-misc-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up libxcb-shape0 (1.4-1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxcb-shape0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxcb-shm0 (1.4-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxcb-xv0 (1.4-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxcb-xv0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1-x:
 libxine1-x depends on libxcb-shape0; however:
  Package libxcb-shape0 is not configured yet.
 libxine1-x depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
 libxine1-x depends on libxcb-xv0; however:
  Package libxcb-xv0 is not configured yet.
 libxine1-x depends on libxine1-bin (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-bin is not configured yet.
dpkg: error processing libxine1-x (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxine1-console:
 libxine1-console depends on libxine1-bin (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-bin is not configured yet.
dpkg: error processing libxine1-console (--configure):
 depNo apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      endency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxine1-misc-plugins (= 1.1.16.3-0ubuntu4) | libxine1-plugins (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-misc-plugins is not configured yet.
  Package libxine1-plugins is not installed.
 libxine1 depends on libxine1-x (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-x is not configured yet.
 libxine1 depends on libxine1-console (= 1.1.16.3-0ubuntu4); however:
  Package libxine1-console is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phonon-backend-xine:
 phonon-backend-xine depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
dpkg: error processing phonon-backend-xine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on kdelibs5 (>= 4:4.3.5); however:
  Package kdelibs5 is not configured yet.
 kdebase-runtime depends on libclucene0ldbl (>= 0.9.20-1); however:
  Package libclucene0ldbl is not configured yet.
 kdebase-runtime depends on libknotificationitem1; however:
  Package libknotificationitem1 is not configured yet.
 kdebase-runtime depends on libplasma3 (>= 4:4.3.5); however:
  Package libplasma3 is not configured yet.
 kdebase-runtime depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
 kdebase-runtime depends on libsoprano4 (>= 2.3.0); however:
  Package libsoprano4 is not configured yet.
 kdebase-runtime depends on libstreamanalyzer0 (>= 0.7.0); however:
  Package libstreamanalyzer0 is not configured yet.
 kdebase-runtime depends on libstreams0 (>= 0.7.0); however:
  Package libstreams0 is not configured yet.
 kdebase-runtime depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
 kdebase-runtime depends on phonon-backend-xine | phonon-backend; however:
  Package phonon-backend-xine is not configured yet.
  Package phonon-backend is not installed.
  Package phonon-backend-xine which provides phonon-backend is not configured yet.
dpkg: error processing kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime-bin-kde4:
 kdebase-runtime-bin-kde4 depends on kdebase-runtime (>= 4:4.3.5); however:
  Package kdebase-runtime is not configured yet.
 kdebase-runtime-bin-kde4 depends on kdelibs5 (>= 4:4.3.5); however:
  Package kdelibs5 is not configured yet.
 kdebase-runtime-bin-kde4 depends on libqt4-svg (>= 4.5.1); however:
  Package libqt4-svg is not configured yet.
dpkg: error processing kdebase-runtime-bin-kde4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqt4-svg
 libclucene0ldbl
 libsoprano4
 soprano-daemon
 libexiv2-5
 libstreams0
 libstreamanalyzer0
 kdelibs5-data
 kdelibs5
 kdelibs-bin
 exiv2
 libknotificationitem1
 libqt4-opengl
 libqt4-webkit
 libplasma3
 libxine1-bin
 libxine1-misc-plugins
 libxcb-shape0
 libxcb-shm0
 libxcb-xv0
 libxine1-x
 libxine1-console
 libxine1
 phonon-backend-xine
 kdebase-runtime
 kdebase-runtime-bin-kde4
E: Sub-process /usr/bin/dpkg returned an error code (1)
nkbatsi@kavourdistiri:~$ 

[SIZE="2"]can somebody help me. my hands are tied up with synaptic and apt-get not running

there' also info about this problem  at this thread:
 
[http://ubuntuforums.org/showthread.php?t=1426627](http://ubuntuforums.org/showthread.php?t=1426627)[/SIZE]

---

