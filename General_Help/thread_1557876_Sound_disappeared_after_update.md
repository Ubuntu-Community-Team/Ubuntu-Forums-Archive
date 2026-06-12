---
title: "Sound disappeared after update"
date: 2010-08-21
forum: General Help
---

### Post by Kranix on 2010-08-21
I recently installed a number of updates using update manager. I then shut down my computer, was away for about an hour, and booted my Lucid laptop...

THE SOUND IS GONE!

I ran aplay -l and it said this:

device_list:223: no soundcards found...

What should i do?!

---

### Post by Kranix on 2010-08-21
Bump.

---

### Post by dino99 on 2010-08-21
"no card found", so check if paprefs and gnome-alsamixer are installed, if not install them then set alsamixer prefs: apps sound alsamixer

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by philinux on 2010-08-21
> **Kranix said:**
> I recently installed a number of updates using update manager. I then shut down my computer, was away for about an hour, and booted my Lucid laptop...

THE SOUND IS GONE!

I ran aplay -l and it said this:

device_list:223: no soundcards found...

What should i do?!

Run this. Use copy and paste.
```
lspci | grep Audio
```

---

### Post by Kranix on 2010-08-21
> **philinux said:**
> Run this. Use copy and paste.
```
lspci | grep Audio
```

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
```

---

### Post by dino99 on 2010-08-21
have you read info given by the link ive posted earlier, and followed the "alsa" section to add the good settings for azalia ?

---

### Post by Kranix on 2010-08-21
> **dino99 said:**
> "no card found", so check if paprefs and gnome-alsamixer are installed, if not install them then set alsamixer prefs: apps sound alsamixer

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

paprefs - not installed.

gnome-alsamixer - installed.

Would installing paprefs solve this?

---

### Post by Kranix on 2010-08-22
ehhhhhh....

Bump?

---

### Post by Kranix on 2010-08-22
Bump again.

---

### Post by Kranix on 2010-08-22
Triple bump.

---

### Post by Kranix on 2010-08-22
I guess i have to quad bump.

---

### Post by Kranix on 2010-08-22
Why no replies?

---

### Post by Kranix on 2010-08-22
No people are posting!

If i have no more replies by tommorow, im asking a mod to delete this thread and then i will make a new one.

---

### Post by Kranix on 2010-08-24
Bump.

If i do´nt have replies in a few days time, i think im just gonna throw my ubuntu CD into the drive again.

---

