---
title: "Boot screen garbled error message"
date: 2010-06-16
forum: General Help
---

### Post by JusticeZero on 2010-06-16
I updated the laptop to 10. I got a lot of error messages during the upgrade! But it seemed to upgrade..
So I boot it up. I get the 'Ubuntu .....' loading screen, then an error message underneath it.
I do not know what the error message is; it is two or three lines long, but all three appear on the same line. One is in white and more legible than the one(s?) behind it.
"Continue to wait or Press S to skip mounting or M for manual recovery."
"The di????r ?e f????w?n?o????is????????y?ye o?n???p?????se??"

If I skip it seems to run more or less normally, though the wireless keeps disconnecting-reconnecting every few seconds.

How can I fix?

---

### Post by dino99 on 2010-06-16
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

sudo apt-get install gconf-cleaner

goto menu: apps system gconf-cleaner, run it (yes to all)

ckeck that drivers are activated: system admin hardware driver

about wifi: into synaptic, install wifi-radar (what is the wifi chipset ?, maybe it need a package to be installed)

---

### Post by JusticeZero on 2010-06-16
Error message on bootup is still there after doing those steps. 
Wireless connection looks like it may be more stable at least.

Any other ideas as far as the error is concerned?

---

