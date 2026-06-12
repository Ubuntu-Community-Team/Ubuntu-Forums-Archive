---
title: "Kernel update broke sound..including past kernels."
date: 2010-09-02
forum: General Help
---

### Post by Lolpanda on 2010-09-02
Title basically says it, an update from a few days ago seems to have broken my sound, including for past kernel versions. 

Synaptic history:

```
Upgraded the following packages:
aptdaemon (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
bogofilter (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
bogofilter-bdb (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
bogofilter-common (1.2.1-0ubuntu1) to 1.2.1-0ubuntu1.1
handbrake-cli (svn3504ppa1~lucid1) to svn3506ppa1~lucid1
handbrake-gtk (svn3504ppa1~lucid1) to svn3506ppa1~lucid1
libgudev-1.0-0 (1:151-12) to 1:151-12.1
libudev0 (151-12) to 151-12.1
libwww-perl (5.834-1) to 5.834-1ubuntu0.1
linux-headers-2.6.32-24 (2.6.32-24.41) to 2.6.32-24.42
linux-headers-2.6.32-24-generic (2.6.32-24.41) to 2.6.32-24.42
linux-image-2.6.32-24-generic (2.6.32-24.41) to 2.6.32-24.42
linux-libc-dev (2.6.32-24.41) to 2.6.32-24.42
mountall (2.15) to 2.15.1
python-aptdaemon (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
python-aptdaemon-gtk (0.11+bzr345-0ubuntu4) to 0.11+bzr345-0ubuntu4.1
udev (151-12) to 151-12.1

```

I followed the troubleshooting, soundcard is detected, I reinstalled the linux sound base, only thing I couldnt do was load the correct module by hand, because the link to the Alsa module list on in that guide to the alsa-docs is outdated and has seemingly changed as there is no search box or anything described in the guide. I really don't even know where to start on this one guys, typically I'd just roll back to an old kernel for now, but even those dont have sound

---

### Post by Lolpanda on 2010-09-03
bumpity bump bump

---

### Post by prayag on 2010-09-06
Bump from me too. Same problem.

---

### Post by a.daniel on 2010-09-20
My sound problems after Upgrade to 2.6.32-24 were fixed by following the advice in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519)

> 
Actually, this appears to be a bug with permissions, I had to add myself to the audio group. I'm not sure what's causing it, but it doesn't appear to be kernel related.


---

