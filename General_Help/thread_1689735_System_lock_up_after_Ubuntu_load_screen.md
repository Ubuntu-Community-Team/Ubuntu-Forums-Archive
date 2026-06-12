---
title: "System lock up after Ubuntu load screen"
date: 2011-02-17
forum: General Help
---

### Post by JayUK20 on 2011-02-17
Yesterday I updated my system and rebooted then after the Ubuntu load screen I get the round loading timer and everything locks up and stays on the black screen. I entered the recovery console and dropped to a command prompt and typed startx and Ubuntu booted but the system locked up on the dekstop. I got an error message which said "OAFIID:Gnome_Indicator Appelt" encountered a problem.

IS there anything I Can do to get the system working again? I am using Wubi 9.04 (prefer that version)

Update I done was this:

> sudo dpkg --configure -a && sudo apt-get install -f && sudo apt-get update

Then....

> sudo apt-get install linux-headers-$(uname -r) build-essential make patch gettext autoconf subversion tcl8.5 openssl libssl-dev libnl1 libnl-dev cracklib-runtime python-scapy macchanger-gtk tshark


I've never had a problem with doing the above until now.

---

### Post by JayUK20 on 2011-02-18
Any ideas???

---

