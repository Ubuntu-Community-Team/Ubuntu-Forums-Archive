---
title: "Help - Installed fresh 11.10 and HDMI Sound not working"
date: 2011-10-17
forum: General Help
---

### Post by mmars15 on 2011-10-17
Please can someone help me.  I have an emachines 1402 Nettop with an onboard HDA Nvidia (according to alsamixer) which had Ubuntu 11.04 installed.  I remember I had to fiddle with alsamixer to get sound through my HDMI cable on version 11.04 but cannot remember what I did.  It was all working with 11.04 until I decided to install a fresh Ubuntu 11.10 onto the emachines 1402 nettop.  Now I cannot get sound through the HDMI cable.  I have checked that all s/pdif's are unmuted in alsamixer and tried all different output's in sound preferences (hdmi output/iec958 output) but cannot get any sound through the test speakers application.  I need some direction as to how to solve this and get my sound back.  Thanks!

---

### Post by mmars15 on 2011-10-18
Solved my own issue!  Had to goto additional drivers and activate the "current version" of Nvidia driver instead of the latest driver. After a reboot I heard sound. Yay!

---

