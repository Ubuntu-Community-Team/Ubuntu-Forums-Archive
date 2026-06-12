---
title: "Weird blank bar at the bottom of the screen"
date: 2011-07-12
forum: General Help
---

### Post by greffenstette on 2011-07-12
Hi there!

A couple of days ago, without updating the system or installing any software (AFAIK), a weird blank bar appeared at the bottom of the screen of my Dell Latitude 2100 (check the screenshot for a better detail).

It looks like, somehow, the resolution of the screen is now smaller (1024x576) and Ubuntu doesn't recognize anymore this small band of the screen.

Any opinions/suggestions?

Thank you very much in advance!

---

### Post by ajgreeny on 2011-07-12
I can not see a blank bar in your screenshot; I don't think it has shown up when you made the screenshot, probably because the system does not even know that blank area exists.

Why have you got an **xorg.conf** file that is more or less empty, or has no configuration info in it?  Did you run a command to make such a file?

Can you restart an x-session and copy the **xsession-errors** file before doing anything else, as it can be very difficult to sort out what has caused any of the entries after you've run several applications.

Similarly the dmesg and syslog, but those after a reboot, though those two are probably not a great deal of help anyway.

If you have a live CD/USB, can you run that and see if the problem shows in that as well, which would point to a hardware problem.

---

