---
title: "Fix theses errors."
date: 2010-05-05
forum: General Help
---

### Post by charles_shipp on 2010-05-05
Every time I update my systems I get these errors.
E:nautilus:dependency problems-leaving unconfigured 
E:gnome-settings-daemon:dependency problems-leaving unconfigured
E:libgnome-window-settings1:dependency problems-leaving unconfigured
E:gnome-control-center:dependency problems-leaving unconfigured
E:compiz-gnome:dependency problems-leaving unconfigured
E:gnome-panel:dependency problems-leaving unconfigured
E:gnome-session:dependency problems-leaving unconfigured
E:gnome-applets:dependency problems-leaving unconfigured
E:compiz:dependency problems-leaving unconfigured
E:eog:dependency problems-leaving unconfigured
E:evolution:dependency problems-leaving unconfigured
E:evolution-couchdb:dependency problems-leaving unconfigured
E:evolution-exchange:dependency problems-leaving unconfigured
E:evolution-plugins:dependency problems-leaving unconfigured
E:gnome-screensaver:dependency problems-leaving unconfigured
E:indicator-applet:dependency problems-leaving unconfigured
E:indicator-applet-session:dependency problems-leaving unconfigured
E:nautilus-share:dependency problems-leaving unconfigured
E:python-gnomedesktop:dependency problems-leaving unconfigured
E:python-gnome2-desktop:dependency problems-leaving unconfigured
E:ubuntu-desktop:dependency problems-leaving unconfigured
E:evolution-indicator:dependency problems-leaving unconfigured

---

### Post by philinux on 2010-05-05
What does this do? Any errors?

```
sudo dpkg --configure -a
```

---

### Post by _0R10N on 2010-05-05
what command are you running when this happens?

You may take a look a this thread
[http://ubuntuforums.org/showthread.php?p=4201560](http://ubuntuforums.org/showthread.php?p=4201560)

Kind regards!

---

### Post by charles_shipp on 2010-05-17
E: libgnome-desktop-2-17: subprocess installed post-installation script returned error exit status 2
E: nautilus: dependency problems - leaving unconfigured
E: gnome-settings-daemon: dependency problems - leaving unconfigured
E: libgnome-window-settings1: dependency problems - leaving unconfigured
E: compiz-gnome: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: compiz: dependency problems - leaving unconfigured
E: eog: dependency problems - leaving unconfigured
E: evolution: dependency problems - leaving unconfigured
E: evolution-couchdb: dependency problems - leaving unconfigured
E: evolution-exchange: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gnome-screensaver: dependency problems - leaving unconfigured
E: indicator-applet: dependency problems - leaving unconfigured
E: indicator-applet-session: dependency problems - leaving unconfigured
E: nautilus-share: dependency problems - leaving unconfigured
E: python-gnomedesktop: dependency problems - leaving unconfigured
E: python-gnome2-desktop: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: evolution-indicator: dependency problems - leaving unconfigured

---

### Post by jubilee33 on 2010-05-17
> **charles_shipp said:**
> E: libgnome-desktop-2-17: subprocess installed post-installation script returned error exit status 2
E: nautilus: dependency problems - leaving unconfigured
E: gnome-settings-daemon: dependency problems - leaving unconfigured
E: libgnome-window-settings1: dependency problems - leaving unconfigured
E: compiz-gnome: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: compiz: dependency problems - leaving unconfigured
E: eog: dependency problems - leaving unconfigured
E: evolution: dependency problems - leaving unconfigured
E: evolution-couchdb: dependency problems - leaving unconfigured
E: evolution-exchange: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gnome-screensaver: dependency problems - leaving unconfigured
E: indicator-applet: dependency problems - leaving unconfigured
E: indicator-applet-session: dependency problems - leaving unconfigured
E: nautilus-share: dependency problems - leaving unconfigured
E: python-gnomedesktop: dependency problems - leaving unconfigured
E: python-gnome2-desktop: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: evolution-indicator: dependency problems - leaving unconfigured

What were you trying to install?  Which system are you using currently?

---

### Post by charles_shipp on 2010-05-17
I'm on 10.4 I just started getting
 those erros whin i upgraded

---

### Post by jubilee33 on 2010-05-17
> **charles_shipp said:**
> I'm on 10.4 I just started getting
 those erros whin i upgraded

You mean when you upgraded from a previous ubuntu system to 10.04?  What system were you using before?  Karmic?  I usually do a clean install.  How did you upgrade?

---

### Post by charles_shipp on 2010-05-17
Threads merged.

---

### Post by Soul-Sing on 2010-05-17
charles_shipp could you tell us some background info bout these errors?
- did you perform an upgrade
- did you install/remove certain software

what is the exact outcome of:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```


copy/paste the results

---

### Post by charles_shipp on 2010-05-17
Setting up libgnome-desktop-2-17 (1:2.30.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgnome-desktop-2-17 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-1No apport report written because the error message indicates its a followup error from a previous failure.
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
                                                              7 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 compiz-gnome depends on libgnome-window-settings1 (>= 1:2.17.5); however:
  Package libgnome-window-settings1 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 gnome-control-center depends on libgnome-window-settings1 (= 1:2.30.1-0ubuntu1); however:
  Package libgnome-window-settings1 is not configured yet.
 gnome-control-center depends on gnome-settings-daemon (>= 2.26); however:
  Package gnome-settiNo apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 ngs-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-settings-daemon (>= 2.26); however:
  Package gnome-settings-daemon is not configured yet.
 gnome-session depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 gnome-session depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome | compiz-kde; however:
  Package compiz-gnome is not configured yet.
  Package compiz-kde is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on evolution (>= 2.28.3); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.28.2); however:
  Package evolution is not configured yet.
 evolution-exchange depends on evolution (<< 2.29.0); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.28.3); however:
  Package evolution is not configured yet.
 evolution-plugins depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-screensaver:
 gnome-screensaver depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing gnome-screensaver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet:
 indicator-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing indicator-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet-session:
 indicator-applet-session depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 indicator-applet-session depends on indicator-applet (= 0.3.7-0ubuntu1); however:
  Package indicator-applet is not configured yet.
dpkg: error processing indicator-applet-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomedesktop:
 python-gnomedesktop depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
dpkg: error processing python-gnomedesktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-gnomedesktop (>= 2.30.0-0ubuntu1); however:
  Package python-gnomedesktop is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 ubuntu-desktop depends on gnome-session; however:
  Package gnome-session is not configured yet.
 ubuntu-desktop depends on indicator-applet-session; however:
  Package indicator-applet-session is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-indicator:
 evolution-indicator depends on evolution (>= 2.28.3); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-indicator (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnome-desktop-2-17
 nautilus
 gnome-settings-daemon
 libgnome-window-settings1
 compiz-gnome
 gnome-control-center
 gnome-panel
 gnome-session
 gnome-applets
 compiz
 eog
 evolution
 evolution-couchdb
 evolution-exchange
 evolution-plugins
 gnome-screensaver
 indicator-applet
 indicator-applet-session
 nautilus-share
 python-gnomedesktop
 python-gnome2-desktop
 ubuntu-desktop
 evolution-indicator
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philinux on 2010-05-17
Try this but don't hit the Y key just paste back what it says.

```
sudo apt-get dist-upgrade
```

---

### Post by charles_shipp on 2010-05-17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
23 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 

I stared with Jaunty Jachalope then upgraded to Karmic Kola now I've got 10.4 I don't remeber if i did the clean install.

---

