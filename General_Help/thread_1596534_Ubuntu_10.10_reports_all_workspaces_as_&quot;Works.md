---
title: "Ubuntu 10.10 reports all workspaces as &quot;Workspace 1&quot;"
date: 2010-10-14
forum: General Help
---

### Post by gohanssjn on 2010-10-14
No matter what workspace I am on, if I over over the Workspace Switcher it says "Current Workspace 1."

It makes using devilspie to set workspaces impossible.  Any ideas how to fix this?

---

### Post by 3Miro on 2010-10-14
This is a compiz thing. Compiz creates "fake" workspaces so that everything looks like a continuous wall, that is why for the most part other apps thinks that you have only one workspace. You can use metacity instead (i.e. set desktop effects to "none"), but this will disable the desktop effects.

From what I read about devilspie, its purpose is to add some functionality to metacity only. You should probably install compiz-config-settings-manager (ccsm) and check for this functionality there (that way you can keep your effects on).

---

### Post by gohanssjn on 2010-10-14
Thanks, I see that setting it to "None" makes it work.  I'll try adding the more comprehensive Compiz package now :)

---

### Post by gohanssjn on 2010-10-14
Hmm.  Can't get it to work with viewport switching at all.

---

### Post by gohanssjn on 2010-10-14
Interesting issue.

If I have my workspaces set up as 4x1, it goes to Workspace 3.  but if I change it to 2x2, it wont go to the third workspace, below workspace 1.  Weird.

---

