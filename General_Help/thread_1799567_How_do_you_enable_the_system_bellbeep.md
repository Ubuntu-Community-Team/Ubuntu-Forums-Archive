---
title: "How do you enable the system bell/beep?"
date: 2011-07-07
forum: General Help
---

### Post by fpgdu on 2011-07-07
I really want to enable it...

---

### Post by fpgdu on 2011-07-07
Sorry, I should have mentioned that the beep currently makes a sound. For instance, when i type

```
printf("\a")
```

it makes a tap noise from my laptop's stereo speakers. It's supposed to ring the system bell.

---

### Post by grahammechanical on 2011-07-07
I do not know if this is what you are looking for but go to System Settings and load the Sound utility. It has some options for system sounds.

Regards.

---

### Post by fpgdu on 2011-07-07
> **grahammechanical said:**
> I do not know if this is what you are looking for but go to System Settings and load the Sound utility. It has some options for system sounds.

Regards.

"System settings"???

---

### Post by Muster Mark on 2011-07-08
I think the application you are looking for is simply called "Sound"

I am on 10.10, so this may have changed.

---

### Post by Alwimo on 2011-07-08
Click on the volume indicator, go down to Sound Preferences, then click on the Sound Effects tab and turn the volume up a bit there.

Is that what you are looking for?

---

### Post by wojox on 2011-07-08
We use to blacklist this and it's in there by default.

```
/etc/modprobe.d/blacklist.conf
```

Comment out:

```

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

```

---

