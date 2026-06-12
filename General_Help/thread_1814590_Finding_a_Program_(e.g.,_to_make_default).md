---
title: "Finding a Program (e.g., to make default)"
date: 2011-07-29
forum: General Help
---

### Post by Ludd1te on 2011-07-29
A legacy immigrant, I'm still getting used to working under Ubuntu (11.04) and learning where, e.g., program files are located (usr/bin, etc.).

However, I'm not great at it and could use help:
How can I find where a program is located if I'm not sure of the program's name?

My velleity became a post because I'm trying to make Document Reader the default program to launch .pdf files.  But, the program itself mustn't be named similar enough to "Document Reader" for me to use things like "which document-reader" to find it.

Um, maybe I'd eventually stumble on the name of the program by trying bazoodles of iterations ("dreader" "docreader" "dr" "drat" "darnnit" "dog-vomit!") or figure out which is it in the /bin folder.  But maybe you all could help me out?  Thanks!

---

### Post by wojox on 2011-07-29
You mean Evince?

---

### Post by Ludd1te on 2011-07-29
[FONT=Verdana]Yep!  "which evince" returns "/usr/bin/evince", which in turn launches it--[COLOR=Blue]***thanks***[/COLOR]!  :  )  (Although the copyright and URL direct to Evince authors and site, [/FONT][FONT=Verdana]"About" says it's "Document Viewer 2.32.0" which threw me off.[/FONT][FONT=Verdana])

Not to be greedy, but in addition to finding the path to this particular program, I'd love to know if there is a general way one can find the path to an application on my machine.  E.g., is there somewhere within a program (I guess not under About) where this is given?

Thanks again.
[/FONT]

---

### Post by CatKiller on 2011-07-29
The names used in the launchers are defined in their respective .desktop files, which are generally in /usr/share/applications. You can see which command is actually run by each launcher by dragging-and-dropping the launcher on a text editor window.

---

### Post by Habitual on 2011-07-29
> **Ludd1te said:**
> ...How can I find where a program is located if I'm not sure of the program's name?

terminal > 
```
which (first letter or more) +tabtabtab
```

try it with 
```
which emp tabtabtab
```

You see this or similar:
empathy           empathy-accounts  empathy-debugger

then it's ```
which empathy
```
/usr/bin/empathy

HTH

---

### Post by Ludd1te on 2011-07-29
Excellent!  Thank you Habitual, CatKiller, and Wojox for your very informative responses!  : D

---

### Post by ubername on 2011-07-30
If you right click on an installed package in Synaptic and select 'properties', there is a tab called 'installed files' which shows you where all the files required for that package are installed.

---

### Post by Ludd1te on 2011-07-30
Fantastic, Ubername!  Thanks!

Inspired by these general strategies, I also noticed that mousing over an active process in the System Monitor reveals the address of the application.

Parenthetically, it's great to see the vitality and warmth of the open source community--shown not only here but also in the strength of products like Ubuntu, GNOME, etc. Stallman should be proud!

---

