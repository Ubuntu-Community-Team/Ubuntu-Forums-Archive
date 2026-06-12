---
title: "Dependency problems"
date: 2011-09-29
forum: General Help
---

### Post by ki4jgt on 2011-09-29
> jesse@Remember:~$ sudo aptitude install python3
[sudo] password for jesse: 
Sorry, try again.
[sudo] password for jesse: 
The following NEW packages will be installed:
  libdb5.1{a} python3 python3-minimal{a} python3.2{a} python3.2-minimal{a} 
The following partially installed packages will be configured:
  brasero empathy eog evince evolution evolution-exchange 
  gnome-control-center gnome-icon-theme gnome-screensaver totem 
  totem-mozilla totem-plugins ubuntu-desktop 
0 packages upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 6,264 kB of archives. After unpacking 21.4 MB will be used.
Do you want to continue? [Y/n/?] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libdb5.1 i386 5.1.19-2ubuntu1 [682 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main python3.2-minimal i386 3.2-1ubuntu1 [1,709 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main python3.2 i386 3.2-1ubuntu1 [3,828 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main python3-minimal all 3.2-1ubuntu1 [12.1 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main python3 all 3.2-1ubuntu1 [33.1 kB]
Fetched 6,264 kB in 1min 7s (92.6 kB/s)                                         
Selecting previously deselected package libdb5.1.
(Reading database ... 241341 files and directories currently installed.)
Unpacking libdb5.1 (from .../libdb5.1_5.1.19-2ubuntu1_i386.deb) ...
Selecting previously deselected package python3.2-minimal.
Unpacking python3.2-minimal (from .../python3.2-minimal_3.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package python3.2.
Unpacking python3.2 (from .../python3.2_3.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package python3-minimal.
Unpacking python3-minimal (from .../python3-minimal_3.2-1ubuntu1_all.deb) ...
Selecting previously deselected package python3.
Unpacking python3 (from .../python3_3.2-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfiguNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because the error message indicates its a followup error from a previous failure.
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                    red
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up libdb5.1 (5.1.19-2ubuntu1) ...
Setting up python3.2-minimal (3.2-1ubuntu1) ...
Setting up python3.2 (3.2-1ubuntu1) ...
Setting up python3-minimal (3.2-1ubuntu1) ...
Setting up python3 (3.2-1ubuntu1) ...
running python rtupdate hooks for python3.2...
running python post-rtupdate hooks for python3.2...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 gnome-icon-theme
 brasero
 empathy
 eog
 evince
 evolution
 evolution-exchange
 gnome-control-center
 gnome-screensaver
 totem
 totem-mozilla
 totem-plugins
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 evince
 ubuntu-desktop
 evolution
 gnome-screensaver
 empathy
 eog
 brasero
 totem
 totem-mozilla
 gnome-control-center
 evolution-exchange
 totem-plugins
                                         
jesse@Remember:~$

Anyone have any suggestions?

---

### Post by raja.genupula on 2011-09-29
Have tried to install from software center or Synaptic package manager.?

---

### Post by Bucky Ball on 2011-09-29
Try:

```
sudo apt-get update
sudo apt-get upgrade
```(that will upgrade packages, *not* release.)

Then perhaps ...

```
sudo apt-get install brasero empathy eog evince evolution evolution-exchange 
  gnome-control-center gnome-icon-theme gnome-screensaver totem 
  totem-mozilla totem-plugins ubuntu-desktop
```... if you actually want those apps, then try again. As last user said, have you looked in Synaptics for broken packages? It is wanting to install ubuntu-desktop. What stage are you actually at? Are you running a desktop or terminal?

---

### Post by ki4jgt on 2011-09-29
No broken packages. I've upgraded numerous times before posting this.

> jesse@Remember:~$ sudo apt-get install brasero empathy eog evince evolution evolution-exchange 
[sudo] password for jesse: 
Sorry, try again.
[sudo] password for jesse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
brasero is already the newest version.
eog is already the newest version.
evolution is already the newest version.
evolution-exchange is already the newest version.
empathy is already the newest version.
evince is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfiguNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        red
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 brasero
 empathy
 eog
 evince
 evolution
 evolution-exchange
 gnome-control-center
 gnome-screensaver
 totem
 totem-mozilla
 totem-plugins
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
jesse@Remember:~$

---

### Post by seawolf167 on 2011-09-30
Try

```
sudo dpkg --configure --pending
```

or if that doesn't work

```
sudo apt-get install -f
```

---

### Post by ki4jgt on 2011-10-01
> **seawolf167 said:**
> Try

```
sudo dpkg --configure --pending
```

or if that doesn't work

```
sudo apt-get install -f
```

Tried both.

> sudo dpkg --configure --pendingjesse@Remember:~$ sudo dpkg --configure --pending
[sudo] password for jesse: 
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 evince
 ubuntu-desktop
 evolution
 gnome-screensaver
 empathy
 eog
 brasero
 totem
 totem-mozilla
 gnome-control-center
 evolution-exchange
 totem-plugins
jesse@Remember:~$ 

> jesse@Remember:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfiguNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        red
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 brasero
 empathy
 eog
 evince
 evolution
 evolution-exchange
 gnome-control-center
 gnome-screensaver
 totem
 totem-mozilla
 totem-plugins
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
jesse@Remember:~$ 


---

### Post by Old_Grey_Wolf on 2011-10-01
Enter this command then do an update
```
sudo apt-get install gnome-icon-theme
```

---

### Post by ki4jgt on 2011-10-02
> **Old_Gray_Wolf said:**
> Enter this command then do an update
```
sudo apt-get install gnome-icon-theme
```

> jesse@Remember:~$ sudo apt-get install gnome-icon-theme
[sudo] password for jesse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-icon-theme is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfiguNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        red
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 brasero
 empathy
 eog
 evince
 evolution
 evolution-exchange
 gnome-control-center
 gnome-screensaver
 totem
 totem-mozilla
 totem-plugins
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
jesse@Remember:~$ 


Same thing. It started to install this time though but then just didn't want to any longer.

---

### Post by QLee on 2011-10-02
ki4jgt,
If I were you I would pay special attention to this part of the error message:
> Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2

As you can see from reading through the rest of the message, the errors cascade because of that initial error, ultimately it is because of that failure that the rest of the packages can't be configured.

Were you trying to do something with that graphic? Is there a file named that in that location? Offhand, I don't know which package carries that logo and I am on a Squeeze system right now. If the file is missing, don't worry, someone here will remember which package provides that graphic, I would guess that it will have Ubuntu somewhere in the name. :-)

---

### Post by Old_Grey_Wolf on 2011-10-02
> **QLee said:**
> If the file is missing, don't worry, someone here will remember which package provides that graphic, I would guess that it will have Ubuntu somewhere in the name. :-)

The Ubuntu Logo .svg file can be downloaded from here [http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg](http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg)

Then put the file in /usr/share/icons/gnome/scalable/places/

sudo apt-get -f install
should reconfigure the latest packages

---

### Post by ki4jgt on 2011-10-02
> **QLee said:**
> ki4jgt,
If I were you I would pay special attention to this part of the error message:


As you can see from reading through the rest of the message, the errors cascade because of that initial error, ultimately it is because of that failure that the rest of the packages can't be configured.

Were you trying to do something with that graphic? Is there a file named that in that location? Offhand, I don't know which package carries that logo and I am on a Squeeze system right now. If the file is missing, don't worry, someone here will remember which package provides that graphic, I would guess that it will have Ubuntu somewhere in the name. :-)

I install gnome-shell. Then, after countless bugs, completely removed gnome, removed the repositories for it, and then reinstalled gnome2

---

### Post by Old_Grey_Wolf on 2011-10-02
> **ki4jgt said:**
> I install gnome-shell. Then, after countless bugs, completely removed gnome, removed the repositories for it, and then reinstalled gnome2

Just as I thought. Use my previous post about fixing the svg file. That should fix it for you.

---

### Post by ki4jgt on 2011-10-03
> **Old_Gray_Wolf said:**
> The Ubuntu Logo .svg file can be downloaded from here [http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg](http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg)

Then put the file in /usr/share/icons/gnome/scalable/places/

sudo apt-get -f install
should reconfigure the latest packages

> jesse@Remember:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up gnome-icon-theme (2.31.0-0ubuntu2) ...
update-alternatives: using /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg to provide /usr/share/icons/gnome/scalable/places/start-here.svg (start-here.svg) in auto mode.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/16x16/places/start-here.png because associated file /usr/share/icons/gnome/16x16/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/22x22/places/start-here.png because associated file /usr/share/icons/gnome/22x22/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/24x24/places/start-here.png because associated file /usr/share/icons/gnome/24x24/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/256x256/places/start-here.png because associated file /usr/share/icons/gnome/256x256/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/32x32/places/start-here.png because associated file /usr/share/icons/gnome/32x32/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/48x48/places/start-here.png because associated file /usr/share/icons/gnome/48x48/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: error: alternative path /usr/share/icons/gnome/scalable/places/debian-swirl.svg doesn't exist.
dpkg: error processing gnome-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of brasero:
 brasero depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing brasero (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on gnome-icon-theme (>= 2.30.0); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on gnome-icon-theme (>= 2.19.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on gnome-icon-theme (>= 2.17.1); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfiguNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        red
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gnome-icon-theme (>= 2.19.92); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.32.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.33.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem:
 totem depends on gnome-icon-theme (>= 2.15.90); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on totem (= 2.32.0-0ubuntu10); however:
  Package totem is not configured yet.
dpkg: error processing totem-pNo apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    lugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-icon-theme; however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-icon-theme
 brasero
 empathy
 eog
 evince
 evolution
 evolution-exchange
 gnome-control-center
 gnome-screensaver
 totem
 totem-mozilla
 totem-plugins
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
jesse@Remember:~$ 

Yay, error destroyed :-) Now for the next one :-(

---

### Post by satyanash on 2011-10-08
Hi, Same problem here.
IF you fix debian-swirl.svg in the same way, it asks for gnome-foot.svg.
I stopped there, will be doing a full reinstall anyway.
But will wait till I backup all my stuff.
Hopefully a solution will be found.
Satyajeet

---

### Post by satyanash on 2011-10-08
Hi,
Found a Solution!

Follow the steps on this link!
[http://joshua.doodnauth.com/blog/tag/gnome-icon-theme/](http://joshua.doodnauth.com/blog/tag/gnome-icon-theme/)

It Worked for me!
Download:

**ubuntu-logo.svg** (from [http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg](http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg))

**gnome-foot.svg**,**debian-swirl.svg** and **swirl-foot.svg** from [http://www.parsix.org/browser/pkg/vinnie/main/gnome-icon-theme/trunk/debian?rev=6662](http://www.parsix.org/browser/pkg/vinnie/main/gnome-icon-theme/trunk/debian?rev=6662)

Put all SVGs in 
```
/usr/share/icons/gnome/scalable/places/
```

then 
```

sudo apt-get clean all
sudo apt-get update
sudo apt-get -f install

```

Satyajeet

---

### Post by Th1cKA on 2011-10-12
> **sattu94 said:**
> Hi,
Found a Solution!

Follow the steps on this link!
[http://joshua.doodnauth.com/blog/tag/gnome-icon-theme/](http://joshua.doodnauth.com/blog/tag/gnome-icon-theme/)

It Worked for me!
Download:

**ubuntu-logo.svg** (from [http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg](http://en.wikipedia.org/wiki/File:Ubuntu_logo.svg))

**gnome-foot.svg**,**debian-swirl.svg** and **swirl-foot.svg** from [http://www.parsix.org/browser/pkg/vinnie/main/gnome-icon-theme/trunk/debian?rev=6662](http://www.parsix.org/browser/pkg/vinnie/main/gnome-icon-theme/trunk/debian?rev=6662)

Put all SVGs in 
```
/usr/share/icons/gnome/scalable/places/
```

then 
```

sudo apt-get clean all
sudo apt-get update
sudo apt-get -f install

```

Satyajeet

Working. Thank you :)

---

