---
title: "Touchpad problems with openjdk java"
date: 2010-10-08
forum: General Help
---

### Post by Jamesss on 2010-10-08
I'm running Ubuntu 10.04 and openjdk-6-jdk (version 1.8.1) with processing-1.2.1 and arduino-0019. I have a synaptics touchpad and the settings are:

Mouse click with touchpad: disabled
Edge scrolling: disabled
Two-finger scrolling: enabled
Horizontal scrolling: enabled

The problem is that in both arduino and processing two-finger scrolling results in a right-click (sometimes it also scrolls, but usually not).
If I disable Horizontal scrolling, everything is fine, but obviously I have no horizontal scrolling!

Are there some java settings to adjust somewhere or is this a bug with java? 

thanks

James

---

### Post by P4man on 2010-10-08
I doubt its a java issue, but its easy enough to test it firefox or whatever?

Now not all touchpads support two finger scrolling (in fact, most dont, especially if the laptop is a year old or older). If yours doesnt support it, you will need to stick to edge scrolling.

---

### Post by qduaty on 2010-10-29
> **Jamesss said:**
> The problem is that in both arduino and processing two-finger scrolling results in a right-clickFollow my thread on Netbeans forums, [http://forums.netbeans.org/viewtopic.php?t=32834](http://forums.netbeans.org/viewtopic.php?t=32834) - maybe someone there knows the solution.

P4man - no one replaces their laptops every year. Even 5 yo Synaptics devices are known to support 3 fingers and it perfectly works on Macs, Windows, and recently on Linux too. Only Java has problems with multitouch. Or rather, both mouse wheels in use at the same time, which is unlikely for a mouse but very common with touchpads.

---

