---
title: "Forcing Windows to Open Centered"
date: 2009-10-02
forum: General Help
---

### Post by Joseph Schwenker on 2009-10-02
Hi everyone!  I have been enjoying Ubuntu a lot, but one thing that is really annoying me is that even though I would like my windows to be centered, they always open in the top left-hand corner of the screen, forcing me to move them to the center.  I am using Metacity.  Is there any way that I can designate the center of my screen for application windows to open in?  Also, PLEASE DO NOT tell me to use Compiz.  **I ABSOLUTELY CANNOT STAND COMPIZ!**
Thanks!

---

### Post by aktiwers on 2009-10-02
You could have a look at DevilsPie
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

---

### Post by Joseph Schwenker on 2009-10-03
> **aktiwers said:**
> You could have a look at DevilsPie
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

Sweet!  Devilspie looks promising, however, how do I make it center ALL of the windows and dialogs that open?

---

### Post by wojox on 2009-10-03
Look in here Alt+F2

```
gconf-editor
```

Look in /apps/metacity/general/

focus_new_windows = smart

---

### Post by Joseph Schwenker on 2009-10-03
> **wojox said:**
> Look in here Alt+F2

```
gconf-editor
```Look in /apps/metacity/general/

focus_new_windows = smart

The only thing that the smart option does is be a smart alec!  It is already enabled, but doesn't do anything at all.

---

