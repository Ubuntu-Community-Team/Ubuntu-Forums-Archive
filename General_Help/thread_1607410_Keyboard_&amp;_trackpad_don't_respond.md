---
title: "Keyboard &amp; trackpad don't respond"
date: 2010-10-27
forum: General Help
---

### Post by scooterkool on 2010-10-27
My Thinkpad R32 keyboard & trackpad will not work when booted off the HD with 9.04, I can plug in an external USB keyboard & that works fine.
_If I start the laptop from a Ubuntu LiveCd the keyboard & trackpad work fine._
There must be some system file disabling the onboard keyboard, I have used Keyboard Preferences to try different keyboard models.

Still No Luck.
Any Ideas?:confused:

---

### Post by Hippytaff on 2010-10-27
Is the liveCD the same version that your running on the HD?

---

### Post by scooterkool on 2010-10-27
Hi,
Yes the LiveCD is the same version, that just proves it's not a hardware problem....

---

### Post by scooterkool on 2010-11-02
In preparation to upgrade offline I ran the commands

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get remove

After restarting the keyboard and mouse were working normally.
:popcorn:

---

