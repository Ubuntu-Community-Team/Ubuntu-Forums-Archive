---
title: "xsetwacom mapping to button number problem"
date: 2010-09-05
forum: General Help
---

### Post by oedipuss on 2010-09-05
I'm using xserver-xorg-input-wacom 10.6 from a ppa, on Lucid, with a wacom intuos 3, to fix the problem where any pad button teleports the cursor to the top left corner. 

I can use xsetwacom to map a pad button to any other pad button, or to a key , with xsetwacom set "device name" ButtonX number or "key X", or "core key X". 
Both commands work by themselves, but if I map a button to a key, I can't remap it back to a button number ... It just keeps sending the key event. 
I've tried any combination of Button 1, 1, "1", "Button 1".. 
Mapping the button to a different key works just fine. 


"xsetwacom get etc" doesn't seem to work correctly, it shows the latest mapping if it's a button number, but not if it's a key ... 


Also, DebugLevels and CommonDBG won't work. Setting or getting them just prints "Property for 'DebugLevel' not available."

Any ideas on what's going wrong, or where to look for more debug info on what's happening ? Or even newer versions of the wacom drivers I could try that can work with lucid ? (source from linuxwacom needs a newer xorg)

---

### Post by Favux on 2010-09-05
Hi oedipuss,

I'd think you'd want to update your wacom drivers to get the latest xsetwacom fixes and additions.  See **I. & II.** in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

And "core" is deprecated.

---

### Post by oedipuss on 2010-09-05
Thank you! Still somewhat weird behavior, when getting button values with xsetwacom , but setting works now =)

PS:I think the module was already the latest. The one made from source and the one already there were of identical size.

---

### Post by Favux on 2010-09-05
Good, it's working!  :)

There's an Intuos3 sample xsetwacom script attached to the second post on the Bamboo P&T HOW TO thread which may or may not interest you.  It still needs work on the Wacom tablet mouse/cursor section.

---

