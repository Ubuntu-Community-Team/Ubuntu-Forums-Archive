---
title: "Everything invisible/transparent"
date: 2010-10-24
forum: General Help
---

### Post by amorphouskev on 2010-10-24
Help please!! 

I'm running 10.10 - last night I was working around with Compiz and the transparency options when I totally effed something up. Now all I can see is my desktop. I can't click on any menus, and the only way I can tell that a menu or program has loaded is by the Running Notifier icon on Docky. 

Can any one help me fix this? Is it possible to fix?

---

### Post by amorphouskev on 2010-10-24
bump out of desperation...

---

### Post by akand074 on 2010-10-24
You could hold Alt + Scroll up to lower transparency of a particular window/panel. Also an easier way if you screwed a lot up is do this:

```
metacity --replace
```This will completely disable all of compiz, fix what you did wrong, and then run this command:

```
compiz --replace
```Problem Solved. Hope this helps. Post back if you need more help. Otherwise mark your thread as solved.

EDIT: In case you didn't know, run those commands in the Terminal, Accessories > Terminal. Also, in case you didn't know, to fix what you did, go to "Opacity, Brightness and Saturation" in compizconfig Settings manager and increase the value for the transparency you put on your panel/applications if that is what you did. Just thought I'd add some detail as I'm unsure of your knowledge.

---

### Post by amorphouskev on 2010-10-24
Thank you so much! I just crossed my fingers and went for it, cuz I could tell that the terminal was open ... but couldn't see it to know what was going on after I entered the commands.

Thanks again!

---

