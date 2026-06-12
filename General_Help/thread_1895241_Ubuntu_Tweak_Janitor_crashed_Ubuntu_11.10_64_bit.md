---
title: "Ubuntu Tweak Janitor crashed Ubuntu 11.10 64 bit"
date: 2011-12-14
forum: General Help
---

### Post by jmb52695 on 2011-12-14
I updated my computer this morning, and before i restarted it i ran ubuntu tweak's janitor tool (i know it was probably the wrong thing to do before i restarted my computer to finish installing the update) after i restarted my computer Ubuntu hangs at the final screen before the login screen (the one where all the dots under Ubuntu are filled in) What happened and how do i fix it? I can't find any help on Google or the fourms.
Thanks!

---

### Post by jmb52695 on 2011-12-14
Anybody? I need to get my computer back up and running ASAP!

---

### Post by jmb52695 on 2011-12-14
I tried running theses commands

sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get upgrade

They did not do anything however.

I also tried to repair all broken packages in the recovery mode but no luck. Any help?

---

### Post by jmb52695 on 2011-12-14
I still am unable to figure this out, i really need my computer for work tomorrow though! I just purged Ubuntu-Tweak and it still did not help any. I told the Ubuntu-Tweak janitor to clean everything, and like i said it was right after i updated everything, but before i restarted. So i would be very thankful for any help!

---

### Post by jmb52695 on 2011-12-14
I was finally able to catch an error message while it was booting, here it is:

Checking for running unattended-upgrades:
Traceback (most recent call last):
    File "/usr/share/unattended-upgrades/unattended-upgrade-shutdown", line 27, in <module>
        import apt_pkg
ImportError: No module named apt_pkg

it then starts the winbind daemon
starts bluetooth
PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

it then appears to hang at the following thing

* Checking battery state...

it does not do anything past that

---

### Post by jmb52695 on 2011-12-15
Still can't figure it out! Is there anyone that can help me? Please!

---

### Post by Frogs Hair on 2011-12-15
I found this on Google . [http://techspear.com/2011/08/booting-ubuntu-oneiric-stops-at-checking-battery-state-ok/](http://techspear.com/2011/08/booting-ubuntu-oneiric-stops-at-checking-battery-state-ok/)

---

