---
title: "Maximize,minimize,close buttons vanished"
date: 2009-12-03
forum: General Help
---

### Post by yaqubyahya on 2009-12-03
I just fixed my resolution(thanks to Grenage)

But now another problem, My max,min and close buttons have vanished, and when i open terminal its blank, i have to run metacity --replace for it to fix it and i hav added the command to the startup, but i am not ahppy with this because it doesnt let me use my compiz desktop effects.

Does anyone maybe know hwo to fix this without using metacity --replace?

Also when it asks for a password its blank.

---

### Post by yaqubyahya on 2009-12-03
Hello? could someone help please.

---

### Post by yaqubyahya on 2009-12-03
:s

---

### Post by yaqubyahya on 2009-12-03
Hello!

---

### Post by jegerjensen on 2009-12-03
It is difficult understand your problem.  I believe you would get more response if you focused on one issue at a time, and explained more clearly what is the problem.

---

### Post by pjsmetana on 2009-12-03
I think your problem with the buttons dissapearing is the same thing I saw. Only when I double clicked around on the empty space at the top it came back from what looked like a skinny version of Maximize. Have you tried this?

Yes it will affect Compiz, because obviously, how can you even get them to activate like this.

There should be no pw needed.

---

### Post by yaqubyahya on 2009-12-03
Ok, i just rewrote my xorg.conf file to fix my resolution which worked like a charm, but now the max min and close buttons have vanished from the top right corner of every program, to fix this in terminal i run metacity --replace

But i dont want to use this because it disables my compiz fusion effects, is there any other way to fix this? so that i use my effects, and also the border of every window has vanished.

---

### Post by yaqubyahya on 2009-12-03
No, for pw, when it asks for a password when im doing administrative tasks the box is blank where i need to put my password, and yes i have tried double clicking, it doesnt work.

I really need this fixed, because compiz is the only reason i installed ubuntu. :(

---

### Post by yaqubyahya on 2009-12-03
...?

---

### Post by jegerjensen on 2009-12-03
Thanks, that was much clearer ;)  

When you issue the command "metacity --replace" all that happens is that the standard gnome window manager takes over from compiz.  Have you tried restarting compiz instead with "compiz --replace" or something equivalent?  (I'm not familiar with compiz, so I don't know the exact commands.)  

Maybe you can restart compiz from a terminal, perhaps with debug options, and get some diagnostic output?

---

### Post by yaqubyahya on 2009-12-03
Ill try and ill post the results.

---

### Post by yaqubyahya on 2009-12-03
I tried compiz --replace which restarted it but did not fix the problem, basically nothings happened.

---

### Post by jegerjensen on 2009-12-03
"compiz --help" does list a few options you could experiment with.  Unfortunately, not any debug flags.  Not for the version on hardy at least.

Maybe the compiz project offer some advice about how to debug, there may be logfiles or something you could check.

---

### Post by yaqubyahya on 2009-12-03
I have found that since i have an older nvidia graphics card, that this will happen, it told em to edit the xorg.conf file.

And to restart x-server

---

### Post by yaqubyahya on 2009-12-03
It worked!

Now i can use compiz without the borders vanishing

---

### Post by jegerjensen on 2009-12-03
What did you do?  What instructions did you follow?

---

