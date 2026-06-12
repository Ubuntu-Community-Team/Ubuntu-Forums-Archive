---
title: "Gnome typing is jacked up?"
date: 2012-02-01
forum: General Help
---

### Post by connor99994 on 2012-02-01
I just installed the Gnome gui on my Debian vps server. When I log into the server via tightvnc I get this issue.

When I type the "F" key it gives me an "H"

When I type the "E" key it gives me a "9" 

Every single one of my keys inserts a different key. What do I do? Could it have to do with my xstartup?

---

### Post by llamabr on 2012-02-01
That's weird.  So you're trying to log in on a login splash screen, like gdm?  At the bottom, there may be a dropdown for different types of keyboards?  My father in law did this once.  His computer was "broken" for 6 months because he accidentally clicked swedish.  Change it back to your favorite language.

---

### Post by connor99994 on 2012-02-01
I tried this and figured out that I'm on a US 105-key board (with windows keys) 

The keys are still pretty messed up. Any other ideas :)?

---

### Post by connor99994 on 2012-02-02
Bump :/. I have NO idea what to do! Somebody please help me out :)?

---

### Post by hawthornso23 on 2012-02-02
The first thing I'd try in your situation is plugging a different keyboard into a USB port and rebooting. I don't hold out high hopes that this will fix the problem, but hey - it is really easy to do and rules out keyboard hardware errors.

Next I'd check if the keyboard is working OK in BIOS setup. If not then it isn't ubuntu's fault. It is some sort of BIOS setup error and you'd need to work the problem there.

Finally I'd haul out an ubuntu live CD or USB key and boot from that. This should get you into a functional system so you can work on the problem. As the earlier poster said, sounds like your keyboard type is misidentified in a config files somewhere.

Good Luck

---

