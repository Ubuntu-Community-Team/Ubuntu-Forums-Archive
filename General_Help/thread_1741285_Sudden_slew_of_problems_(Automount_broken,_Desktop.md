---
title: "Sudden slew of problems (Automount broken, Desktop auto-organizes, Nautilus slow)"
date: 2011-04-27
forum: General Help
---

### Post by stravant on 2011-04-27
Some time within the last week or so a whole bunch of problems suddenly appeared on my 10.10 installation, having had no problems in the past.

The primary concern is that USB storage devices have stopped auotmounting, both harddrives which are plugged in at boot-time, external (an internal ones too, so it may not be a USB problem?), and USB drives that I plug in at run-time. I have already checked the common solution to this, checking that the gconfig "auotmount stuff" key is set to true, but that doesn't seem to be the problem.

On top of that, several other issues appeared around the same time:
-My desktop seems to auto-organize itself by name whenever I log in, when it never did before.
-Nautilus is *noticeably* slow when opening folders with any reasonable amount of stuff in them (even my home folder takes almost a second to display), when even on large folders it used to be effectively instant.
-My default browser seems to be broken. When I click hotlinks in other programs such as IM clients which used to send requests to open pages to my browser, they no longer do anything.

Now, given that I've not had a single major issue in the past, I find it must not be just a coincidence that all of these things happened at the same time. Is there anything that could have happened to put all this stuff on the fritz all of a sudden?

How should I proceed to go about fixing all of these problems?

---

### Post by Hedgehog1 on 2011-04-28
Based on this combinations of issues, checking your hard drive health seems a good place to start.

Menu to System >> Applications >> Disk Utility and look at the SMART status of your hard drive.  



***The Hedge***

:KS

---

### Post by stravant on 2011-04-28
All the disks have a perfect health on the disk status thing (They're only between 5 months and 1 year old too, so I wouldn't expect them to be starting to have problems either)

---

### Post by stravant on 2011-05-07
Solved several issues I was having with this:

In "assistive technologies" "Enable assistive technologies" was set to true. Simply turning this setting off fixed almost all of these problems (my window movement is now butter-smooth where it used to be sort of jittery).

Does anyone have any idea why this setting would have such a huge effect on the system performance?

---

