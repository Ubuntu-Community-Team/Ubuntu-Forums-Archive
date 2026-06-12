---
title: "env LANG=C?"
date: 2011-05-04
forum: General Help
---

### Post by DanneStrat on 2011-05-04
Hello.

A couple of days ago I installed cairo-dock just

out of curiosity. After installing I noticed that the

"swedish" translation wasn't complete(there were both english

and swedish mixed together in the menus) so I went to the

"GLX dock" forums to see if there was a way to get english-only

in the menus.

I got a reply and the solution was to run cairo-dock with:

```
env LANG=C cairo-dock
```

Now, this worked OK for the dock itself, but for

some reason, the applications that I had launchers for in the dock

also seemed to run with "env LANG=C", all having english in the menus.

Why is that?

I know that "LANG=C" is the default locale in the applications code itself, but

why would this affect the other applications that I had launchers for(besides 

cairo-dock)?

Thanks in advance.

---

### Post by blimbo on 2011-05-04
Where did you make this change, in the launcher menu properties?

What happens if you do 'echo $LANG' from a terminal?

---

### Post by DanneStrat on 2011-05-04
> **blimbo said:**
> Where did you make this change, in the launcher menu properties?

What happens if you do 'echo $LANG' from a terminal?

I made the change to the "cairo-dock" launcher in the main menu

and also in the menu for "autostart" so that it would always start with 

that argument.

"echo $LANG" give the output "sv_SE.utf8".

---

### Post by DanneStrat on 2011-05-04
Does anybody know why this happens?

---

### Post by DanneStrat on 2011-05-05
I figured it out.

It was supposed to be like that.

Thread solved.

---

