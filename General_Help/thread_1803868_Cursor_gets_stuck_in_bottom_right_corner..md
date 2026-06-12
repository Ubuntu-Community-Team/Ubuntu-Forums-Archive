---
title: "Cursor gets stuck in bottom right corner."
date: 2011-07-14
forum: General Help
---

### Post by ericools on 2011-07-14
I have a strange problem.  I googled and can't find quite the same thing.

Whenever I move my cursor to the bottom right corner of my screen it sticks there for a moment, but then lets me move it again.  No issues as long as I don't go in the corner.

The effect seems to affect an area 4cm long and 2cm tall regardless of what is showing on the screen.  Changing to proprietary drivers has no effect.

Does anyone have any idea what could cause this?  


System:
Ubuntu 11.04 - Gnome Shell
ATI HD-5770 GPU

---

### Post by pszpak on 2011-07-20
I have the same issue and the same video card. No solutions so far.

---

### Post by EA8CRA on 2011-07-21
I'm currently running Ubuntu 10.04 with an ATI HD-6450 and I'm having the same issue. It's quite annoying when trying to work with applications which have buttons in the lower right corner :-?

---

### Post by echogene on 2011-08-02
I have this problem too, also with an HD-5770. It happens on any resolution.  It only seems to occur when the pointer is moving out of the bottom right, and not in.  It is a very strange and annoying problem.  It sounds at first guess like the ATI drivers are being special.  I also have no solutions to offer. : (

---

### Post by thomasmc on 2011-08-14
I have exactly the same problem, but I'm using an ATI 5450 card, and Linux Mint Debian Edition.


I just went to the ATI website and downloaded the latest driver, but that did not fix the problem when I rebooted.

---

### Post by thomasmc on 2011-08-14
According to the ATI forum, this is a bug in the 64 bit drivers, and still hasn't been fixed.

I did search around, and found a temporary workaround. It's not pretty, for me the cursor now flickers a lot, and disapears when it isn't moving, but at least it doesn't get stuck in the corner anymore.

edit (as root) /etc/X11/xorg.conf
add this line to the Device section:

           Option "SWcursor"

This causes the cursor to be drawn by software, instead of hardware, which is the default.

Hopefully the next release of the Catalyst software will fix this.

---

