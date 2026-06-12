---
title: "Ubuntu 10.04 / ATI 5770: dual monitor problem"
date: 2010-08-30
forum: General Help
---

### Post by brad_richards on 2010-08-30
New machine with an ATI 5770, with a fresh install of Ubuntu 10.04 (lucid, 64-bit). What a mess!

As reported elsewhere, the initial install sometimes came up with a black screen, or corrupted displays, different each time. After several retries, I had a display that was corrupted but barely readable. The installed Ubuntu booted, but also had a corrupted display, just barely readable. I was just able to make out the hint that I should use the proprietary drivers, so I booted into safe mode and enabled them. Afterward, the display came up correctly.

This is ok for me, as a long-time Ubuntu user. But it really is like a trip back to the bad-old-days of Linux: you really cannot expect anyone but a geek to get through this. And the is the LTS version of Ubuntu?

I still have one unresolved problem - suggestions welcome.

I use two monitors, to provide a double-wide single desktop. When I log in, the second monitor displays random noise, and is entirely unusable. I have to use System-Preferences-Monitors to switch the second display off, then switch it back on, and then everything works fine.

---

### Post by brad_richards on 2010-09-08
Bump - any ideas why the second monitor is messed up at boot?

Note: I can open System-Administration-Monitors

- then disable the second monitor and apply

- then say "restore previous settings" 

And everything works fine until the next time I log in.

So: the setting are basically correct, there is just some problem that happens when they are first set up by the system.

---

### Post by Ellipsis on 2010-09-12
I am thinking of getting a 5770 with a dual monitor set up. Any work around to this issue? Does it work with the Maverick?

---

### Post by jamessnell on 2010-09-14
Yeah, I'm bashing my face against the wall over this one too :(

---

### Post by brad_richards on 2010-09-17
SOLVED: Open the ATI Catalyst control center and use it to confirm the settings. Assuming your desktop is set up the way you want, do the following:

1. Open: System/Preferences/ATI Catalyst Control Center (Administrative)

2. Go to the display manager

3. Make some harmless change, click "apply"

4. Change things back to the way you want, click "apply"

5. Close the Catalyst Control Center

For me, the only visible effect is that my login now appears on the second monitor. Plus, of course, the the problem of the dead screen on login is fixed.

Hope it works for everyone else as well...

---

### Post by shukle on 2010-09-19
Thanks a lot! This fixed the issue for me. I have ATI 5750.
And indeed it changed the login to happen on the 2 screen.

---

