---
title: "Window Border problems..?"
date: 2009-07-30
forum: General Help
---

### Post by nickicksu on 2009-07-30
Hi everyone. Starting today, whenever I start up my Ubuntu, any windows that I open have transparent window borders, a strange theme for maximizing/minimizing/closing, and are just plain ugly :(. To fix this problem, I tried to use metacity --replace, and surprisingly, it worked, but none of my compiz effects would work (like widget layers, wobbly windows, etc) and I can't really get compiz without using a crappy window border, or having a good window border with no visual effects. Any ideas/solutions would be much appreciated :D:D:D
EDIT: Also, nothing in Appearance that I modify does anything, and I'm stuck with default mouse until I change or use metacity --replace

---

### Post by CatKiller on 2009-07-30
That's because you're using Emerald to decorate your windows. If you do *metacity --replace*, Metacity will be both your window manager and your window decorator. You could either go into Emerald Theme Manager to choose a theme more to your liking (there are some nice ones available) or go into CompizConfig Settings Manager and change the Command setting of the Window Decoration plugin to metacity.

---

### Post by nickicksu on 2009-07-30
> **CatKiller said:**
> That's because you're using Emerald to decorate your windows. If you do *metacity --replace*, Metacity will be both your window manager and your window decorator. You could either go into Emerald Theme Manager to choose a theme more to your liking (there are some nice ones available) or go into CompizConfig Settings Manager and change the Command setting of the Window Decoration plugin to metacity.
And how would I do that?

---

### Post by CatKiller on 2009-07-30
> **nickicksu said:**
> And how would I do that?

Which?

Emerald Theme Manager is at System &#8594; Preferences &#8594; Emerald Theme Manager.

CompizConfig Settings Manager is at System &#8594; Preferences &#8594; CompizConfig Settings Manager, provided you've installed the compizconfig-settings-manager package in Synaptic.

---

