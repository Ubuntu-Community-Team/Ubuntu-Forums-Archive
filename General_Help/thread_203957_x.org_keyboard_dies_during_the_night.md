---
title: "x.org keyboard dies during the night"
date: 2006-06-26
forum: General Help
---

### Post by heldal on 2006-06-26
It turns out that keyboard-problems arise even on a tty so the below is not specific to X. 

On a tty:

[LIST]
[*]caps/num-lock keys keeps working
[*]multiple presses on a key may eventually generate a character
[*]remains possible to switch terminal <xtrl-alt-Fn>
[*]only the active tty goes bonkers. 
[*]killing all processes on the faulty tty brings up a login-prompt, but the keyboard is not reset.
[*]resetting the tty with stty changes nothing 
[/LIST]


----------

On two computers, both upgraded from breezy to dapper I have the same problem. At night, around 1am it seems, the X-server stops responding to keyboard input. Hardware is different, one laptop / one desktop, so that is hardly the problem. There is no response with ctrl-alt-backspace and even caps/numlock keys are dead. The only way out except a reboot is to escape the x-session through the switch-user mechanism or kill the x-server via a network connection. The keyboard comes back to life once it is possible to switch to a console or a new x-server is starting. The same happens every night at the same time.

I'm not able to identify anything (cron or otherwise) that should happen at the same time every night which would affect the x-server's keyboard module.

Disabling the screensaver makes no difference.

Killing all applications leaving just a clean desktop with no apps changes nothing.

Left at the gdm login-screen the keyboard still locks up ruling out any user configuration, misbehaving gnome applets etc.

Both computers use the Nvidia module, but that shouldn't affect the keyboard given the modular nature of x.org 7.X

Nothing relevant to the keyboard is afics written to any logfile.

Suggestions?

---

### Post by heldal on 2006-07-28
It turns out that the tiger intrusion-detection scripts were to blame. During its nightly check it messes up the keyboard on the active tty or X-server. Removing the "tiger" package fixed the problem on one of my machines. I'll check which particular test in tiger is to blame on another machine later. 

To begin with I blamed the X-server. That is not correct.

---

