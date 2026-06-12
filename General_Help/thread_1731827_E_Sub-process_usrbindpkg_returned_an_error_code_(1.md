---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-04-17
forum: General Help
---

### Post by umwhat on 2011-04-17
This happens for EVERYTHING I try to install through terminal.
When I try to install/uninstall from USC, I get "Package operation failed: The installation or removal of a software package failed."

This is the log I get when I get that error:
(attempting to uninstall emesene)

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
(Reading database ... 135088 files and directories currently installed.)
Removing emesene ...
Removing python-libmimic ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

Also, I forgot to add, even though I get these errors when installing/uninstalling through USC, they still install/uninstall.

---

### Post by coldraven on 2011-04-17
What version of Ubuntu are you running?

---

### Post by umwhat on 2011-04-18
Ubuntu 10.10

---

### Post by Rubi1200 on 2011-04-18
Hi,

try running these commands in the terminal and posting back with the errors if any are reported:

```
sudo apt-get install -f

sudo dpkg --configure -a
```

What wireless card do you have on the computer?

You could remove the package and see if it helps:

```
sudo apt-get purge firmware-b43-installer
```

---

### Post by umwhat on 2011-04-20
Removing the firmware worked, but now I get:
E: Some index files failed to download, they have been ignored, or old ones used instead.

and:
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied) E: Unable to lock directory /var/lib/apt/lists/ E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?		

And I always use sudo, so I don't know what's up with that.

---

### Post by TeoBigusGeekus on 2011-04-20
Try this and see if it helps:
Rename the lists directory
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_backup
```
Clean up your cache
```
sudo apt-get clean
```
and try again.

---

### Post by umwhat on 2011-04-28
Thanks! I deleted the firmware and everything is fine now! :)

---

