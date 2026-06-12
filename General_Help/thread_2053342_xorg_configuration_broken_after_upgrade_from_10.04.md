---
title: "xorg configuration broken after upgrade from 10.04 to 12.04.1"
date: 2012-09-05
forum: General Help
---

### Post by think13 on 2012-09-05
After upgrading from 10.04 to 12.04.1, I cannot log in to my account (it immediately kicks me back to the login screen). The guest session goes to a nonfunctional desktop. Looking at the Xorg logs, I get these errors:
```
(EE) Screen 0 deleted because of no matching config section.

(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found
```

I have a bunch of backups of xorg.conf, but no xorg.conf.d
```
david@david-desktop:~$ ls /etc/X11/
app-defaults                      xorg.conf_backup_2009820227
cursors                           xorg.conf_backup_20098301531
default-display-manager           xorg.conf_backup_20098301532
default-display-manager.dpkg-tmp  xorg.conf.dist-upgrade-200910300846
fonts                             xorg.conf.dist-upgrade-201005081552
ja_JP.eucJP                       xorg.conf.dist-upgrade-201209050206
ja_JP.UTF-8                       xorg.conf.failsafe
rgb.txt                           xorg.conf.original-0
X                                 Xreset
xinit                             Xreset.d
xkb                               Xresources
xorg.conf                         Xsession
xorg.conf.20090830151911          Xsession.d
xorg.conf.20090830152316          Xsession.options
xorg.conf.backup                  XvMCConfig
xorg.conf-backup-090904163816     Xwrapper.config
xorg.conf-backup-120429180631
```

I've attached the Xorg.1.log file as well as my xorg.conf.

I have a two monitor setup with monitors from two manufacturers (Acer and Lenovo) with two different aspect ratios.

What would be the easiest way to get this working? If I could get it working with just one screen, I should be able to configure the multiple screen setup through the graphical interface.

Thanks in advance!

---

### Post by kimberlite on 2012-09-05
Just a guess... Try rename xorg.conf and restart.

---

