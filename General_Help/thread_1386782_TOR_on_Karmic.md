---
title: "TOR on Karmic"
date: 2010-01-21
forum: General Help
---

### Post by gavinUK on 2010-01-21
Has anyone got sources for TOR that work for Karmic, I'm in Oman and the tor project site is blocked so I can't check there, bit of a chicken and egg situation!!

cheers

Gav

---

### Post by Robert Lutken on 2010-01-22
hi i hope this should help you = ) it helped me loads :D

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

---

### Post by Sticky_Bit on 2010-01-29
I have been having a hell of a time getting tor installed. I have tried the step at torproject.org and how to linked in the post above but nothing seems to work. Am I doing it wrong or what? After following the steps: 
sudo apt-get install tor tor-geoipdb I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate

---

### Post by bodhi.zazen on 2010-01-29
> **feedusafetus said:**
> I have been having a hell of a time getting tor installed. I have tried the step at torproject.org and how to linked in the post above but nothing seems to work. Am I doing it wrong or what? After following the steps: 
sudo apt-get install tor tor-geoipdb I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate

You most likely need to enabe your universe repository:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

