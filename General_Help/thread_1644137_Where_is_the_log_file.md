---
title: "Where is the log file"
date: 2010-12-12
forum: General Help
---

### Post by satimis on 2010-12-12
Hi folks,

Ubuntu 1010 desktop 64 bit running on VM of VBox

On login as user a warning popup and disappeared promptly.  I was not able to read it.

On;

$ ls /var/log/```

alternatives.log  dmesg.2.gz      messages.1
apparmor          dmesg.3.gz      messages.2.gz
apt               dmesg.4.gz      news
aptitude          dpkg.log        pm-powersave.log
auth.log          faillog         pycentral.log
auth.log.1        fontconfig.log  samba
auth.log.2.gz     fsck            speech-dispatcher
boot              gdm             syslog
boot.log          installer       syslog.1
bootstrap.log     jockey.log      syslog.2.gz
btmp              jockey.log.1    udev
ConsoleKit        kern.log        ufw.log
cups              kern.log.1      unattended-upgrades
daemon.log        kern.log.2.gz   user.log
daemon.log.1      lastlog         user.log.1
daemon.log.2.gz   lpr.log         user.log.2.gz
debug             lpr.log.1       vboxadd-install.log
debug.1           lpr.log.2.gz    vboxadd-install-x11.log
debug.2.gz        mail.err        VBoxGuestAdditions.log
dist-upgrade      mail.info       VBoxGuestAdditions-uninstall.log
dmesg             mail.log        wtmp
dmesg.0           mail.warn       Xorg.0.log
dmesg.1.gz        messages        Xorg.0.log.old

```

Please advise on which log file I can find that warning?  TIA

B.R.
satimis

---

### Post by llamabr on 2010-12-12
my guess is that if the error popped up, and then disappears, and then it boots, you don't need to fix it.

but you might look in dmesg

---

### Post by satimis on 2010-12-12
> **llamabr said:**
> my guess is that if the error popped up, and then disappears, and then it boots, you don't need to fix it.

but you might look in dmesg

Hi,

Sorry, no

On the login page I entered username and passwd -> login.

During login there was a warning popup.  It vanished promptly.  I couldn't read it.  Then it login.

The problem encountered is on browsing it freezes now and then.

B.R.
satimis

---

