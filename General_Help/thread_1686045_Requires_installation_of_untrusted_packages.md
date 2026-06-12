---
title: "Requires installation of untrusted packages"
date: 2011-02-11
forum: General Help
---

### Post by Chrskyes on 2011-02-11
As much as I hate for my first post on the fourms to be me leeching off of the site, I simply cannot figure this out (and I'm sure it's an extremely easy fix too)

I've been using Ubuntu for a couple of months, and it's my first install of a Linux distro and I was bound to screw up some settings along the way here, so bare with me..

Whenever I go to [Update Manager], I am not able to update.
This error message is always returned to me

```
 Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Details:
google-talkplugin sun-java6-jdk ttf-droid ttf-umefont 
```I tried deselecting these updates, no luck. I also went into the settings of Update Manager, and reverted everything back to default, still no luck.

Thanks in advance!

---

### Post by Zilioum on 2011-02-11
Somebody once asked a similar question, maybe one of the solutions there will work for you: [http://ubuntuforums.org/showthread.php?t=1339490]("http://ubuntuforums.org/showthread.php?t=1339490")
Changing the servers used for downloading seemed to fix the problem for some people.

Cheers

---

### Post by jerrrys on 2011-02-11
open up a terminal and enter 
sudo apt-get update
 if that works follow with 
sudo apt-get upgrade

---

### Post by Chrskyes on 2011-02-11
> **jerrrys said:**
> open up a terminal and enter 
sudo apt-get update
 if that works follow with 
sudo apt-get upgrade

This worked, thanks, should have thought of that!

To other guy who replied: Thanks for the thread, I forgot to have mentioned that I did search already to no avail.

---

### Post by jerrrys on 2011-02-11
your update manager should also work now

---

