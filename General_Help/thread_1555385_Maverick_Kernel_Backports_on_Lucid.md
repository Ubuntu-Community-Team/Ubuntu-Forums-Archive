---
title: "Maverick Kernel Backports on Lucid"
date: 2010-08-18
forum: General Help
---

### Post by xenogia on 2010-08-18
Just wondering if anyone is using the Maverick kernel backport with Lucid? Just wanting to know how stable it is.

---

### Post by DarkAmbient on 2010-08-18
Probably been updates to it since, but I tried to install and run it 2-3 weeks ago and I quite never got into the OS. Got errors before entering the gnome desktop.. fresh install and all. Could just be me though. You'll never know with alpha releases.

---

### Post by xenogia on 2010-08-18
> **DarkAmbient said:**
> Probably been updates to it since, but I tried to install and run it 2-3 weeks ago and I quite never got into the OS. Got errors before entering the gnome desktop.. fresh install and all. Could just be me though. You'll never know with alpha releases.


A week or so ago I used the 2.6.35 mainline kernel and got a whole bunch errors before login.  Then I tried 2.6.35.1 which mades thing even worse, had issues with mountall.  Just wondering because these Kernel's would be more suited to Ubuntu that they would be more appropriate.

---

### Post by clhsharky on 2010-08-18
I use the (OSS)Open Source Stack drivers, and the DRI in the kernels is part of that stack. So for me to use the latest OSS I need the latest kernel.
Mainline kernels have never been a problem for me in Lucid, having used .33, .34 and .35 mainline. Maverick kernel backport for Lucid did give me a glitch that has been reported on launchpad, but no show stopper.
I do understand when using the blobs, matching xorg and kernels is a must do.

Sharky

---

### Post by xangua on 2010-08-18
if it's even backport in maverick what else were you expeckting :S

good luck, don't break your penguins ;)

---

### Post by xenogia on 2010-08-18
What is the easiest way to upgrade xorg in correspondence with .35 kernel?

---

### Post by teeepeli on 2010-08-25
There's 2.6.35 kernel with maverick config for lucid in ricotz ppa: [https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

Never had any problems with it and I have used it for a long time.

---

### Post by inameiname on 2010-08-25
I use this and don't have a problem in Lucid:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-19-generic linux-image-2.6.35-19-generic

Just remember to 'sudo apt-cache search linux-image' occasionally to check for new versions since it doesn't do it automatically.

Every now and then there is a bad version, but so far for me, it's been rare. They usually fix it anyway so usually I just wait one or two versions before I decide to upgrade.

---

### Post by xenogia on 2010-08-25
From what I can tell 2.6.36-19 doesn't exist only 18.  Either way I upgraded the kernel and it works fantastic especially VM related stuff.  So much smoother.

---

### Post by inameiname on 2010-08-25
2.6.35-19-generic came out last night in the kernel-ppa I mentioned. I installed it earlier today, and am currently running it.

---

