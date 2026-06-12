---
title: "update-manager's 'Install Updates' button not working"
date: 2010-11-23
forum: General Help
---

### Post by mcfang on 2010-11-23
Running Ubuntu 10.10, recently the update-manager 'Install Updates' button does nothing. It is possible to click it, but packages are not installed and there is no error message. 

Example result in syslog after clicking install, the packages are not installed:
```
Nov 24 11:55:13 AptDaemon: INFO: Initializing daemon
Nov 24 11:55:13 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'pidgin'), dbus.String(u'pidgin-data')], signature=dbus.Signature('s'))
```


I noticed also that the Admin password popup is not called, and tested that there are no problems when run as  **sudo update-manager**, so perhaps it is related to authentication? How can I debug this?

---

### Post by nl4m on 2010-11-23
Try doing it manually:
```
[sudo apt-get update && sudo apt-get upgrade]("http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCoQFjAB&url=http%3A%2F%2Fwww.linuxquestions.org%2Fquestions%2Flinux-newbie-8%2Fsudo-apt-get-update-and-and-sudo-apt-get-upgrade-694365%2F&rct=j&q=sudo%20upgrade%20update&ei=O5nsTKTDJMT7lweiz_n9AQ&usg=AFQjCNFMNoVWED--FF5Tj_YbzVZRep_QHA&cad=rja")
```

Or you can try to reinstall it. Click on "Applications", "Ubuntu Software Center", type in the search bar "update manager", and download the package called "Update Manager".

---

### Post by mcfang on 2010-11-24
I can do the updates manually with sudo apt-get.., and I can do the updates when running update-manager as root.

The problem occurs when running update-manager as user (such as from the system tray icon).

I reinstalled update-manager using synaptic (I don't believe there is a reinstall option in ubuntu software center). Reinstalling does not appear to have made any difference.

---

### Post by mcfang on 2010-11-28
Several bug reports found, doesn't seem to be any real solutions yet :(

[LIST=1]
[*][update-manager's "Install Updates" button doesn't work]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/676865")
[*][install button does nothing]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/501580") 
[*][Install button does nothing when clicked]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/489519") 
[*][Update Manager, "install" button does nothing when u-m was opened by itself]("https://bugs.launchpad.net/hundredpapercuts/+bug/414181") 
[*][update-manager "Install Updates" button not functioning]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/392073")
[/LIST]

---

