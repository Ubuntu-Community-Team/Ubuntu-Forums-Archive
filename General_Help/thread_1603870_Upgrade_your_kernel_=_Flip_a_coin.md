---
title: "Upgrade your kernel = Flip a coin"
date: 2010-10-23
forum: General Help
---

### Post by sr_guy on 2010-10-23
I'm currently running 10.04.1. Since Karmic release (maybe even Hardy) it seems like that 50% of the time when there is a kernel upgrade via repo and update manager, it breaks Nvidia drivers, a reboot invites a low res screen saying that the nvidia kernel is broke. After 2-3 new releases, why is this still the case? With the latest kernel, 2.6.34 for Lucid I believe, it breaks Nvidia drivers no matter what I do. It also causes issues with lirc. The only kernel that I have been able to keep everything working is 2.6.32-25-generic-pae. Is there a clear cut way to know if upgrading will break anything? Sorry about the rants, it's just frustrating. :)

---

### Post by ellgor on 2010-10-23
Hi, I found this guide that gets the nvidia drivers (newest ones) in and running, not sure about Maverick though:

Go to the nvidia site and download the latest driver for your card, have it easy to hand

Open a terminal and stop the gdm with this:

sudo gdm-stop

A black screen with terminal access will be presented, cd to the downloaded nvidia package

Install package with:

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have) be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

 Follow the onscreen guide from Nvidia and when done
 Start GDM

sudo service gdm start

Regards, Ellgor.

---

