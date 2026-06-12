---
title: "System --&gt; Preferences --&gt; Sound Not There"
date: 2010-02-17
forum: General Help
---

### Post by kyle2595 on 2010-02-17
Hi, I am running Ubuntu 9.10 and I was wondering if there was supposed to be a Sound option under System --> Preferences?  There is nothing there for me.  Thanks!

---

### Post by kyle2595 on 2010-02-17
Never mind, Its called "Volume Control"

---

### Post by jamesisin on 2010-02-17
On my (Gnome) system Sound Preferences and Volume Control (both under System &#8212;> Preferences) are *very* different.

---

### Post by Post Monkeh on 2010-02-17
right click on your main menu and select edit menus. scroll down to your system preferences and make sure sound is ticked

---

### Post by kyle2595 on 2010-02-17
I only have "Volume Control".  How do I find out if I have a Gnome System?

---

### Post by jamesisin on 2010-02-17
System &#8212;> About Gnome

---

### Post by wojox on 2010-02-17
Right click Applications
Click Edit Menus
On the left hand side click System
Uncheck Preferences and Administration
Check Control Center and close

---

### Post by kyle2595 on 2010-02-17
That just shows the same stuff in a different way.

---

### Post by jamesisin on 2010-02-17
I guess you are replying to wojox?

In Control Center there ought to be a button for Sound to the left of Volume Control (under Hardware).

---

### Post by ajgreeny on 2010-02-17
In karmic, "volume control" as a panel applet or menu item has gone (at least it has on my system) and is now replaced with the same icon as before but which shows "Output: x%" if you hover over it with the mouse.  If you right click on the icon you can get to sound preferences, the same as in the System ->Preferences menu.

There is also padevchooser, not installed by default, but most definitely needed for some things to work properly, I found, even though I did not actually make any changes to it.

It seems to me that pulseaudio is pretty good, and getting better than it was in jaunty but not fully, or appropriately configured out of the box in karmic, but perhaps that's just my hardware, and the things I use my computer for.

---

### Post by kyle2595 on 2010-02-18
@jamesisin,  I have included a picture of the Control Center and a picture of what pops up when I click "Volume Control".  When I click "Volume Control", a window pops up that says 
"Sound Preferences", is this the same as the regular Sound Preferences?  Thanks.

---

### Post by jamesisin on 2010-02-18
Sorry.  I'm being daft.  Sound and Control Center are gone in 9.10 and ajgreeny above actually mentions this.

If you right-click on the volume applet you can choose Preferences (the dialog you shot).  This is what I mention in my post about setting the Decco device as a sound output device:

[http://www.soundunreason.com/InkWell/?p=1318](http://www.soundunreason.com/InkWell/?p=1318)

You said you are not using PA?  Link me back to that other thread if you can.

---

### Post by ajgreeny on 2010-02-19
You can, however, easily get the Gnome Control Centre back into the menus by right clicking on the menu button or bar and choosing Edit Menus, then just select it in the System section.

---

### Post by jamesisin on 2010-02-19
Odd.  Both of my 9.10 systems have Sound but not Volume Control in Control Center.  (Sound is the same dialog you get by right-clicking on the volume applet.)

---

### Post by ajgreeny on 2010-02-19
No, you're quite right jamesisin, and I hadn't noticed that Volume Control is not there.  I presume that must be because pulse allows each application to set volume separately, and therefore a system wide volume control app is thought redundant, apartvfrom the speaker **Output: #%** icon that I spoke about earlier, which is a volume control, after all.

---

### Post by jamesisin on 2010-02-19
Hmmm... I wonder then if this issue is coming from the upgrade?  He has Volume Control (left over from 9.04?) and no Sound (in the Control Center).

---

### Post by kyle2595 on 2010-02-19
I think that my sound problem was due to the upgrade because when I put in a live disc of 9.10, the sound works fine.  I was reading here: ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting))  and it said "If it turns out that your soundcard is not supported by ALSA, you have basically two different options: Get a new soundcard that is supported by ALSA, or contact the ALSA developers to request support for your soundcards."  They don't support my sound card so I think that I will just let it be for now, thanks anyway.

---

### Post by jamesisin on 2010-02-19
I'm confused.  Does the Live CD not use ALSA?

---

### Post by ajgreeny on 2010-02-20
Surely pulse depends on alsa underpinning it?  Pulse is just the sound server on the machine that manages whatever the sound system (alsa, oss etc etc) produces.

Or have I got that wrong?

---

### Post by jamesisin on 2010-02-20
> **kyle2595 said:**
> I put in a live disc of 9.10, the sound works fine.

They don't support my sound card

This is where I get confused.  If the Live CD works, and if the Live CD is using ALSA, you should be able to do an installation and it should also work.


Here is the thread about my audio problems I keep mentioning:

[http://ubuntuforums.org/showthread.php?p=8855696](http://ubuntuforums.org/showthread.php?p=8855696)

Maybe there will be something useful in there.

---

