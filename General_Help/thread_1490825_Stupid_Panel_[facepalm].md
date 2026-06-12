---
title: "Stupid Panel [/facepalm]"
date: 2010-05-22
forum: General Help
---

### Post by Drybones5 on 2010-05-22
OK so I decided to finally rid of the bottom panel.  And I was about to click delete when I realized it could be a really cool side panel.

I set it right, autohide, and bam.  It was gone and now its there :(

I can get to it :(



[IMG]http://imgur.com/95t86.png[/IMG]

---

### Post by drs305 on 2010-05-22
If you want to put the panel back on the bottom you can put it back with this command (and try again ;-) ):

```
gconftool-2 -s -t string /apps/panel/toplevels/bottom_panel_screen0/orientation bottom
```

If you prefer working with a GUI, open "gconf-editor" and go to the section above.  The hide options are also available in this section.

---

### Post by Drybones5 on 2010-05-22
> **drs305 said:**
> If you want to put the panel back on the bottom you can put it back with this command (and try again ;-) ):

```
gconftool-2 -s -t string /apps/panel/toplevels/bottom_panel_screen0/orientation bottom
```If you prefer working with a GUI, open "gconf-editor" and go to the section above.  The hide options are also available in this section.

Actually the terminal sounds easier than the gui (from looking at the config)

---

### Post by Drybones5 on 2010-05-22
Thanks!  I got it to the bottom and I deleted the sucker :P

---

### Post by kerry_s on 2010-05-22
hey, Drybones5
how do you get the separator to be a line like that?

i'm new to cairo dock. :)

never mind, i just found the setting under "icon" in the advanced menu. thanks i didn't even realize they could be changed.

---

