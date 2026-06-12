---
title: "HOWTO:  Change location of iTunes folder in Windows"
date: 2010-03-24
forum: General Help
---

### Post by perky on 2010-03-24
Situation:  Running out of space on a Virtual Machine (fixed size) and iTunes media location is either within 'My Music' or 'My Documents' somewhere.

Problem:  Apple's [solution]("http://support.apple.com/kb/ht1364") to changing iTunes media location by checking 'Keep iTunes media organized' and 'Copy files to iTunes Media folder when adding to library' is impractical on a VM when music is in /home shared over the VM.

Solution:  Change location of 'My Music' in the Windows VM.

Steps:
1.  Install TweakUI in Windows and close iTunes (and any other program using 'My Music').
2.  Cut and paste the 'My Music' folder to the new drive.
3.  Open TweakUI and within it navigate to My Computer > Special Folders > My Music > Change > Browse to new 'My Music' location > OK (ignore warning about Windows breaking...) > exit TweakUI.
4.  Open iTunes and enjoy :)

Note:  (tested on XP.) I changed the location of 'My Documents' instead, but changing 'My Music' should work and might be better for some.

---

