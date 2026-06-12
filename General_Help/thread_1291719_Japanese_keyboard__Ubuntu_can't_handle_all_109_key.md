---
title: "Japanese keyboard:  Ubuntu can't handle all 109 keys?"
date: 2009-10-15
forum: General Help
---

### Post by TokyoYank on 2009-10-15
I have a Japanese 109 key version of a Microsoft Comfort Curve 2000 usb keyboard[LIST]
[*]Keyboard has worked fine in Vista and Fedora 10 (with some tinkering)
[*]With 9.04 the best I can do (ie, using a 106 layout) has it so the ] key types a /  [LIST]
[*]this is consistent using the visualizer "onboard", the ] key is simply missing (makes sense, it thinks there's only 106 keys)[*]there are other problems too, such as }
[*]they aren't dead keys, they're simply mismapped
[/LIST][/LIST]I installed 9.04 using a standard US qwerty PS2 keyboard, added this USB keyboard afterwards.  Note, I want and like US-en as my locale, but I like this keyboard's meta keys (at times type in Japanese).  I currently type ] by memory using the US qwerty layout, love the GNOME applet for that

More info:[LIST]
[*]System > Preferences > Keyboard > Layouts > Keyboard Model   --  Here I can select "Microsoft Comfort Curve Keyboard 2000" .. but no mention of the 109 key Japanese version
[*]Same place, under "Generic" make, I see 106 key Japanese, but not 109 key
[/LIST]

==> Is there a way to successfully use all 109 keys in Ubuntu?  


If I have more time, things I'm considering to try are:[LIST]
[*]sudo dpkg-reconfigure console-setup
[*]ripping required files from a Fedora rpm somewhere
[*]manually adding my own layout, etc...
[/LIST]

Thanks for reading


*[SIZE="1"]edit:  FIXED[/SIZE]*

---

### Post by TokyoYank on 2009-10-16
Generic Japanese 106 works now.  Don't know what happened--perhaps my window focus options made it unclear which window had which layout.  (slash / appears for unassigned keys when US layout is chosen)

---

