---
title: "Software Center and Synaptic Problems"
date: 2010-09-05
forum: General Help
---

### Post by Speedcuber on 2010-09-05
Hi,

I am encountering some glitches with Ubuntu Software Center and Synaptic. Whenever I go to install or uninstall anything using either of these programs, I get an error message: "Package operation failed"

Here is the contents of the details box when I just tried to install a game with the Software Center:

```
installArchives() failed: Selecting previously deselected package trigger-rally. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 190487 files and directories currently installed.) 
Unpacking trigger-rally (from .../trigger-rally_0.5.2.1-1_i386.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for menu ... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libqt3-mt (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libavahi-qt3-1: 
 libavahi-qt3-1 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libavahi-qt3-1 (--configure): 
 dependency problems - leaving unconfigured 
Setting up liblua50 (5.0.3-4) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblua50 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of liblualib50: 
 liblualib50 depends on liblua50 (>= 5.0.3); however: 
  Package liblua50 is not configured yet. 
dpkg: error processing liblualib50 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kdelibs4c2a: 
 kdelibs4c2a depends on libavahi-qt3-1 (>= 0.6.16); however: 
  Package libavahi-qt3-1 is not configured yet. 
 kdelibs4c2a depends on liblua50 (>= 5.0.3); however: 
  Package liblua50 is not configured yet. 
 kdelibs4c2a depends on liblualib50 (>= 5.0.3); however: 
  Package liblualib50 is not configured yet. 
 kdelibs4c2a depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kdelibs4c2a (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kfilereplace-kde3: 
 kfilereplace-kde3 depends on kdelibs4c2a (>= 4:3.5.9); however: 
  Package kdelibs4c2a is not configured yet. 
 kfiNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
lereplace-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kfilereplace-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of klinkstatus-kde3: 
 klinkstatus-kde3 depends on kdelibs4c2a (>= 4:3.5.9); however: 
  Package kdelibs4c2a is not configured yet. 
 klinkstatus-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing klinkstatus-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kommander-kde3: 
 kommander-kde3 depends on kdelibs4c2a (>= 4:3.5.9); however: 
  Package kdelibs4c2a is not configured yet. 
 kommander-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kommander-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libqbanking8: 
 libqbanking8 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libqbanking8 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libaqbanking29-plugins-qt: 
 libaqbanking29-plugins-qt depends on libqbanking8; however: 
  Package libqbanking8 is not configured yet. 
 libaqbanking29-plugins-qt depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libaqbanking29-plugins-qt (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of quanta: 
 quanta depends on kdelibs4c2a (>= 4:3.5.9); however: 
  Package kdelibs4c2a is not configured yet. 
 quanta depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
 quanta depends on kfilereplace-kde3 (= 4:3.5.10-0ubuntu4); however: 
  Package kfilereplace-kde3 is not configured yet. 
 quanta depends on klinkstatus-kde3 (= 4:3.5.10-0ubuntu4); however: 
  Package klinkstatus-kde3 is not configured yet. 
 quanta depends on kommander-kde3 (= 4:3.5.10-0ubuntu4); however: 
  Package kommander-kde3 is not configured yet. 
dpkg: error processing quanta (--configure): 
 dependency problems - leaving unconfigured 
Setting up trigger-rally (0.5.2.1-1) ... 
 
Processing triggers for menu ... 
Errors were encountered while processing: 
 libqt3-mt 
 libavahi-qt3-1 
 liblua50 
 liblualib50 
 kdelibs4c2a 
 kfilereplace-kde3 
 klinkstatus-kde3 
 kommander-kde3 
 libqbanking8 
 libaqbanking29-plugins-qt 
 quanta 
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libqt3-mt (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up liblua50 (5.0.3-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblua50 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of klinkstatus-kde3: 
 klinkstatus-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing klinkstatus-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libavahi-qt3-1: 
 libavahi-qt3-1 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libavahi-qt3-1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of quanta: 
 quanta depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
 quanta depends on klinkstatus-kde3 (= 4:3.5.10-0ubuntu4); however: 
  Package klinkstatus-kde3 is not configured yet. 
dpkg: error processing quanta (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liblualib50: 
 liblualib50 depends on liblua50 (>= 5.0.3); however: 
  Package liblua50 is not configured yet. 
dpkg: error processing liblualib50 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libaqbanking29-plugins-qt: 
 libaqbanking29-plugins-qt depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libaqbanking29-plugins-qt (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kfilereplace-kde3: 
 kfilereplace-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kfilereplace-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kommander-kde3: 
 kommander-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kommander-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kdelibs4c2a: 
 kdelibs4c2a depends on libavahi-qt3-1 (>= 0.6.16); however: 
  Package libavahi-qt3-1 is not configured yet. 
 kdelibs4c2a depends on liblua50 (>= 5.0.3); however: 
  Package liblua50 is not configured yet. 
 kdelibs4c2a depends on liblualib50 (>= 5.0.3); however: 
  Package liblualib50 is not configured yet. 
 kdelibs4c2a depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kdelibs4c2a (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libqbanking8: 
 libqbanking8 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libqbanking8 (--configure): 
 dependency problems - leaving unconfigured 

```

The unusual thing is, despite this message, often the installation works fine, and I can use the program I installed fine. Sometimes, however, this is not the case, and the program is all glitchy or does not show up as installed.

When uninstalling, however, I have much less success and I am having great trouble uninstalling anything from my computer. I almost never works.



I have reinstalled Ubuntu Software Center several times (using Synaptic, and I still get the error messages while doing this).

Thanks.

---

### Post by Speedcuber on 2010-09-05
In case it helps, here is a thread about the topic I made a few months ago. It remained unanswered, so I tried to ignore the problem, but I'm afraid it is getting really annoying.

[http://ubuntuforums.org/showthread.php?t=1533342](http://ubuntuforums.org/showthread.php?t=1533342)


Also, perhaps Quanta has something to do with it? This was the program I was trying to install when the problem first occurred, and I see it shows up in the error details box above, even though the program I was installing has nothing to do with Quanta.

---

