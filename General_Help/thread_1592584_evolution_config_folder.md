---
title: "evolution config folder"
date: 2010-10-10
forum: General Help
---

### Post by wrixis on 2010-10-10
Does anyone know how to delete evolution configs? I tried deleting .evolution under user folder and .gconf/apps/evolution but the old configuration is still in evolution.

---

### Post by andrewthomas on 2010-10-10
did you purge and reinstall evolution?
 
```
sudo aptitude purge evolution 
```
 
followed by 
 
```
 
sudo aptitude update && sudo aptitude install evolution

```

---

### Post by wrixis on 2010-10-10
Thank, but that don't delete "user configurations". After delete .evolution folder and restar, it seems to be ok for karmik but not at all for maverick. In the indicator applet, apper the options of evolution, options that has to be there only if evolution is configutared so you have to delete also the indicator applet folder.

I'm going to tried again and if it's that, I'll mark as solved.

---

### Post by wrixis on 2010-10-10
OK. You have to delete the TWO ones and restart in the karmik case and also delete the indicator applet folder under gconf folder in order to delete the indicator options.

---

### Post by MoLE on 2011-01-26
Have a look at my forum post [here]("http://ubuntuforums.org/showpost.php?p=10400475&postcount=5").  It details how to delete the evolution configuration data from the .gconf app tree.

Cheers,

MoLE

---

