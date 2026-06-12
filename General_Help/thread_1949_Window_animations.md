---
title: "Window animations"
date: 2004-10-24
forum: General Help
---

### Post by Dracontopes on 2004-10-24
I want to turn off the window animations, like maximizing and minimizing. I have disabled the animations in GConf, but they still happen. 

Can they be turned off?

---

### Post by Dracontopes on 2004-10-24
They are really annoying me :)

---

### Post by beesee on 2004-10-25
[QUOTE=Dracontopes]Can they be turned off?[/QUOTE]
Unfortunately, no.  Although awhile ago someone did make a patch that disables those animations.  If you feel like recompiling metacity you could google around and see what turns up.

---

### Post by ErikN on 2004-10-25
Gconf-editor, enable reduced_resources. The key is in apps -> metacity -> general.

---

### Post by Dracontopes on 2004-10-27
Thank you, I will try this as soon as I get home.

:)

---

### Post by nblit on 2006-12-26
Steps to disable window animation
1. Open terminal and enter ```
gconf-editor
```
2. Browse to ```
apps/metacity/general
```
3. locate the **reduced_resources** key and make sure its checked.

If the reduced_resources key does not exist perform the following:
1. Right click on an empty are of the right pane and select New Key from the menu.
2. In the name area enter ```
/apps/metacity/general/reduced_resources
```
3. Select **Boolean** in the Type field
4. Set the value to **True**


Once your done i recomend restating gnome using ALT-CTRL-BACKSPACE


Disclaimer:
If reduced_resources is set to true, metacity will give the user less feedback by using wireframes, avoiding animations, or other means. This is a significant reduction in usability for many users, but may allow legacy applications to continue working, and may also be a useful tradeoff for terminal servers. However, the wireframe feature is disabled when accessibility is on. 

Enjoy

---

### Post by geoffDeGeoffGeoff on 2007-12-04
Unfotunately the wireframe you get when you change window size after setting reduced_resources is more annoying than the horrible flash when you minimize/maximize windows.

---

