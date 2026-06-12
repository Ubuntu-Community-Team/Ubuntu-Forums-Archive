---
title: "proftpd not starting with latest kernel"
date: 2010-06-08
forum: General Help
---

### Post by cryptotheslow on 2010-06-08
Hi,

Running proftpd on Lucid 32bit I have a problem that has me stumped.

On the current kernel 2.6.32-22-generic proftpd does not startup on system startup - in fact there is no mention of it in any logs, including the proftpd log files.

From Terminal I try a sudo proftpd and get this:

```

graham@gt-desktop:~$ sudo proftpd
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
gt-desktop - 127.0.1.1:21 masquerading as nn.nn.nn.nnn
gt-desktop - mod_delay/0.6: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory
gt-desktop - notice: unable to listen to local socket: Operation not permitted
```

If I boot into the previous kernel: 2.6.32-21-generic proftpd starts up fine on system startup and if I kill it then restart it I get:

```

graham@gt-desktop:~$ sudo proftpd
 - notice: unable to bind to Unix domain socket at  '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
gt-desktop - 127.0.1.1:21 masquerading as nn.nn.nn.nnn

```

... and it starts up fine.


The weird thing is, is that this did not break right after the kernel upgrade. It was working fine after that for a couple of days and several reboots on the new kernel.

The only thing that has changed between it working and not working is some updates I applied last night as recommended by the Update Manager:

```

Commit Log for Tue Jun  8 20:30:34 2010

Upgraded the following packages:
brasero (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
brasero-common (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
gnome-panel (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
gnome-panel-data (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
libbrasero-media0 (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
libcairomm-1.0-1 (1.8.0-1build2) to 1.8.4-0ubuntu1
libgcr0 (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libgp11-0 (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libpam-gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libpanel-applet2-0 (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
openoffice.org-base-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-calc (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-common (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-draw (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-emailmerge (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gnome (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gtk (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-impress (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-math (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-style-human (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-writer (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
python-papyon (0.4.6-0ubuntu2) to 0.4.8-0ubuntu1
python-uno (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
rhythmbox (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
rhythmbox-plugins (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
telepathy-butterfly (0.5.8-1ubuntu1) to 0.5.9-0ubuntu1
ttf-opensymbol (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
tzdata (2010i-1) to 2010j-0ubuntu0.10.04
tzdata-java (2010i-1) to 2010j-0ubuntu0.10.04
uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1
ure (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1

```

Since rebooting after that set of updates, proftpd will not start up - seemingly with some kind of permissions problem... but I can't work out what. I have reinstalled the proftpd-basic package to no effect.

Any thoughts on how to fix, or dig deeper this would be much appreciated.

Thanks :)

---

