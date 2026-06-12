---
title: "Sound configuration doesnt stick?"
date: 2009-12-27
forum: General Help
---

### Post by mac666 on 2009-12-27
Hey
Each time i reboot my computer i have to run alsaconf and select my soundcard, i only have one installed soundcard.

Else, i dont get any sound...

But after reboot, the setting are lost and i need to do it again.

Weird?

---

### Post by The Secret on 2009-12-27
```
gksudo gedit /etc/init.d/alsa-utils

```

Scroll down to the 378th line and comment it out.

```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by mac666 on 2009-12-27
Thanks, will give it a try!

BTW, it was line 372 for me :)

---

