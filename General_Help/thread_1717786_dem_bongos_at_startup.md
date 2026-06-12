---
title: "dem bongos at startup"
date: 2011-03-30
forum: General Help
---

### Post by musendrophilus on 2011-03-30
I have sounds turned off with Maverick Meerkat via System -> Preferences -> Sound.

I recently discovered upon reviewing System -> Preferences -> Startup Applications there was a little program for a startup sound. I removed it.

Yet when I continue to restart Ubuntu, the sound keeps playing. How else can I address this so my computer's silent unless I decide to play something?

---

### Post by musendrophilus on 2011-04-04
Five days, no response, bumpan.

Halp plx.

---

### Post by dnairb on 2011-04-04
IIRC System --> Admin --> Login Screen

Click "Unlock" and enter your password. You can then disable the log-in sound

---

### Post by musendrophilus on 2011-04-05
Forgot to mention that I did that as well. Still have the bongos.

It's just odd.

---

### Post by dnairb on 2011-04-06
> **musendrophilus said:**
> Forgot to mention that I did that as well. Still have the bongos.

It's just odd.

Odd indeed.

You could try disabling all system sounds:
System --> Preferences --> Sound and change the sound theme to "No Sounds"

Or, if even this doesn't work, uninstall the ubuntu-sounds package.

---

### Post by tredegar on 2011-04-06
Those annoying sounds are stored in **/usr/share/sounds/ubuntu/stereo/**
Open that directory and click through the files until you find the one you hate.
Then delete it: No annoying sound will play.

Or replace the file with one you prefer, but renamed as the original ( maybe **desktop-login.ogg** )

I hate all those distracting sounds too.

Computer: Just DO AS I SAY!

---

