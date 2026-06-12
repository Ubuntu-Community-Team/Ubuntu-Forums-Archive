---
title: "alsa driver problem"
date: 2011-04-12
forum: General Help
---

### Post by cadogan32 on 2011-04-12
i just installed the new alsa drive for my laptop cause the headphone jack wasnt working.ever since then anytime i try to install a program from the terminal or synaptic i get errors.

sudo apt-get install build-essential

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-28-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.32086.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

it always relates back to the alsa-driver,but i dont know what to do to fix it.any ideas?

---

### Post by cadogan32 on 2011-04-12
nevermind i got it working again.mod delete this message.

---

