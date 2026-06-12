---
title: "Installing 11.10 with ati Radeon black screen LIVE CD working bypass"
date: 2011-10-23
forum: General Help
---

### Post by collisionystm on 2011-10-23
I just figured this out and wanted to share.

When I would boot from the Live Cd, even with nomodeset and acpi=off, I would only get to the command line. No GUI.

If you are having this problem and you have the radeon card you can do the following...

reboot your computer from the cd rom drive

hold the SHIFT key while booting so you can get to the selection screen. Choose your language, cursor over Try Ubuntu without Installing

Press F6, choose nomodeset

it ESC and then ENTER to boot.

Once you are at the text login

```
sudo bash
```

```
apt-get remove xserver-xorg-video-radeon
```
```

X

```
Press CTRL + ALT + F1

```
service lightdm start
```

Voila, you are now at the 11.10 unity live mode.

---

### Post by BlackXanthus on 2012-01-24
[B]Thank You

[/B]Having just got my hands on some HP Pavillion G-Series laptops with Radeon Graphics cards, trying to install 64 bit version of Ubuntu, normally a walk in the park was proving to be problematic. I was almost contemplating moving to a different flavour of Linux!

This fix works extremely well, and I was quite able to install the system from the live CD. All that remains to be seen is if they will then boot....

~BX

---

