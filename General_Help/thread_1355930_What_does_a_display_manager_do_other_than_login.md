---
title: "What does a display manager do other than login?"
date: 2009-12-15
forum: General Help
---

### Post by bailout on 2009-12-15
I am planning on doing a minimal install on my netbook and want to keep it as simple and lightweight as possible. As I am thinking of either using lxde or xfce I was considering slim as an alternative to gdm/kdm. But tbh I am not sure what they do other than provide a graphical login page.

Would I lose any functionality if I just logged in on the command line and then typed startx?

---

### Post by nmaster on 2009-12-15
bump.  i was wondering the same thing.  i'm thinking of doing a minimal install one of my father's old machines.

---

### Post by Ylon on 2009-12-15
If X goes crash for whatever reason, gdm will reload it.

Also it check if X boot correctly, if it don't, gdm warn you with the failsafe menu (reconfigure xorg etc.)

---

### Post by nmaster on 2009-12-15
hmmm... i guess thats useful.  i was thinking of using xdm, btw.

---

### Post by wojox on 2009-12-15
> **bailout said:**
> 
Would I lose any functionality if I just logged in on the command line and then typed startx?

No it's possible. You just need an .xinitrc file in your home directory. Only options you lose are fail-safe gnome or something.

---

### Post by wojox on 2009-12-15
> **neal.m.master said:**
> hmmm... i guess thats useful.  i was thinking of using xdm, btw.

xdm is fine.

---

