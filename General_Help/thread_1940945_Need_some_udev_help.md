---
title: "Need some udev help"
date: 2012-03-14
forum: General Help
---

### Post by Mr. Echo on 2012-03-14
Hello.  I have added a second sound card to my system.  I want to override the default owner/permissions for audio devices and make this card readable/writable only by root.  (I'm doing this because I'm scheduling the card to play something every day to a remote speaker via root's crontab and I don't want any other user desktops interfering with that card).  Anyway, I've tried the following udev rule:

# Creative Ensoniq
KERNEL=="audio*", ATTRS{vendor}=="0x1274", ATTRS{device}=="0x5880", SYMLINK+="ensoniq", OWNER="root", MODE="0600"

I've placed this rule into /etc/udev/rules.d/99-tcg.rules.  The rule seems to be executing because the /dev/ensoniq link is being created but the owner and mode are not being set correctly.  The device ends up as follows after running "udevadm trigger":

lrwxrwxrwx 1 root root 6 2012-03-14 16:01 /dev/ensoniq -> audio2
crw-rw----+ 1 root audio 14, 36 2012-03-14 16:01 /dev/audio2

I think this is set up by the default udev rules.  I'm using Ubuntu 10.04.4 LTS 64 bit.

Any idea what I'm doing wrong?

---

