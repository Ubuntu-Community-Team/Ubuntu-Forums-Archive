---
title: "nvidia-settings MetaMode error"
date: 2012-07-26
forum: General Help
---

### Post by doriad on 2012-07-26
I installed nvidia-current (on Kubuntu 12.04). When I went to edit my settings with nvidia-settings, I get:

"Failed to set MetaMode (1) 'DFP-0: nvidia-auto-select @1920x1200 +2560+0, DFP-4: nvidia-auto-select @2560x1600 +0+0' (Mode 4480x1600, id: 150) on X screen 0."

Does anyone know what that means or how to fix it?

Thanks,

David

---

### Post by flipper T on 2012-07-26
try opening nvidia settings from terminal, using sudo:

```
sudo nvidia-settings
```

make changes & see if error still occurs.

---

### Post by doriad on 2012-07-26
Yes, it does the same thing.

---

### Post by flipper T on 2012-07-26
try deleting the .nvidia folder from your home folder, re-boot & try again.

---

### Post by doriad on 2012-07-26
So I actually just got it working by just clicking "save to xorg.conf" rather than clicking "Apply" (which is where I was getting the error). I'm kind of afraid to break it on purpose since it is working now... perhaps if it breaks again I can try your idea and report back :)

---

### Post by flipper T on 2012-07-26
oh, go on & break it !

kinda interested to find out what happens next :)

ciao

---

### Post by flipper T on 2012-07-26
> **doriad said:**
> So I actually just got it working by just clicking "save to xorg.conf" rather than clicking "Apply" (which is where I was getting the error). I'm kind of afraid to break it on purpose since it is working now... perhaps if it breaks again I can try your idea and report back :)



if you are saving to a conf, rather than applying, wont changes only come into effect on next boot ? error reoccurs then ?

---

### Post by doriad on 2012-07-26
flipperT, yes, that is correct, which is one reason why it is annoying :)

---

