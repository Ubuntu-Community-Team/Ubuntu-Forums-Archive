---
title: "Keyboard Shortcuts 10.04"
date: 2010-04-30
forum: General Help
---

### Post by Turwaithien on 2010-04-30
Okay so I upgraded to 10.04, and now none of my keyboard shortcuts that involved the super/cmd/win/meta/whatever you want to call it key work. The ones involving the other usual keyboard shortcut keys (ctrl/alt/shift basically) still work. I suppose I could try and change all the shortcuts to involve the still working keys, but that is a lot of shortcuts and they'd end up being long and complicated and not very short.

---

### Post by Turwaithien on 2010-04-30
Bump. :)

---

### Post by Turwaithien on 2010-05-01
Okay so so far I've been able to get my old ones working again, but I accidentally changed one of my shortucts before (mod4 + t to open the terminal) and now I can't change it back.

I got the ones already set to work again by opening the terminal, running xev and finding the output of hitting the super key. On the third line it had the keycode (133 for me) and something about Multi in parenthesis. Then I ran:  xmodmap -e 'keycode 133 = Super_L'

xev then said that hitting the super key was indeed the super key. All of my old shortcuts now work, but I still can't set new ones with the super key. It won't let me attach any letters in the keyboard shortcuts thing.

I apologize if my instructions (if anyone attempts to use them if they've also got this problem) are inadequate. I've pretty much only ever asked for help on these forums. I'm not much good at explaining things.

---

### Post by Turwaithien on 2010-05-01
Also, and I realize I seem to only be talking to myself, but that's okay, I do that all the time, every time I log out and back in (or restart) it all goes away and I have to redo the above process. It's rather unfortunate. Actually it's just rather irritating.

---

### Post by vickoxy on 2010-05-13
I have the same problem: opened new thread here:
[http://ubuntuforums.org/showthread.php?t=1482404](http://ubuntuforums.org/showthread.php?t=1482404)

Hoping to find solution

---

### Post by vickoxy on 2010-05-13
See this: [http://ubuntuforums.org/showpost.php?p=7174543&postcount=10](http://ubuntuforums.org/showpost.php?p=7174543&postcount=10)

After reboot i have one shortcut wit win/super key saved. 

Do not know how to set "alt" behaviour, but i think that the solution is in keyboard layout properties.

---

