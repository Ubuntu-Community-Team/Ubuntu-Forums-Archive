---
title: "Libre Office templates &quot;disappearing&quot;"
date: 2011-05-16
forum: General Help
---

### Post by Paddy Landau on 2011-05-16
I have a number of templates in LibreOffice (originally from OpenOffice).

I open a template (File > Template > Edit), make some changes, and save it under a different name (File > Save As...).

Under Open Office, this process used to save a new template. Then, I would have two different templates.

In Libre Office, however, the results are quite bizarre.

I have done this with four different templates. Here is what I see when I try to use the templates (Ctrl-Shift-N, or File > New > Templates and Documents):


[LIST]
[*]One template worked correctly: I can see the old and new templates, and they both open correctly.
[*]One template shows only the old version, which opens correctly, but the new template is not shown.
[*]Two templates show only the old versions, but bizarrely, they open the new templates.
[/LIST]

Puzzlingly, if I look under Nautilus, all eight templates are in the correct folder (with the correct names and extension .ott); and, if I double-click them, they all open correctly in LibreOffice.

So, they have saved correctly; but LibreOffice is completely confused.

If you can, please help me fix this problem, so all the templates are displayed, and tell me what I must do to prevent it from happening again.

---

### Post by Hedgehog1 on 2011-05-17
Update Manager just loader a number of updates for Libre Office this morning on my PC.

I wonder if the fix for this issue is carried in the rather large update?

***The Hedge***

:KS

---

### Post by Paddy Landau on 2011-05-17
Hmm, I have no new updates outstanding; although I did install LibreOffice afresh yesterday.

As I use 10.04, which comes by default with OO not LO, I use the LO PPA:```
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu lucid main
```I don't know if this is the right PPA to use.

I've tried deleting the templates, restarting LO, restoring the templates, and using LO's template organiser with its update function, all to no avail. I'm rather frustrated with it!

**EDIT:** The version on my machine is 3.3.2.

---

### Post by Hedgehog1 on 2011-05-17
I just checked, after the updates my version in Natty is also 3.3.2.

Ok - it is not fixed yet then.

***The Hedge***

:KS

---

### Post by Paddy Landau on 2011-05-17
I have the answer.

[http://en.libreofficeforum.org/node/700](http://en.libreofficeforum.org/node/700)

Seems like it was something I did wrong, though it was by no means obvious!

---

