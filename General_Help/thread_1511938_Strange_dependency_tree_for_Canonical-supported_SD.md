---
title: "Strange dependency tree for Canonical-supported SDL packages?"
date: 2010-06-17
forum: General Help
---

### Post by aquavires on 2010-06-17
Hi all,

Some time ago I installed SDL in Ubuntu 10.04 using Synaptic Package Manager. Now, there are upgrades available for the following packages:

libsdl1.2-dev
libsdl1.2debian
libsdl1.2debian-pulseaudio

Trying to upgrade them seemed to reveal contradictory dependencies.

If I select "mark for upgrade" on libsdl1.2-dev or libsdl1.2debian, Synaptic says I have to **remove** libsdl1.2debian-pulseaudio. But if I select "mark for upgrade" on libsdl1.2debian-pulseaudio, Synaptic tells me that I have to **upgrade** libsdl1.2-dev and libsdl1.2debian!

I'm worried about breaking something, so I haven't upgraded yet. Is there an error in the dependency tree, or am I missing something obvious?

---

### Post by aquavires on 2010-06-18
Is it safe to update?

Marking **libsdl1.2-dev** or **libsdl1.2debian** for upgrading also requires the removal of **ubuntu-desktop**. I'm not familiar with what ubuntu-desktop is for, but removing it doesn't sound like a good idea.

If I select **libsdl1.2debian-pulseaudio** for upgrading, Synaptic requires me to upgrade libsdl1.2-dev and libsdl1.2debian, but makes no mention of ubuntu-desktop. Will it implicitly remove ubuntu-desktop anyway?

Any advice would be much appreciated, thanks!

---

### Post by dcstar on 2010-06-19
> **aquavires said:**
> Is it safe to update?

Marking **libsdl1.2-dev** or **libsdl1.2debian** for upgrading also requires the removal of **ubuntu-desktop**. I'm not familiar with what ubuntu-desktop is for, but removing it doesn't sound like a good idea.

If I select **libsdl1.2debian-pulseaudio** for upgrading, Synaptic requires me to upgrade libsdl1.2-dev and libsdl1.2debian, but makes no mention of ubuntu-desktop. Will it implicitly remove ubuntu-desktop anyway?

Any advice would be much appreciated, thanks!

The latest official version of these on my system is 1.2.14-4ubuntu1.1(lucid-updates), if you are installing from another unofficial repository then you will have issues like that.

---

