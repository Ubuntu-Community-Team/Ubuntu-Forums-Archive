---
title: "Login Screen gone"
date: 2010-01-11
forum: General Help
---

### Post by thejambi on 2010-01-11
Alright I need some help. I don't know what caused it, but as I boot into Ubuntu (9.10), the login screen never appears. Boot splash shows, then the cursor shows up but never the login screen. I haven't found anything that will reset the default gdm or login screen that works. Any help?

---

### Post by JC Cheloven on 2010-01-11
Quite obvious but anyway: did you try reinstalling the 'gdm' package? for example from synaptic...

---

### Post by efflandt on 2010-01-11
When you say "boot splash" works, are you getting the ubuntu logo and then nothing, or are you just referring to the grub menu, then blinking cursor, then nothing (with no boot activity)?  The latter seems to happen (at least for me) if using a digital monitor (DVI or HDMI) that is a different native resolution than in /etc/usplash.conf (even if the monitor is capable of the listed resolution).  I don't know why usplash does not "try" to use the usplash.conf resolution (like it does for VGA when it does not know monitor capabilities).

Can you boot a (recovery) entry, login as yourself to the console, and does **startx** work from there?  That should work if it is just a usplash.conf issue.  But if startx does not start gnome, you may have some other video issue.

What video do you have and are you using any non-standard driver (something you had to specifically install and/or configure)?

---

