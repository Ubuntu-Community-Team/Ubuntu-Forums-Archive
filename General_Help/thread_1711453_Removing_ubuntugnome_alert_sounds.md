---
title: "Removing ubuntu/gnome alert sounds"
date: 2011-03-21
forum: General Help
---

### Post by KeiNivky on 2011-03-21
There are some really annoying sounds located in the directory /usr/share/sounds/ubuntu (or gnome instead of ubuntu). I am not using gnome anymore, but they keep playing when I try to close a window, or when I click some things. Maybe it's because I still use gdm.
How can I disable these alert sounds via command line? I thought about just deleting the files, but that seems to be messy since the system will keep trying to play the sounds (but will not find them).

---

### Post by An Sanct on 2011-03-21
Maybe you could run
```
gnome-volume-control
```
and there under the "Sound Effects" tab set the "sound theme" :) or just mute the "Alert volume".

---

### Post by tredegar on 2011-03-21
Try System - Preferences - Sound
Under the "Sound Preferences, Sound Effects" tab uncheck "Enable window & button sounds".

If that fails, I have no problem with quick & dirty hacks: Just rename all those sound files with .hated extension: They will not be found, will not be played, and you'll notice no difference in performance.

Hope this helps.

---

### Post by An Sanct on 2011-03-21
> **tredegar said:**
> Try System - Preferences - Sound
Under the "Sound Preferences, Sound Effects" tab uncheck "Enable window & button sounds".

If that fails, I have no problem with quick & dirty hacks: Just rename all those sound files with .hated extension: They will not be found, will not be played, and you'll notice no difference in performance.

Hope this helps.

I don't know :), he said, he doesn't use gnome anymore (thus where to find it in gnome is pointless) - I don't even know if my volume control terminal command will help...

---

### Post by tredegar on 2011-03-21
> he doesn't use gnome anymore (thus where to find it in gnome is pointless)

The system sounds, and most other system files, tend to be in the same place, regardless of the desktop you use.

You can go there (in the filesystem), and disable them.

Edit: See this recent [link]("http://ubuntuforums.org/showthread.php?t=1709389")

---

### Post by KeiNivky on 2011-03-22
> **An Sanct said:**
> Maybe you could run
```
gnome-volume-control
```and there under the "Sound Effects" tab set the "sound theme" :) or just mute the "Alert volume".

I tried that. Curiously  the sound effects tab is already set at "none" and the volume of the alert volume is set to zero. Anyway, I marked the mute square and aparently the sounds stopped. But won't the mute do the same as deleting the files? I mean, the system will keep playing the sounds, but since the volume is low they won't be heard.

---

### Post by An Sanct on 2011-03-23
IMHO no.

**mute**: 
The sounds will not be looked for and will not be played.

**deleted files without mute**:
The sounds files will be looked for, but errors will be logged (files not found), no sounds played.

**low volume** (0)
The sounds files will be played (really loud ;)) at a volume of 0%

All bring the "same" results ... but from all three options, mute represents the best way. No superfluous logging of missing system files, no hassle.

---

### Post by satish_j on 2011-03-23
@tredegar
If we uncheck "Enable window & button sounds",does the Login sound also will be stopped??

---

### Post by An Sanct on 2011-03-24
You can disable the login screen at System>Administration>Login Screen.

---

