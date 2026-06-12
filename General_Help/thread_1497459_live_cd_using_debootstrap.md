---
title: "live cd using debootstrap"
date: 2010-05-30
forum: General Help
---

### Post by plutoniumpenguin on 2010-05-30
Hello.

I'm following this guide: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

Now, it says that you need to install the package called "discover"/"discover1" on the new system.  However, in Lucid, this package is not even in the main repositories!  Is there something equivalent that is used in Lucid instead?  The official Ubuntu live cd certainly doesn't have this package...

Also, is it possible to configure things so that some of the startup applications are disabled (e.g. "look for new hardware drivers") and so that some of the menu shortcuts are changed to new targets (I want to run things like gedit, nautilus, and the terminal as superuser, so I want the shortcut commands to have a "gksu" prefixed)?

Thanks!

---

### Post by plutoniumpenguin on 2010-05-30
bump

---

### Post by bakegoodz on 2010-05-30
The package is there, but I have universe and multiverse in my sources

you can just add the words: universe multiverse After every line in /etc/apt/sources.list

Example:
deb [http://bla.org/ubuntu](http://bla.org/ubuntu) lucid main restricted universe multiverse
deb [http://bla.org/ubuntu](http://bla.org/ubuntu) lucid-updates main restricted universe multiverse
deb [http://bla.org/ubuntu](http://bla.org/ubuntu) lucid-security main restricted universe multiverse

then run: apt-get update

---

### Post by plutoniumpenguin on 2010-05-30
Sorry, I should have been more clear.  I actually was aware that the package still existed, but what I meant by "main repositories" was the repositories that you have access to if you have the word "main" after an url in the sources.list file.  Anyways, the point I was trying to make is that this seems like evidence for that particular guide being outdated, because I have a hard time accepting Ubuntu putting up a guide like that which requires you to use software that they don't fully support and which is not even used in their official version of the product which following this guide is supposed to produce (namely, a live cd).

---

### Post by Fatman_UK on 2010-07-29
Hi.

I'm following the same guide but debootstrap seems to install a completely broken Lucid for me. Half the packages are missing and the rest can't be installed due to cyclic dependencies.

I'm stuck at "apt-get install --yes dbus", so you've got further than me, penguin. Tried "apt-get -f install", it doesn't do anything. Tried aptitude instead, it does no better.

Ah well! I'll delete the broken chroot and try again tonight, maybe with Karmic instead. At least that's been around a bit longer.

[EDIT]

I got it working with Karmic in the end. One thing I will say is to be very careful with chroot/etc/apt/sources.list, because it's very easy to accidentally upgrade your chrooted Karmic to Lucid if your host is on Lucid. I managed it without even noticing, and now my chroot won't boot. I guess Lucid doesn't like being squashfs'd (yet)?

Here we go again! Maybe I'll set up a VM with Karmic so I can't dist-upgrade too far.

[EDIT]

I've managed to reproduce my original error. [Bug report.]("https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/611711")

---

