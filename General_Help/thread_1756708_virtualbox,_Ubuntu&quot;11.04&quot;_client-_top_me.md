---
title: "virtualbox, Ubuntu&quot;11.04&quot; client- top menu missing"
date: 2011-05-12
forum: General Help
---

### Post by guest5 on 2011-05-12
I am running this as a client in virtualbox on windows7.  The top menu is missing, and the right click function for the desktop is missing.  The right click works in all other places it should.  Any thoughts?

---

### Post by aphatak on 2011-05-12
Well, the lack of the top menu foxed me at first, too!  If you hover over the top panel, the top menu appears in it.  If you are in your desktop, the 'Application .. Places .. System' menu shows up;  if you are in a full-screen application, the application's top menu shows up.

Come to think of it, it is not such a bad idea; you *could* think of the top menu bar of each window as wasted space.  However, when it is thrown at you out of the blue, so to speak, it can be puzzling!

---

### Post by guest5 on 2011-05-12
Yes, I understand.  What I failed to iterate properly was that the menu does not appear as it is expected to appear when hovered over.  I don't know if I need to reinstall everything, or maybe refresh the Unity deskop somehow or what.

I have worked with Ubuntu since Dapper, but would still consider myself a noob.

I do appreciate all the help.

---

### Post by LewisDowney on 2011-05-14
Same thing here. To the degree it does appear when I hover over it, it is intermittently broken or partially absent. Similarly when I hover over the icons in the Dock, a patch of static appears.

I am running Ubuntu 11.04 and Virtualbox 4.0.6 on Mac OS X 10.6.7. Numerous tweaks and adjustments to Virtualbox settings have not helped, but that is how I am attacking the problem. It just seems too basic to be a core issue with Ubuntu.

---

### Post by Netbattler11 on 2011-05-16
I also have this problem. My solution is simply to go to full screen mode. The drop down menu that appears at the bottom still works fine. 

My host is Ubuntu 11.04, my virtualbox is 4.06, and my guest is Windows XP.

---

### Post by guest5 on 2011-05-18
I just updated to virtualbox 4.08 and the problem did not go away.  
Sometimes I have the right click menu on the desktop, but mostly I do not. No memu for the desktop.  Good thing we can access our 'places' from elsewhere.  This does not happen on all pc's, just this one.


Host
Asus, Windows7, SSdrive, 12gigs ram

Guest
Ubuntu 11.04

---

### Post by kibaya on 2011-05-18
Install vistuall box guest additions and activate seamless mode this should automatically resize the client when it boots

---

### Post by wannabegeek on 2012-02-25
I also have a missing VB menu bar...nothing has worked...I have been able to manually setup the guest additions through windows cmd but what a hassle...my screen res is stuck at 800x600 too and I can't get write access to the ext3 partions I worked hard to share with the guest....

VB worked flawless when I tried on Ubuntu host and Windows guest...not the other way around is becoming a real pain in the ****....

I'd just stick with Ubuntu but my TV 's HDMI driver doesn't play well with Ubuntu....

wbg

---

