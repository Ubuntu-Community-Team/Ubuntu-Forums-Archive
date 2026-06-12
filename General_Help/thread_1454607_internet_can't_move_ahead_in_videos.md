---
title: "internet can't move ahead in videos"
date: 2010-04-14
forum: General Help
---

### Post by oleink on 2010-04-14
Hey I've kind of ignored this until I had the major parts of my ubuntu said up. During videos I cannot click on the little bars to move ahead in the video this happens sometimes in youtube and in other stuff.  Also if an add that like stretches onto the screen comes up I might not be able to click exit.  In both cases my mouse thing turns into the little hand for clicking but it doesn't work

---

### Post by oleink on 2010-04-15
any help here?

---

### Post by oleink on 2010-04-15
has anyone else experienced this?

---

### Post by scottuss on 2010-04-15
You only waited 12 hours for an initial reply before "bumping" your post. Give it some time! :)

If you don't get any replies, maybe take it as an indication that no one else has the problem.

As it happens, I have had this problem quite a lot and it's related to Flash. I've never found a fix, I usually just put up with it.

---

### Post by oleink on 2010-04-15
Ok thanks.  I have just put up with it until recently when i cant read about the Packers haha.  Some random adds come up i cant exit out of

---

### Post by scottuss on 2010-04-15
> **oleink said:**
> Ok thanks.  I have just put up with it until recently when i cant read about the Packers haha.  Some random adds come up i cant exit out of

Some Flash based video players are coded to force you to watch the ads, so their video content is not able to be skipped by design.

---

### Post by LurkyLou on 2010-04-15
There have been some flash problems that I've been able to address by installing flashplugin-installer (& nonfree and nonfree-extrasound) via Synaptic.  -LL

---

### Post by cascade9 on 2010-04-15
I got some of those issues when I used 32bit flash on 64bit. Solved by manually d/ling and installing 64bit version of flash.

---

### Post by oleink on 2010-04-15
I see.  I couldn't find flash plugin installer.

---

### Post by LurkyLou on 2010-04-15
> **oleink said:**
> I see.  I couldn't find flash plugin installer.
I'm using Karmic Koala on a 32-bit system.  
In System->Administration->Synaptic Package Manager, you can search or scroll for it.  Notice there are no spaces (flashplugin-installer).
You might also try:
sudo apt-get update
from the command line before you check Synaptic.  this will update available packages.
Also, in System->Administration->Software Sources, be sure you've got main, universe, restricted and multiverse options checked.

---

