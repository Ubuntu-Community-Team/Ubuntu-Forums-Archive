---
title: "Having numpad keys treated as arrow keys."
date: 2009-08-18
forum: General Help
---

### Post by tomeedee on 2009-08-18
The arrow keys on my laptop are broken and I was wondering if there was a way for Ubuntu to treat numpad keypresses as if I pressed the arrow keys.  E.g Having my computer respond to me pressing down Numpad 3 as if I had pressed down the right arrow key.

Thanks in advance for any help.

---

### Post by cmnorton on 2009-08-18
In gui mode, or x-term? You can remap keys, but not in all instances. This sounds like you need a repair. Laptops are tricky even when they work properly.

---

### Post by tomeedee on 2009-08-18
Thank you for your response I posted because I couldn't find any results in google because I had forgotten the term remapping.  A quick search returned an archive that said to use xmodmap and I have gotten what I wanted to work.

For future reference in case someone stumbles upon this in a search I used

xmodmap -e 'keysym KP_Begin = Up'
xmodmap -e 'keysym KP_Down = Down'
xmodmap -e 'keysym KP_End = Left'
xmodmap -e 'keycode 89 = Right'

---

