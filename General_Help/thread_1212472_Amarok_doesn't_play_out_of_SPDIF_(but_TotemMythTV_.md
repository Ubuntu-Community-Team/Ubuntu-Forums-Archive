---
title: "Amarok doesn't play out of SPDIF (but Totem/MythTV does)"
date: 2009-07-13
forum: General Help
---

### Post by damien_d on 2009-07-13
Dear all,

I have recently upgraded my motherboard and chip for various reasons, but I have been having problems trying to get SPDIF (optical audio) fully work.

I am using Ubuntu (Gnome) 9.04 Jaunty.

I have gotten most of the problems sorted out - see [http://ubuntuforums.org/showthread.php?t=1201139](http://ubuntuforums.org/showthread.php?t=1201139) for the details.

However, one persistent problem I have is getting Amarok 2 to play music out of SPDIF.

I can play audio on SPDIF out of Totem, MythTV and Rhythmbox without problems.  To do so, I needed to explicitly go to System -> Preference -> Sound and change from "Autodetect" to "VT1708S Digital"

If I plug an ordinary set of speakers into the standard light green jack, I can hear that Amarok is indeed playing music.

So far I have been trying to get my head around the following file that, from searching around a little, might help:
```

.kde/share/config/phonondevicesrc

```

Deleting it makes no difference - it regenerates itself.  My guess that Phonon (as opposed to whatever gnome uses) is not pushing sound out the correct port.  How can I set this up to make it work?

If there's further information that will help, I will gladly supply it.

 -- Damien

EDIT: I should mention that on my old motherboard, Amarok 2 played quite nicely out of SPDIF.

---

### Post by damien_d on 2009-12-05
This magically fixed itself with Ubuntu 9.10.  Don't ask me how!

  -- Damien

---

