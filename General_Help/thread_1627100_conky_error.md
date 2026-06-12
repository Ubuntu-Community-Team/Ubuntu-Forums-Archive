---
title: "conky error"
date: 2010-11-21
forum: General Help
---

### Post by antonvrg on 2010-11-21
hi i have this wierd box thing around conky, how do i make it smaller or remove?

thanks Anton.

Image:

[IMG]http://ge.tt/3gxN7d/Screenshot.png[/IMG]

---

### Post by antonvrg on 2010-11-21
anyone?

---

### Post by stinkeye on 2010-11-21
To make outlined window smaller change this in your conky config
```
minimum_size 180 100  # width length
maximum_width 200
```
Change for what you want.

For the shadowing...
If using Metacity as the window manager, turn off compositing.
**gconf-editor** > /apps/metacity/general/compositing_manager
*** If that's Docky your using, with Metacity, you may have to live with the shadow as Docky requires compositing. ***


If using compiz add conky to the shadow windows box in the Window Decoration plugin. 
**compizconfig-settings-manger** > Effects > Window Decoration > Shadow windows
Copy and paste this into the shadow windows box.
```
(any) & !(class=Conky)
```
The "!" means **not**(class=Conky)

---

### Post by melkespreng on 2010-11-21
read to fast.

stinkeye already solved it.

---

