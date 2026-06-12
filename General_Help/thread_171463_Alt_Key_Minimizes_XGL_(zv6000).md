---
title: "Alt Key Minimizes XGL (zv6000)"
date: 2006-05-06
forum: General Help
---

### Post by castorjay on 2006-05-06
After upgrading XGL to 0.0.10-0ubuntu3 and up (currently at 0.0.10-0ubuntu8) i had a problem with my alt and shift keys.  

alt would minimize any window i had open, which became annoying becaue before i would alt+tab, all my windows would minimize.  when i would open them back up, the windows would now be maxamized which was also annoying.

the shift key would not work when typing, but would work for a command.  for example i could use shift+ another key to activate a shortcut, but when typing if i wanted to type a symbol (such as ! @ # ? < >) basically anything that required shift.

i went through every plugin under xgl and could not find a shortcut assigned to alt or shift, i even checked ubuntu's keyboard shortcuts.

anyway, if you are having the same problem here is the fix.  under gconf>apps>compiz>general>allscreens>options go down the the middle of the page and look for "minimize_window" and change it to another key, i disabled mine, this will fix the alt key.  for the shift key, scroll down a little more and look for "slow_animations" and change it, i disabled this one as well.

p.s. i have a zv6000 laptop and have problems with assigning shortcuts to the keys F9 - F12 so this problem might only apply to very few people.  just thought i'd share.

---

