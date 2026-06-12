---
title: "Can't get Xbox 360 controller to work in Intrepid."
date: 2009-08-18
forum: General Help
---

### Post by cafink on 2009-08-18
I have Ubuntu 8.10 and I've been trying to play games in SDLMAME using the Hori Real Arcade Pro EX joystick for the Xbox 360.  As far as I'm aware, the HRAP EX is simply considered a standard wired 360 controller (albiet without the two analog sticks), so I expected it to be pretty simple to get it working.  However, I'm having a heck of a time doing so and none of the many tutorials I've found has been much help.

When I plug the joystick into my computer's USB port, the green "ring of light" flashes constantly, which I understand is actually the expected behavior.  But SDLMAME simply doesn't recognize the controller.  I've tried running jscalibrator, but I get a "could not access the specified path(s)" error (I used sudo, so it's not a permissions issue).  I've looked in the /dev/input directory, but I don't see js0 or anything like it (all that's in there is event*, mice, and mouse*).  I ran "xinput list" and didn't see anything listed that looked like it might be the joystick.

Any suggestions on what I might need to do to get this joystick working?

Thank you.

---

