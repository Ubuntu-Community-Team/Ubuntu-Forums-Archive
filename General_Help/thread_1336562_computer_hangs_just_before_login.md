---
title: "computer hangs just before login"
date: 2009-11-24
forum: General Help
---

### Post by MichaelBurns on 2009-11-24
On random occasions, my computer hangs just before login.  This has happened 3 times from bootup, and now just recently from logout.  More specifically:

from boot up:
grub seems to function properly.  Then, I see the rat in the circle (xubuntu logo) with the status bar (kernel loading splash?).  Then, I see a blank screen with the busy system cursor (login loading splash?) for a few seconds, which is the screen that I normally see just before the login screen.  After than, the monitor loses the signal from the computer (I here an auto-shutoff type of "click").  The computer is unresponsive to mouse and keyboard input.  I simply do a hard reboot.  (I know that I'm not supposed to do that, but what else can I do in this situation?)

from logout:
I click the logout icon in the upper-right corner and select logout from the list.  The session closes, and then, after a few seconds, the monitor loses the signal from the computer.  Again, the computer is unresponsive to mouse and keyboard, and I simply do a hard reboot.

I reiterate that this usually doesn't happen, but I would like to prevent it from ever happening.  This is actually my mom's computer, and I'm trying to convince her, my sister, and anyone else who happes to use the computer that xubuntu kicks MS Windows butt.  However, I don't think that it will look good for xubuntu if I have to tell my mom to "try rebooting;" that's so Microsoft.

a possible (but unsuspected) cause:
I have messed with some PAM settings.  In particular, I have added a line at the beginning of /etc/pam.d/gdm that allows the user named "anyone" to login without being prompted for a password:

```

auth   sufficient   pam_succeed_if.so user = anyone

```

However, I will point out that this does seem to be working exactly the way I wanted it to, so I don't suspect this to be the problem, especially since the problem is infrequent and intermittent, and I *usually* experience a successful login (to "anyone").

---

### Post by MichaelBurns on 2009-12-14
bump

---

