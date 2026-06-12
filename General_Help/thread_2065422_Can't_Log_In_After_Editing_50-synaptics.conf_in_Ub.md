---
title: "Can't Log In After Editing 50-synaptics.conf in Ubuntu 12.04"
date: 2012-10-01
forum: General Help
---

### Post by karat on 2012-10-01
I was editing my touchpad settings, but nothing seemed to change.  Even after rebooting, nothing seemed to change.  Then suddenly, rebooting caused me not to be able to log in.  Undoing the change and rebooting didn't do anything.

I boot fine, but when I try to log in, I get a screen of messages that go by too fast to tell and get dropped back to the login screen.

How do I find out what it is dying on, and how do I get default settings again?

This is for Ubuntu 12.04, and I was editing 50-synaptics.conf.

---

### Post by karat on 2012-10-01
Any way to quickly reset my login preferences?

---

### Post by karat on 2012-10-01
It's not a user dotfile.  It's got to be X.  Any way to reset these settings to default?

---

### Post by karat on 2012-10-01
dpkg-reconfigure didn't help

---

### Post by steeldriver on 2012-10-01
Can you log in to a non graphical virtual terminal (Ctrl-Alt-F1)? if so you can check the /var/log/Xorg.0.log and your ~/.xsession-errors

Also check that ~/.Xauthority is owned by you and writeable

---

### Post by karat on 2012-10-02
> **steeldriver said:**
> Can you log in to a non graphical virtual terminal (Ctrl-Alt-F1)? if so you can check the /var/log/Xorg.0.log and your ~/.xsession-errors

Also check that ~/.Xauthority is owned by you and writeable

Yes, I could log in that way.  I tried to reinstall a few things, but nothing worked.  How do I get a fresh copy of the file to compare against?  How do I know which package it came from?

---

