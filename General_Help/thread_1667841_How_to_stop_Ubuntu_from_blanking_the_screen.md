---
title: "How to stop Ubuntu from blanking the screen"
date: 2011-01-15
forum: General Help
---

### Post by nrundy on 2011-01-15
I have both Computer and Display set to NEVER SLEEP in power management. yet after about five minutes of inactivity, Ubuntu always blanks out the screen (i.e., just a black monitor screen but the monitor power light is still on).

How do I stop this? I want to continue to see what is on my desktop--I do not want the screen to blank out ever.

---

### Post by Rubi1200 on 2011-01-16
System > Preference > Screensaver and adjust according to your needs.

---

### Post by DeMus on 2011-01-16
The OP has done that already. What he needs extra is this:

With "xset -dpms" it is possible to switch off dpms
With "xset s noblank" it is possible to stop the screen from being blanked.
Add this to .bashrc (in your home folder) and make sure the file is executable.

---

### Post by Rasa1111 on 2011-01-16
"SCreensaver" and "power management" settings are different.

In "power management", set both to "never".

and in "screensaver", slide the bar all the way to the right (2 hours)
and uncheck both boxes (if you want).

That should do it.

---

### Post by Schuby007 on 2012-02-20
> **DeMus said:**
> The OP has done that already. What he needs extra is this:

With "xset -dpms" it is possible to switch off dpms
With "xset s noblank" it is possible to stop the screen from being blanked.
Add this to .bashrc (in your home folder) and make sure the file is executable.

DPMS is used to turn the display ON or OFF. I don't think that is the OP's problem here. And "xset s noblank" just sets the screensaver preference to not blank so instead it will show a giant "X" on the screen, which I don't think is what the OP wants either...

The XSET setting that fixed my problem is "xset s off", which effectively disables the screensaver. And, by appending that command to the bottom of your .profile file in your home directory you will automatically disable the screensaver every time you log in xD
cheers.

---

