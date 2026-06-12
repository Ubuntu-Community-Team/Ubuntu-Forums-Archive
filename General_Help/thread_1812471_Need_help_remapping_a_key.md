---
title: "Need help remapping a key"
date: 2011-07-26
forum: General Help
---

### Post by sarahlizz3 on 2011-07-26
I bought a new keyboard and it has an annoyingly placed macro key next to the left shift key.  I would like to remap the macro key to also work like a shift key.  I have been going through forums and how to and none of them are working.  
The keycode for the key is 94.  
The keyboard is a [Caselogic wireless]("http://www.microcenter.com/single_product_results.phtml?product_id=0360450") (so when I tried to use KeyLogic I couldn't find the keyboard in the list).

Any help or ideas would be much appreciated!!!

---

### Post by tredegar on 2011-07-26
**xmodmap** is what you want to use.

I hate Caps Lock, so I turn it into another Shift key with this script, which runs when I login:```
#!/bin/bash
# Make Caps Lock be Shift
xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "add Shift = Caps_Lock"
```
You'll have to play with **xmodmap** when in a terminal to see exactly what command(s) you need to give it to re-map your annoying key. 
```
xmodmap -pk
```
Will show you how things are *currently* set up, and of course, take a look at **man xmodmap**
If you make a mistake, and mess up your keyboard, logging out and back in again will reset it back to normal.

---

### Post by enimeizoo on 2011-07-26
Well, everything is said, but I just want to mention the -pke option. It gives you about the same info, but in a way that can be fed back to xmodmap. 
I find it very handy.

---

### Post by sarahlizz3 on 2011-07-26
Thanks, it's working now!
I actually figured out that I had remapped the wrong key with xmodmap - it had "worked" but I now had no question mark key... Oops.  

But it worked with xmodmap, so thanks!

---

