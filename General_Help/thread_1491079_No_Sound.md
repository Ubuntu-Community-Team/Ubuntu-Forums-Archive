---
title: "No Sound?"
date: 2010-05-23
forum: General Help
---

### Post by Pioneer5000 on 2010-05-23
I have lost sound after a reboot, also having issues when installing new software?

The icon for sound in the gnome panel is showing the volume at mute but even when I turn it up it doesnt change and im not getting any sound at all.

Any suggestions?  Anyone else having any issues?

---

### Post by Pioneer5000 on 2010-05-23
I think this issue has to do with oss4-dkms

If that helps?

I tried uninstall and then reinstalling but getting this error message when re-installing.

---

### Post by Pioneer5000 on 2010-05-23
This is what im getting:

---

### Post by Pioneer5000 on 2010-05-28
Bump.

Does anyone know how I can fix this as I still dont have sound. I dont want to have to completly reinstall Ubuntu....

---

### Post by pr0t3g3 on 2010-05-28
I'm having more or less the same problem... the difference is, that it's stuck at the last volume setting.. I cannot adjust it... I'm afraid that if nobody replies to my thread I will have no choice.  You might want to consider the same thing.  
Reinstalling your os that is ;D

---

### Post by Pioneer5000 on 2010-05-28
This is so weird, I tried uninstalling oss4-dkms again and this time it worked properly!

```
sudo dpkg --purge oss4-dkms
```

Then I just made sure that pulse audio was installed, rebooted and I now have sound back.

---

### Post by badefanti on 2010-06-04
could this be a reason why i lost sound in kubuntu ?

i do not know how or where to make the correction you mentioned.  could you please give me an idiot's step by step direction.  thanks

---

