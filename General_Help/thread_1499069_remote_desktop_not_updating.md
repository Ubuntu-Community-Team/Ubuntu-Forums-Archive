---
title: "remote desktop not updating?"
date: 2010-06-01
forum: General Help
---

### Post by freebeer on 2010-06-01
I recently installed Ubuntu 10.04 and enabled Remote Desktop access on the machine.  Using vncviewer from my XP box, I can log in just fine, but I'm not getting the screen refreshed in vncviewer.  The Ubuntu box is getting all the mouse movements and clicks (I can see the ubuntu box from the XP box - I can see the mouse cursor moving around and I can see the menus being selected, etc.) Those events are just not showing up in the vcnviewer, though.  TightVNCviewer version 1.3.10.

FWIW, prior to installing 10.04 I had 7.10 on that box and everything worked as it should.  No changes on the XP box.  I doubt it's relevant, but I had a power supply failure on the Ubuntu box, replaced that as well as the mother board - some of the capacitors looked like they were ready to go.  I believe the new motherboard has a different nvidea-based on-board video chip.  Since I had to replace the PS and mobo, I figured I might as well install 10.04 while I was at it.

---

### Post by gsgleason on 2010-06-01
Disable desktop effects.  This is an issue with compiz and vnc - here is a bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)

---

### Post by freebeer on 2010-06-01
Ah!  Thank you kindly (and for the link).


Update: I found a simple way of fixing this issue should anybody else care.  Go into System -> Preferences -> Appearance.  Select the Visual Effects Tab.  Click on NONE.

A simple way to disable the desktop effects and vncviewer now seems quite happy.

---

### Post by pizza-is-good on 2011-06-27
I just recently ran into the same problem. Both PC running 10.04. Controlling machine would nor refresh.
Disabling desktop effects did it. Not too much of a hassle since it is a media server. 

To the OP, please mark this thread as solved.

---

