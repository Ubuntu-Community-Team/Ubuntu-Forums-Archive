---
title: "Automated horizontal scrolling"
date: 2010-05-09
forum: General Help
---

### Post by M de V on 2010-05-09
Hi all,

I have an odd problem here, for which I hope you could give me some pointers to solve it: I'm using a normal two-button wheel mouse. Now for no reason my system has started doing this: Everything is scrolled horizontally to the right, at all times, this means text fields, lists, in all applications, even though the mouse does not even support this. This is beyond annoying of course, I just can't figure out how to put a stop to it.

I have read a bit about configuring input devices via xorg.conf.d and tried setting

Option "HorizEdgeScroll" "0"

to disable horizontal scrolling altogether, but no avail. Maybe it was in the wrong section.

xev outputs the following at all times:

ButtonPress event, serial 33, synthetic NO, window 0x4000001,
    root 0x15a, subw 0x0, time 568687, (101,69), root:(113,163),
    state 0x10, button 7, same_screen YES

"Button 7" appears to be a horizontal scroll in right direction, which is done constantly, as if I was scrolling to the right at all times. Very odd.

Any ideas? Help would be appreciated :)

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux voltaire 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=87b777e1-b9ee-4a88-a541-6aaf5b169fe6 ro quiet splash
Build Date: 23 April 2010  05:11:46PM

This is using GNOME.

Cheers!

---

