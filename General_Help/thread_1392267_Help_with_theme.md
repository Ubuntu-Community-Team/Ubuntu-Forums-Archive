---
title: "Help with theme"
date: 2010-01-27
forum: General Help
---

### Post by Ske7ch on 2010-01-27
Well, I installed some time ago a Mac OS theme and now I decided to use another theme but the problem im having is that everytime I open a window the Maximize, Minimize and Close bottons are all on the left side of the window...How do I change them back to their original positions?

Thanks!

---

### Post by Ginsu543 on 2010-01-27
You can do that by opening the Configuration Editor in Applications --> System Tools. Then, go to apps --> metacity --> general. There you will see a setting called "button_layout." If the Maximize, Minimize, and Close buttons are all on the left side, then the value for "button_layout" should read "close,minimize,maximize:menu". If you change it to "menu:maximize,minimize,close", that should put the buttons back on the right side.

---

### Post by Ske7ch on 2010-01-28
Well im looking for Config Editor everywhere and I cant find it. Checked the Software Center and I do have it installed but I cant seem to find it.

---

### Post by raktarok on 2010-01-28
Press Alt+F2, and type gconf-editor. That should do it..

There should be a menu entry for that tool, maybe its hidden in yours. Fire up the main menu editor (right click the menu and you will have it) and see in the section system tools.

---

### Post by Ske7ch on 2010-01-28
Got it!!

Thanks guys, much appreciated!

---

