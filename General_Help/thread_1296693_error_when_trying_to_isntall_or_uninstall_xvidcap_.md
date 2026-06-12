---
title: "error when trying to isntall or uninstall xvidcap or any other program"
date: 2009-10-20
forum: General Help
---

### Post by BAMF1501 on 2009-10-20
i get this error

 installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 154510 files and directories currently installed.) 
Removing xvidcap ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Setting up libmp3lame0 (3.98.2+debian-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmp3lame0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libxvidcore4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of avidemux-plugins: 
 avidemux-plugins depends on libmp3lame0; however: 
  Package libmp3lame0 is not configured yet. 
 avidemux-plugins depends on libxvidcore4 (>= 1:1.0.0-0.0); however: 
  Package libxvidcore4 is not configured yet. 
dpkg: error processing avidemux-plugins (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of avidemux: 
 avidemux depends on avidemux-plugins; however: 
  Package avidemux-plugins is not configured yet. 
dpkg: error processing avidemux (--configure): 
 dependency problems - leaving unconfigured 
Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing imagemagick (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of lame: 
 lame depends on libmp3lame0; however: 
  Package libmp3lame0 is not configured yet. 
dpkg: error processing lame (--configure): 
 dependency problems - leaving unconfigured 
Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libavutil-extra-49 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdirac0c2a (1.0.2-0ubuntu1) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdirac0c2a (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libopenjpeg2 (1.3+dfsg-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libopenjpeg2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libavcodec-extra-52: 
 libavcodec-extra-52 depends on libavutil-extra-49 (>= 4:0.5+svn20090706); however: 
  Package libavutil-extra-49 is not configured yet. 
 libavcodec-extra-52 depends on libavutil-extra-49 (<< 4:0.5+svn20090706-99); however: 
  Package libavutil-extra-49 is not configured yet. 
 libavcodec-extra-52 depends on libdirac0c2a; however: 
  Package libdirac0c2a is not configured yet. 
 libavcodec-extra-52 depends on libmp3lame0; however: 
  Package libmp3lame0 is not configured yet. 
 libavcodec-extra-52 depends on libopenjpeg2; however: 
  Package libopenjpeg2 is not configured yet. 
 libavcodec-extra-52 depends on libxvidcore4 (>= 1:1.0.0-0.0); however: 
  Package libxvidcore4 is not configured yet. 
dpkg: error processing lNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ibavcodec-extra-52 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mplayer-nogui: 
 mplayer-nogui depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however: 
  Package libavcodec52 is not installed. 
  Package libavcodec-extra-52 is not configured yet. 
 mplayer-nogui depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however: 
  Package libavutil49 is not installed. 
  Package libavutil-extra-49 is not configured yet. 
 mplayer-nogui depends on libmp3lame0; however: 
  Package libmp3lame0 is not configured yet. 
 mplayer-nogui depends on libxvidcore4 (>= 1:1.0.0-0.0); however: 
  Package libxvidcore4 is not configured yet. 
dpkg: error processing mplayer-nogui (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mplayer: 
 mplayer depends on mplayer-nogui; however: 
  Package mplayer-nogui is not configured yet. 
 mplayer depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however: 
  Package libavcodec52 is not installed. 
  Package libavcodec-extra-52 is not configured yet. 
 mplayer depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however: 
  Package libavutil49 is not installed. 
  Package libavutil-extra-49 is not configured yet. 
 mplayer depends on libmp3lame0; however: 
  Package libmp3lame0 is not configured yet. 
 mplayer depends on libxvidcore4 (>= 1:1.0.0-0.0); however: 
  Package libxvidcore4 is not configured yet. 
dpkg: error processing mplayer (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 libmp3lame0

---

### Post by lidex on 2009-10-21
Two commands you can try in this order are:
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by BAMF1501 on 2009-10-21
i typed in those 2 commands and get this 

epic1501@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for epic1501: 
Setting up libdirac0c2a (1.0.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdirac0c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libavutil-extra-49 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenjpeg2 (1.3+dfsg-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenjpeg2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxvidcore4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmp3lame0 (3.98.2+debian-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmp3lame0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing imagemagick (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is not configured yet.
 mplayer depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 mplayer depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing mplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lame:
 lame depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
dpkg: error processing lame (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avidemux-plugins:
 avidemux-plugins depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 avidemux-plugins depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing avidemux-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavcodec-extra-52:
 libavcodec-extra-52 depends on libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil-extra-49 is not configured yet.
 libavcodec-extra-52 depends on libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil-extra-49 is not configured yet.
 libavcodec-extra-52 depends on libdirac0c2a; however:
  Package libdirac0c2a is not configured yet.
 libavcodec-extra-52 depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 libavcodec-extra-52 depends on libopenjpeg2; however:
  Package libopenjpeg2 is not configured yet.
 libavcodec-extra-52 depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing libavcodec-extra-52 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-nogui:
 mplayer-nogui depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not installed.
  Package libavcodec-extra-52 is not configured yet.
 mplayer-nogui depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is not configured yet.
 mplayer-nogui depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 mplayer-nogui depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing mplayer-nogui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avidemux:
 avidemux depends on avidemux-plugins; however:
  Package avidemux-plugins is not configured yet.
dpkg: error processing avidemux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdirac0c2a
 libavutil-extra-49
 libopenjpeg2
 libxvidcore4
 libmp3lame0
 imagemagick
 mplayer
 lame
 avidemux-plugins
 libavcodec-extra-52
 mplayer-nogui
 avidemux
epic1501@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  binutils-static policykit
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libmp3lame0 (3.98.2+debian-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmp3lame0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxvidcore4 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of avidemux-plugins:
 avidemux-plugins depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 avidemux-plugins depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing avidemux-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avidemux:
 avidemux depends on avidemux-plugins; however:
  Package avidemux-plugins is not configured yet.
dpkg: error processing avidemux (--configure):
 dependency problems - leaving unconfigured
Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing imagemagick (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of lame:
 lame depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
dpkg: error processing lame (--configure):
 dependency problems - leaving unconfigured
Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libavutil-extra-49 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up libdirac0c2a (1.0.2-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdirac0c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenjpeg2 (1.3+dfsg-4) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenjpeg2 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libavcodec-extra-52:
 libavcodec-extra-52 depends on libavutil-extra-49 (>= 4:0.5+svn20090706); however:
  Package libavutil-extra-49 is not configured yet.
 libavcodec-extra-52 depends on libavutil-extra-49 (<< 4:0.5+svn20090706-99); however:
  Package libavutil-extra-49 is not configured yet.
 libavcodec-extra-52 depends on libdirac0c2a; however:
  Package libdirac0c2a is not configured yet.
 libavcodec-extra-52 depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 libavcodec-extra-52 depends on libopenjpeg2; however:
  Package libopenjpeg2 is not configured yet.
 libavcodec-extra-52 depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing lNo apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                ibavcodec-extra-52 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer-nogui:
 mplayer-nogui depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not installed.
  Package libavcodec-extra-52 is not configured yet.
 mplayer-nogui depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is not configured yet.
 mplayer-nogui depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 mplayer-nogui depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing mplayer-nogui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on mplayer-nogui; however:
  Package mplayer-nogui is not configured yet.
 mplayer depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not installed.
  Package libavcodec-extra-52 is not configured yet.
 mplayer depends on libavutil49 (>= 3:0.svn20090303-1) | libavutil-extra-49 (>= 3:0.svn20090303-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is not configured yet.
 mplayer depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 mplayer depends on libxvidcore4 (>= 1:1.0.0-0.0); however:
  Package libxvidcore4 is not configured yet.
dpkg: error processing mplayer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmp3lame0
 libxvidcore4
 avidemux-plugins
 avidemux
 imagemagick
 lame
 libavutil-extra-49
 libdirac0c2a
 libopenjpeg2
 libavcodec-extra-52
 mplayer-nogui
 mplayer
E: Sub-process /usr/bin/dpkg returned an error code (1)
epic1501@ubuntu:~$

---

### Post by BAMF1501 on 2009-10-21
bump

---

### Post by lidex on 2009-10-21
These packages seem to be problematic:
```
libdirac0c2a
libavutil-extra-49
libopenjpeg2
libxvidcore4
libmp3lame0
imagemagick
mplayer
lame
avidemux-plugins
libavcodec-extra-52
mplayer-nogui
avidemux
```

Starting with the first one run the command ```
sudo dpkg --configure -a
``` replacing "-a" with the package name. One at a time please. If reports not installed then:```
sudo apt-get install packagename
```

---

