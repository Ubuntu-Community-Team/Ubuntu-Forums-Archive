---
title: "Flubbed Theme"
date: 2010-08-21
forum: General Help
---

### Post by moore.bryan on 2010-08-21
After customizing the hell out of my Ubuntu install and trying several themes, I'm actually trying to get *back* to a pure Ambiance theme; however, no matter what settings I change in gconf-editor, the buttons remain on the right side. I've purged the light-themes package and reinstalled, as well as logged-out and restarted the entire computer to no avail.

Am I missing something?

Thanks...

---

### Post by stinkeye on 2010-08-21
Not sure what you've done but the setting in gconf is 
```
close,minimize,maximize:menu
```
in gconf editor > /apps/metacity/general/button_layout

Unless your using emerald as your window decorator.

---

### Post by moore.bryan on 2010-08-21
Thanks, stinkeye; I'm already comfortable with gconf-editor, though. I've set the button layout to "close,maximize,minimize:menu" which *should* put things to how they were originally, but it still looks like this:
[[IMG]http://imgur.com/kkoXP.png[/IMG]](http://imgur.com/kkoXP.png)
And, to boot, Chromium is the only program that shows the change. Huh?

---

### Post by moore.bryan on 2010-08-21
I've even gone so far as to delete my ~/.gconf and no change.

---

### Post by stinkeye on 2010-08-21
Oh well, best of luck hunting that one down.#-o

---

### Post by moore.bryan on 2010-08-21
Thanks... sometimes, these "unimportant" questions go unanswered for eons. It was nice of you just to drop-in! :-)

---

### Post by stinkeye on 2010-08-21
Only other place I can think of that might cause this is
~/.gtkrc
or
~/.gtkrc-2.0-gnome-color-chooser

---

### Post by moore.bryan on 2010-08-21
I have neither of those...

---

