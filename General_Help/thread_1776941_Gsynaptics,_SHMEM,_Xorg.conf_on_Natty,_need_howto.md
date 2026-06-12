---
title: "Gsynaptics, SHMEM, Xorg.conf on Natty, need howto"
date: 2011-06-07
forum: General Help
---

### Post by icarus74 on 2011-06-07
Hi,

The Synaptics touchpad on my laptop, where I am running Ubuntu natty 11.04-amd64 desktop is extremely sensitive and the cursor is running wild with random clicks, screen scrolls and what not. Checking around figured that the touchpad has several settable parameters, and one needs to tweak those. Apparently, gsynaptics is the way to go, however that requires enabling shared-memory access to the touchpad driver, which needs editing Xorg.conf. And, sometime around 9.04, Xorg.conf was made optional, s.t. Xorg server runs with defaults / autodetection, but could potentially read/use Xorg.conf if one existed. 

So the question is, how do I create a Xorg.conf file which reflects the current defaults (as used by Xorg server), since everything (barring the touchpad) is working pretty well, so I don't want to mess with the defualts ? Only after I have such a file, can I think of modifying it, for Synaptics driver SHMEM.

Looking for some guidance.

cheers,
Icarus

---

### Post by icarus74 on 2011-06-07
Is it possible to auto generate an Xorg.conf with the current set of defaults ? Anyone ?

---

### Post by icarus74 on 2011-06-07
Okay, I think I've found the solution, so I thought of sharing.

In fact in my case Natty (11.04) Desktop 64amd, the thingy around SHMEM was already enabled, and all I had to do was install gsynaptics, and I am able to use it, and with immediately usable.

Of course, finding the right values to set, is another task.

---

