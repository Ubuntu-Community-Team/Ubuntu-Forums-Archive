---
title: "Update Manager Authentication notice"
date: 2010-08-10
forum: General Help
---

### Post by de Bacon on 2010-08-10
Sorry I have a hard time writing these questions, but here goes,

My update manager is configured to look once a day, and I have only 3 repositories on my list of "Other Software" they are:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner (Source Code)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

Today Update Manager has an update in which all the items are marked as "can't be authenticated"  I canceled the update but it is kind of alarming. Any thoughts on why these can't be authenticated?  

Specifically the updates are-

Important security updates:

libldap-2.4-2
  OpenLDAP libraries (Size: 209 KB)
w3m
  WWW browsable pager with excellent tables/frames support (Size: 1.0 MB)

Recommended updates:

python-apt
  Python interface to libapt-pkg (Size: 182 KB)

tzdata
  timezone and daylight-savings time data (Size: 660 KB)

update-manager
  GNOME application that manages apt updates (Size: 783 KB)

update-manager-core
  manage release upgrades (Size: 195 KB)

update-manager-kde
  Support Modules for Update Notifier KDE (Size: 48 KB)

---

### Post by lubumbax on 2010-08-11
Hi, can you open a terminal and execute (without the '$'):
$ sudo apt-get update
$ sudo apt-get upgrade
What does it return? Pay special attention to 'signatures' related feedback.

---

### Post by de Bacon on 2010-08-11
I did that, there were no warnings or other about signatures.  Though after closely looking at the output, I decided to abort the process, due to my own ignorance in knowing the result, other than it was going to install all the updates had I continued.  

I went back to update manager and ran its process again, this time there were no warnings about authentication.  So I let the update run.  All still works though I have not yet rebooted the system, there isn't a 'reboot message' anyhow.  

I guess I can live with the result and hope (in my ignorance).  

Thanks

---

