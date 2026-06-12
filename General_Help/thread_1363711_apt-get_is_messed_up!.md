---
title: "apt-get is messed up!"
date: 2009-12-24
forum: General Help
---

### Post by hobbleDHoy on 2009-12-24
I recently successfully installed iFuse in order to access my iPhone on Ubuntu (latest). However, it apparently left me with some broken packages. Whenever I try to install something, anything, through apt-get, it informs me that some packages related to the iFuse installation are broken, and that I need to fix them. This is the message I get when trying to install automake:

The following packages have unmet dependencies:
  automake: Depends: autoconf (>= 2.60) but it is not going to be installed
            Depends: autotools-dev (>= 20020320.1) but it is not going to be installed
  gvfs-backends: Depends: usbmuxd but it is not going to be installed
  ifuse: Depends: libusbmuxd1 but it is not going to be installed
  libiphone0: Depends: libusbmuxd1 but it is not going to be installed
  libusbmuxd-dev: Depends: libusbmuxd1 (= 1.0.1-0ubuntu1~k) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I then do the "-f", and then I get the following message:

Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb
 /var/cache/apt/archives/usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried "sudo apt-get autoremove", and to manually remove each package, using both "sudo apt-get remove" and actually cd-ing to the specified directory, but everytime I get an error message like the first one. Does anyone have any idea what this is about?

Peace

---

### Post by taurus on 2009-12-24
Did you run the command that it told you to?

```
sudo **apt-get -f install**
sudo apt-get update
```

---

### Post by hobbleDHoy on 2009-12-25
Yes, I did "sudo apt-get -f install", and then I got the message:

Errors were encountered while processing:
/var/cache/apt/archives/libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb
/var/cache/apt/archives/usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

"sudo apt-get update" doesnt help either :(

---

### Post by taurus on 2009-12-25
Try cleaning out your cache.

```
sudo apt-get clean
sudo apt-get update
```

Did you install iFuse from the repos?

---

### Post by hobbleDHoy on 2009-12-25
I did that too, but nothing changed :(

Yes, I followed this tutorial:

[http://www.ubuntugeek.com/ipod-touch-3g-sync-over-usb-without-jailbraking-in-ubuntu-karmic.html](http://www.ubuntugeek.com/ipod-touch-3g-sync-over-usb-without-jailbraking-in-ubuntu-karmic.html)

---

### Post by taurus on 2009-12-25
What if you temporarily disable that third-party repo in Synaptic or Software Sources.  See if that cures the problem.

---

### Post by hobbleDHoy on 2009-12-25
Thanks a lot, I opened Synaptic and marked the broken packages for complete removal. Im still a noob, so thanks for helping me out ;)

---

### Post by taurus on 2009-12-25
I assume everything is back in order with your system again then?

---

### Post by hobbleDHoy on 2009-12-25
Yup, thank you so much :D

---

