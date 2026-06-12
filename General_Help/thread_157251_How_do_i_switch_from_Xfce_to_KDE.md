---
title: "How do i switch from Xfce to KDE?"
date: 2006-04-08
forum: General Help
---

### Post by junglemike on 2006-04-08
Hi I'm new user. I have old computer, specs are at the bottom. At first I installed Xfce. Even though it is fast - It is hard to get used for me. Than I installed a KDE, In the process of removing unnecesary services - i removed KDM,  - it's OK for me to log on from console. But when i type "startx " - it runs xfce4 and not kde (i didn't remove kde itself). How do i tell him to run kde?

---

### Post by taurus on 2006-04-08
Instead of typing startx to start your X session, how about typing
```

startkde

```

---

### Post by junglemike on 2006-04-08
I tried it, it says "unable to open display ""
Does it meand that kdm is necessary to run kde?

---

### Post by taurus on 2006-04-08
See if you have any GUI login screen running in the background.  Run this from a prompt and look at the processors on the right...
```

ps -A | more

```
Hit the space bar for the next 24 lines...  Make sure you don't have any kdm or gdm running.

---

### Post by junglemike on 2006-04-09
I run this command ps -A | more  and didn't see any dkm or gdm.
So I had to run sysv-rc-conf again and enable KDM - this is the only way i was able to boot to KDE again (there is session type at the bottom that let's me choose xfce or kde).

But question is still open: 
How do i choose what windows manager is default one.
I wan to try other window manager (because my computer is slow with kde - see specs at the bottm)
But i'm afraid to do so - i  don't know if i'll be able to switch back if i don't like new gui.
Hope anybody can help me.

---

### Post by thesisko on 2006-04-09
Have you tried editing your .xinitrc file in your home directory?  If it says startxfce4 or is blank, replace it with startkde.

---

