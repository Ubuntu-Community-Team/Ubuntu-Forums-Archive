---
title: "Why everything seems so big?"
date: 2010-07-16
forum: General Help
---

### Post by Marco.75 on 2010-07-16
Hi, this is my first experience with ubuntu (and linux in general). I'm really satisfied but there's something that disappoints me about the desktop appearance.
My current screen resolution is 1024x768, but I don't know why everything seems so "oversized".
Icons, simbols, characters, the pointer itself, seems just way too big... how can I solve this?
p.s. I know there are single ways to set character-icon-pointer dimensions... but I'd like to know if there is some kind of general setting that can simultaneously affect each of these graphical elements...

---

### Post by mike555 on 2010-07-16
If you monitor can handle it ,set the resolution higher ..... System > Preferences > Monitor

---

### Post by Marco.75 on 2010-07-16
it's a quite old laptop (packard bell easynote e3) that I want to use as a linux only machine.
I'm quite sure 1024x768 is the max possible resolution...

---

### Post by Vaphell on 2010-07-16
you can try setting smaller fonts in appearance options or lower dpi but probably it won't be pretty

---

### Post by the8thstar on 2010-07-16
Can you post a screenshot of your desktop? (Applications -> Accessories -> Take Screenshot) We might be able to help further this way.

---

### Post by Marco.75 on 2010-07-17
ok, I'll try to do that, I'm an absolute beginner.

---

### Post by Marco.75 on 2010-07-17
Here's a set of five shots of my desktop and some windows...
btw I already verified: the resolution is 1024x768. At this resolution 
everything should be tight and small... at least it so it was on windows.


[ATTACH]163720[/ATTACH]

[ATTACH]163721[/ATTACH]

[ATTACH]163722[/ATTACH]

[ATTACH]163723[/ATTACH]

[ATTACH]163724[/ATTACH]

---

### Post by Vaphell on 2010-07-17
there is nothing inherently wrong with your setup, sorry. That's how this theme looks, simply it's not too good for old lowres displays. There is more eyecandy to it than it used to be in WinXP and that eats more pixels
You can:
- test other themes
- set up smaller fonts system wide (panels and menus will occupy less space) or try to lower DPI from 96 to 80 or whatever - this scales everything (preferences->appearance->fonts)
- in firefox zoom in/out with CTRL+mousescroll (in nautilus that works too)
- desktop icons are controlled by nautilus preferences, there are settings for default zoom for icon view and that applies to desktop, change from 100% to 66% or whatever
- also you can scale desktop icons per icon basis - right click, stretch icon

---

### Post by Marco.75 on 2010-07-17
Thankyou, setting the DPI helped a lot... now it is set @ 72 (25% less than 96) and it looks fine.
BTW if I want to finetune something else... where can I access the nautilus preferences?

---

### Post by digitalcitizenx on 2010-07-17
Alt + F2

type in

gconf-editor

go to

apps --> Nautilus --> icon-view

"default_zoom_level" make it say "smaller"

this should take care of your large icon issue

---

### Post by Vaphell on 2010-07-17
less haxxorish way would be to simply open Preferences in your file browser (coincidentally its name is nautilus ;)) there you can find dropdown boxes with zoom options, among the others.

---

### Post by Marco.75 on 2010-07-18
ok, after some tuning it fits good now!
I set up the default zoom level for the nautilus views, and reduced the dpi to 72 (which made more slim the toolbars also).
I also found a setting to reduce the dimension of the toolbar buttons!

Now I have another problem (firefox or any other browser taking ages to resolve hostnames) but that's another story :-)

---

### Post by the8thstar on 2010-07-18
Forza Italia ! I'm glad to see your problems are now resolved. About Firefox, do you used an HDCP protocol to connect to the Internet?

---

### Post by jean noel on 2010-07-20
I personally have a slightly different problem. My screen resolution is ok at 1440 * 900. The fonts and icons are fine, but recently, I have noticed that they look much better after I have opened a document in adobe reader.
Any hints on why it should be so?
Thanks
Jean Noel

---

### Post by Vaphell on 2010-07-20
'they' = fonts?
i am not sure if i understand - adobe reader somehow updated your system-wide configuration and now fonts look better or adobe reader fonts are better than system ones? either way inspect System->Preferences->Appearance->Fonts->advanced

---

