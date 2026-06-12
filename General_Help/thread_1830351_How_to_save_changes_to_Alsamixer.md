---
title: "How to save changes to Alsamixer"
date: 2011-08-21
forum: General Help
---

### Post by keithk50 on 2011-08-21
Each time I boot into Ubuntu I have to mute the External Speaker within Alsamixer GUI in order to get sound.   I have made several attempts to save this setting but without success:confused:
Also read numerous threads and google search tips but no matter what I try it still results in having to open Alsamixer and manually mute the setting each time I launch Ubuntu.
Does anyone have a fix for this or suggest where to find one.
All help appreciated:D   Using 11.04.

---

### Post by wojox on 2011-08-21
You tried:

```
sudo alsactl -f /var/lib/alsa/asound.state store
```

---

### Post by ajgreeny on 2011-08-21
Normally Esc will save any changes you make in alsasmixer in terminal before you close the terminal.  Are you closing it without using Esc?

---

### Post by keithk50 on 2011-08-21
> **wojox said:**
> You tried:

```
sudo alsactl -f /var/lib/alsa/asound.state store
```

Hi wojox.   No luck I'm afraid.   Thanks for the help never the less.

Hi ajgeeny. Thanks for the tip.   No, I was not using the esc key previously before closing terminal however I did as you suggested before re-starting but nothing changed in regard to saving the Alsamixer settings.

Also installed Gnome Alsa Mixer GUI which also lets you mute the External Amp.   Still no joy!   

Its not a big issue, and I have had a lot worse problems during my adventure with Ubuntu but it is bugging me:confused:   I never get to hear that lovely startup sound:(

---

### Post by anataniel on 2011-09-01
Hey guys I fixed this by setting up my parameters in Alsamixer, then executing 'sudo alsactl store 0' in terminal and adding `alsactl restore` command at "Startup Application". All works fine for me, even its "lovely startup sound" when Ubuntu starts.
Anyway I used for help this thread [link]("http://ubuntuforums.org/showthread.php?t=1331321")

---

