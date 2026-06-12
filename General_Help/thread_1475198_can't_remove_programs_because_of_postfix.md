---
title: "can't remove programs because of postfix"
date: 2010-05-06
forum: General Help
---

### Post by xjgnsdof on 2010-05-06
I get this when I try to uninstall anything (Synaptic, Software Store, doesn't matter):

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 206484 files and directories currently installed.)
Removing gimp ...
Removing gimp-data ...
Removing libgegl-0.0-0 ...
Removing libbabl-0.0-0 ...
Removing libgimp2.0 ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up postfix (2.7.0-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: INFRINGER.hsd1.md.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: INFRINGER.hsd1.md.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on lsb-invalid-mta | mail-transport-agent; however:
  Package lsb-invalid-mta is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
 lsb-core depends on maNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ilx | mailutils; however:
  Package mailx is not configured yet.
  Package bsd-mailx which provides mailx is not configured yet.
  Package mailutils is not installed.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
dpkg: error processing lsb-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 4.0); however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-printing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
 lsb depends on lsb-desktop; however:
  Package lsb-desktop is not configured yet.
 lsb depends on lsb-printing; however:
  Package lsb-printing is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 mailx
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb-desktop
 lsb-printing
 lsb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

Setting up postfix (2.7.0-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: INFRINGER.hsd1.md.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: INFRINGER.hsd1.md.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on lsb-invalid-mta | mail-transport-agent; however:
  Package lsb-invalid-mta is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 4.0); however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-printing (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-printing; however:
  Package lsb-printing is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
dpkg: error processing lsb-desktop (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

What the hell does this **** mean?

---

### Post by xjgnsdof on 2010-05-06
Fixed. I just had to install the unmet dependency "default-mta."

---

### Post by gnik1 on 2010-06-02
> **elgilicious said:**
> Fixed. I just had to install the unmet dependency "default-mta."

I am having a similar issue with installs.

Could u post how you corrected this? I do not know how to install the unmet dependency.

THanks in advance!

---

