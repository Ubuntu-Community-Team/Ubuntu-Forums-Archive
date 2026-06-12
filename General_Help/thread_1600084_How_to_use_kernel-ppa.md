---
title: "How to use kernel-ppa?"
date: 2010-10-18
forum: General Help
---

### Post by NearlyALaugh on 2010-10-18
Hi there,

I'd like to use the backported Maverick kernel on my Lucid installation. However, I've been unable to use the kernel-ppa archive [to install it](http://ubuntuforums.org/showthread.php?p=9933985#post9933985).

```
$ sudo apt-add-repository ppa:kernel-ppa/ppa
...
$ sudo aptitude update
...
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US
...
```
Why does **apt-get update** ignore the archive? Why is its [Launchpad page](https://launchpad.net/~kernel-ppa/+archive/ppa) empty?


Peace~

---

### Post by NearlyALaugh on 2010-10-20
Anyone have success downloading the backported kernel for Lucid?


Edit: They just uploaded **linux-image-generic-lts-backport-natty** at the ppa.

---

### Post by bitmonkey on 2010-11-05
I am also having trouble with this - apt-get just seems to ignore the repository and not see it at all. Which is odd, because I installed linux-image-server-lts-backport-natty on 3 boxes about a week or two back with no problem, I'm now following my notes from that day exactly to the letter, I've checked the PPA source entries, the key is downloaded, but it won't install now.

---

### Post by User4519 on 2011-01-29
> **bitmonkey said:**
> I am also having trouble with this - apt-get just seems to ignore the repository and not see it at all. Which is odd, because I installed linux-image-server-lts-backport-natty on 3 boxes about a week or two back with no problem, I'm now following my notes from that day exactly to the letter, I've checked the PPA source entries, the key is downloaded, but it won't install now.

Exactly the same problem here... Earlier today, I installed Kubuntu 10.10, added the PPA and installed the 2.6.38 kernel. It didn't show up right away, so I also tried adding the lines necessary in /etc/apt/sources.list, and after that it showed up.

I just reinstalled everything (was just testing on a different harddrive the first time around), this time adding the key and the lines manually. Nothing.

Tried the PPA again, still nothing.

I've tried dist-upgrading to the latest 2.6.35 kernel, removing and adding the sources.lst lines, re-adding the PPA, I simply cannot apt-cache search my way to the 2.6.38 kernel anymore... I'm stomped!

---

### Post by User4519 on 2011-01-29
Ahhhh...

The PPA is indeed either broken, or Maverick isn't supported? If you copy/paste the sources.list deb lines that are presented on launchpad, you get to install the kernel.

deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

I don't like to install kernels for a previous version of buntu, though :(

---

### Post by User4519 on 2011-01-29
Whoops, our mistake. These kernel backports are only meant for LTS versions, it seems. So maverick isn't going to get any of these specifically.

FWIW, doing it manually, using the lucid deb links on the page, worked just fine for me. The default kernels on lucid and maverick do not support the hotkeys or the touchpad on my laptop properly, so I need to get this (or an equivalent kernel, really, or a Linux Mint kernel)... Anyway, everything seems to work just fine for me using this lucid kernel on maverick.

---

