---
title: "Cannot open Ubuntu Software Center and Update Manager. (Python Errors)"
date: 2011-11-05
forum: General Help
---

### Post by Rhosta on 2011-11-05
Hi, I have the problem with Ubuntu Software Center and Update Manager.

After the last update with update manager which required restart, I cant open Ubuntu software manager (it tries to open but then nothing happens) and update manager (completely nothing).

I am using Ubuntu 11.10 installed with Wubi.

I've tried these three steps:
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

"sudo apt-get upgrade" returns this after confirmation:
```

Setting up python-gobject (3.0.0-0ubuntu4) ...
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing python-gobject (--configure):
 subprocess installed post-installation script returned error exit status 101
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-gobject (>= 2.29.3); however:
  Package python-gobject is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python-gobject (>= 2.28); however:
  Package python-gobject is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-appindicator:
 python-appindicator depends on python-gobject; however:
  Package python-gobject is not configured yet.
dpkg: error processing python-appindicator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gconf:
 python-gconf depends on python-gobject (>= 2.17.0); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-gconf (--coNo apport report written because the error message indicates its a followup error from a previous failure.
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
                                                                         No apport report written because MaxReports is reached already
                                                       nfigure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-gobject (>= 2.21.3); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gmenu:
 python-gmenu depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-gmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomekeyring:
 python-gnomekeyring depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-gnomekeyring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gst0.10:
 python-gst0.10 depends on python-gobject (>= 2.11.2); however:
  Package python-gobject is No apport report written because MaxReports is reached already
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
                                                                      No apport report written because MaxReports is reached already
                                                    not configured yet.
dpkg: error processing python-gst0.10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ibus:
 python-ibus depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-ibus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-indicate:
 python-indicate depends on python-gobject; however:
  Package python-gobject is not configured yet.
dpkg: error processing python-indicate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-notify:
 python-notify depends on python-gtk2 (>= 2.10); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-farsight:
 python-farsight depends on python-gst0No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   .10; however:
  Package python-gst0.10 is not configured yet.
dpkg: error processing python-farsight (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-papyon:
 python-papyon depends on python-gobject (>= 2.10); however:
  Package python-gobject is not configured yet.
 python-papyon depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
 python-papyon depends on python-farsight; however:
  Package python-farsight is not configured yet.
dpkg: error processing python-papyon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pyatspi2:
 python-pyatspi2 depends on python-gobject (>= 2.90.1); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-pyatspi2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-ubuntuone-client:
 python-ubuntuone-client depends on python-notify; however:
  Package python-notify is not configured yet.
dpkg: error processing python-ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-vte:
 python-vte depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-vte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-webkit:
 python-webkit depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-webkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-wnck:
 python-wnck depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-wnck (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python-gobject; however:
  Package python-gobject is not configured yet.
dpkg: error processing python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
 python-aptdaemon.gtk3widgets depends on python-gobject (>= 2.27.91); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oneconf:
 oneconf depends on python-gobject; however:
  Package python-gobject is not configured yet.
 oneconf depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing oneconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on python-gobject (>= 2.90); however:
  Package python-gobject is not configured yet.
 software-center depends on python-aptdaemon (>= 0.40); however:
  Package python-aptdaemon is not configured yet.
 software-center depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
 software-center depends on oneconf (>= 0.2.6); however:
  Package oneconf is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
 system-config-printer-gnome depends on python-notify; however:
  Package python-notify is not configured yet.
 system-config-printer-gnome depends on python-gobject; however:
  Package python-gobject is not configured yet.
 system-config-printer-gnome depends on python-gnomekeyring; however:
  Package python-gnomekeyring is not configured yet.
dpkg: error processing system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python-gobject (>= 2.28.6-2); however:
  Package python-gobject is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtkwidgets:
 python-aptdaemon.gtkwidgets depends on python-aptdaemon (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
 python-aptdaemon.gtkwidgets depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
 python-aptdaemon.gtkwidgets depends on python-vte; however:
  Package python-vte is not configured yet.
dpkg: error processing python-aptdaemon.gtkwidgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gobject
 apport-gtk
 gedit
 python-appindicator
 python-gconf
 python-gtk2
 python-gmenu
 python-gnomekeyring
 python-gst0.10
 python-ibus
 python-indicate
 python-notify
 python-farsight
 python-papyon
 python-pyatspi2
 python-ubuntuone-client
 python-vte
 python-webkit
 python-wnck
 python-aptdaemon
 python-aptdaemon.gtk3widgets
 oneconf
 software-center
 system-config-printer-gnome
 update-manager
 update-notifier
 python-aptdaemon.gtkwidgets
 python-aptdaemon-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by kadama on 2012-01-01
I have the same problem

---

### Post by yugnip on 2012-01-01
you could try:

```
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade
sudo dpkg --configure --pending

```

---

### Post by kadama on 2012-01-02
As the message says "Package python-gobject is not configured yet." I started the Synaptic Package Manager from terminal using the command gksudo synaptic &. Then I reinstalled python-gobject. That affected the Unity Dash line.  I followed the instructions in the link below to solve the Dash problem

[http://ubuntuforums.org/showthread.php?t=1742741&highlight=search+option+unity+dash+results](http://ubuntuforums.org/showthread.php?t=1742741&highlight=search+option+unity+dash+results)

You might have to reinstall the other applications which are affected by python. A tedious task but it worked for me

---

