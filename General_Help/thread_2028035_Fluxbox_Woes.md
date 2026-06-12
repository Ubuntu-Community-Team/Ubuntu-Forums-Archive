---
title: "Fluxbox Woes"
date: 2012-07-17
forum: General Help
---

### Post by nonedrinkwater on 2012-07-17
Whenever I load up file manager, fluxbox freaks out and removes the right click-desktop menu, and it only shows the "change background" menu. 

how do i fix this?

---

### Post by Bigtime_Scrub on 2012-07-17
Which file manager are you using?

---

### Post by m_duck on 2012-07-17
I guess you are using Nautilus (the default Ubuntu file manager) as your file manager in Fluxbox? There are two solutions - you can either launch Nautilus with the following:```
nautilus --no-desktop
```This will stop it handling and messing up the desktop.

Alternatively, you could use an alternative file manager; two popular ones being Thunar or PCManFM.

---

### Post by nonedrinkwater on 2012-07-17
> **m_duck said:**
> I guess you are using Nautilus (the default Ubuntu file manager) as your file manager in Fluxbox? There are two solutions - you can either launch Nautilus with the following:```
nautilus --no-desktop
```This will stop it handling and messing up the desktop.

Alternatively, you could use an alternative file manager; two popular ones being Thunar or PCManFM.

is there a way to force fluxbox into defaulting thunar instead of nautilus?

---

### Post by m_duck on 2012-07-18
I imagine so... How do you access the file manager generally? Menu, run dialogue, automatically opened with other programs?

(Disclaimer: I'm an Openbox user)

---

### Post by andrew.46 on 2012-07-19
> **nonedrinkwater said:**
> is there a way to force fluxbox into defaulting thunar instead of nautilus?

Not a default as such but you can set your desired file manager in *$HOME/.fluxbox/menu* and then set up a key combination to open it (if desired) in *$HOME/.fluxbox/keys*.

---

### Post by m_duck on 2012-07-19
> **andrew.46 said:**
> Not a default as such but you can set your desired file manager in *$HOME/.fluxbox/menu* and then set up a key combination to open it (if desired) in *$HOME/.fluxbox/keys*.
That's the sort of thing I was going to be getting at, but thanks for saving me the research!

---

### Post by nonedrinkwater on 2012-07-21
> **Bigtime_Scrub said:**
> Which file manager are you using?

nautilus

---

### Post by andrew.46 on 2012-07-22
> **nonedrinkwater said:**
> nautilus

Nautilus always seemed a little heavy for such a lightweight desktop, have you considered using thunar (my own choice) or pcmanfm?

---

### Post by meditatingfrog on 2012-10-03
Thanks to mduck and andrew.46 , your information helped me solve the problem as well.

And nonedrinkthewater for posting \o/

---

