---
title: "I can not upgrade to Ubuntu 10.10"
date: 2010-10-12
forum: General Help
---

### Post by keniceland on 2010-10-12
I can not upgrade to Ubuntu 10.10 for any strange reasons:
$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
.
Moreover the "update manager" states my system is up to date yet im running 10.4
and no upgrade button or whatever appears
----------------------------------------------

I'm running on x86-64bit
.
$ lsb_release -rd
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
.
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
.
$ cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
prompt=normal

---

### Post by wilee-nilee on 2010-10-12
Go to software sources-updates in the menu and next to  release upgrade click normal.

---

### Post by plucky on 2010-10-12
Try ```
sudo apt-get update
sudo do-release-upgrade
```

Good Luck

---

### Post by ljunggr1 on 2010-10-12
I'm not sure what everything is called in English, but you have to do something like this:

System -> Administration -> Software sources -> Updates tab
The last option should be something like "normal upgrade" (not LTS)

Then check again. Worked for me.

---

### Post by keniceland on 2010-10-14
Thank you all for the replies.
All your suggestions were in place but no way to upgrade. 
Anyway at the end I resolved using "ubuntu-10.10-alternate-amd64.iso" and running from there the upgrade.

---

### Post by itaylor on 2010-12-02
I had the same, issue, went through all the same suggested fixes, and eventually upgrading using the installer on the 10.10 alternate CD. Thanks letting me know something like that was an option.

---

### Post by nutsy.ben on 2011-05-14
Yeap definitively an option. The alternate cd saved my life for the 10.04 version

---

