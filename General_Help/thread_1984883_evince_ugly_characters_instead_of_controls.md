---
title: "evince ugly characters instead of controls"
date: 2012-05-22
forum: General Help
---

### Post by jazzerit on 2012-05-22
Hey guys, I have a problem - when using evince, all of the text on GUI widgets comes out as those square characters, but the pdf itself is alright. I've put the output from a command line:
```

(evince:5985): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Ubuntu 11'

(evince:5985): Pango-WARNING **: font_face status is: <unknown error status>

(evince:5985): Pango-WARNING **: scaled_font status is: out of memory

(evince:5985): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Ubuntu 11', text='&#9679;'

(evince:5985): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Ubuntu 11'

(evince:5985): Pango-WARNING **: font_face status is: out of memory

(evince:5985): Pango-WARNING **: scaled_font status is: out of memory

(evince:5985): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Ubuntu 15.83984375'

(evince:5985): Pango-WARNING **: font_face status is: out of memory

(evince:5985): Pango-WARNING **: scaled_font status is: out of memory

(evince:5985): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Ubuntu 15.83984375', text='This document is locked and can only be read by entering the correct password.'
```
This would seem to be related, I just can't figure out what to do about it. Already tried reinstalling evince,and changing my fonts.

---

### Post by flemur13013 on 2012-05-22
[FONT=monospace]"the offending font is 'Ubuntu 11'"

I've had nothing but problems from that font - perhaps you need to change the fonts somewhere else (maybe w/gnome-tweak-tool?)  and/or completely remove the "ubuntu" font from the machine.
(FWIW, "xpdf" doesn't work at all as a replacement.)


[/FONT]

---

### Post by jazzerit on 2012-05-22
> **flemur13013 said:**
> [FONT=monospace]"the offending font is 'Ubuntu 11'"

I've had nothing but problems from that font - perhaps you need to change the fonts somewhere else (maybe w/gnome-tweak-tool?)  and/or completely remove the "ubuntu" font from the machine.
(FWIW, "xpdf" doesn't work at all as a replacement.)


[/FONT]

Unfortunately, changing the font with gnome-tweak-tool doesn't work either.

---

### Post by jazzerit on 2012-05-22
OK, I've sort of fixed it - it seems to be a problem with the ~/.fonts folder. When I renamed it, the fonts on widgets in evince decided to work. I would rather like to know *what* in my fonts folder is causing it.

---

### Post by jazzerit on 2012-05-22
ooooookay. Fixed it - my fonts folder was actually a symbolic link to a place on my crunchbang partition that's mounted on boot, since I've divided the (already a little inadequate) partition into two for the two OSes, I felt that it may be a good idea to just symlink, but from what I can find out from t'internets, it's a permissions error. Anyway, thanks for all your help, guys.

---

