---
title: "Black screen after nvidia driver 185 installed"
date: 2010-01-25
forum: General Help
---

### Post by armendvisoka on 2010-01-25
Hi everyone! :)

After installing Ubuntu and seeing my resolution would only go to 800 x 600, I found this strange. A message popped up about the nVidia drivers I could downlaod that would enable me to do more so I did. I restarted and all was fine. Nice effects, high resolution.

 However, after going on XP, then going onto Ubuntu, the screen ahs gone black. The white Ubuntu logo can be seen for a while as it loads, but then the monitor goes completely blank as I hear the sound when the log-in screen appears.

As I said in my title, it was the 185 driver. Can anyone help? Thanks alot for any help, much appreicated! :D


Regards,
armendvisoka

EDIT: I'm on Ubuntu 9.10 and my graphics card is a nVidia 7600 GS 256MB.

---

### Post by cariboo on 2010-01-25
Start in recovery mode, select drop to root prompt from the menu, then at the prompt type:

```
nvidia-xconfig
```

once it has run, type exit, then select resume from the menu. This should take you to a working desktop.

---

### Post by armendvisoka on 2010-01-26
> **cariboo907 said:**
> Start in recovery mode, select drop to root prompt from the menu, then at the prompt type:

```
nvidia-xconfig
```once it has run, type exit, then select resume from the menu. This should take you to a working desktop.

I tried this but it still boots to a black screen. :/

Thanks for trying to help! Is there anything else I can do?

---

### Post by armendvisoka on 2010-01-29
bump

---

