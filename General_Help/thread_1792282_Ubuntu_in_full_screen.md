---
title: "Ubuntu in full screen?"
date: 2011-06-28
forum: General Help
---

### Post by Coolmariorocks on 2011-06-28
on my other computer there is a lot of dark space like a square. but i can see ubuntu and it works just fine but i want to know if i install ubuntu on my laptop will it be in full screen like windows 7 currently is? (There is no dark spots on the screen)   I hope you guys know what i talking about.

---

### Post by wolfen69 on 2011-06-28
What you are experiencing with your other computer is not typical. Your laptop install should be fine and full screen. After doing *many* installs of ubuntu, it's always been "full screen".

---

### Post by mcduck on 2011-06-28
> **Coolmariorocks said:**
> on my other computer there is a lot of dark space like a square. but i can see ubuntu and it works just fine but i want to know if i install ubuntu on my laptop will it be in full screen like windows 7 currently is? (There is no dark spots on the screen)   I hope you guys know what i talking about.

Impossible to say without knowing more about your hardware.

Anyway, what you are seeing is caused by the OS running at low resolution, and the laptop's screen simply displaying it as it is (without scaling it to full screen). LCD displays only have one resolution they can show and anyhting else must be either scaled to the display's native resolution or displayed pixel-per-pixel but with black areas to fill the rest of the screen.

The reason why you aren't getting a correct resolution would be related to your graphics card, so if installing Ubuntu would make things work correctly depends on the graphics card you have and if there is a decent Linux driver for it.

---

### Post by nzjethro on 2011-06-28
Please run the command

```
xrandr
```

in a terminal, and post the output here.

---

