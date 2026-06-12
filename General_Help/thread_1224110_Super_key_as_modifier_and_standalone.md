---
title: "Super key as modifier and standalone?"
date: 2009-07-27
forum: General Help
---

### Post by brownbat on 2009-07-27
This has been asked from time to time, but I can not seem to find an answer.

Is it possible to set up the Super key as a standalone key and a modifier at the same time?

---

### Post by CatKiller on 2009-07-27
I shouldn't imagine so. How would it know when you wanted to use it as a modifier rather than as a standalone key. Something you might be interested in, though, is that the shortcut to open the menu is Alt-F1.

---

### Post by brownbat on 2009-07-27
Thanks for your thoughts on this problem, I should have included more detail.

"How would it know when you wanted to use it as a modifier rather than as a standalone key."

I'm not sure of the specific controls there, but I know it's worked this way on Gentoo before, and works with no config on certain other OS's.

I'm hip to Alt-F1, that's a good tip. But personally, I would probably use the key for a launcher like Beagle or Do, since a one keystroke launcher, especially one where my hands can stay close to the home row, seems to pump up my personal efficiency a lot. Making WinKey/Super a launcher is one choice I would begrudge MS for getting right in Win 7.

---

### Post by CatKiller on 2009-07-27
Actually, it does work. I don't know how, but it does. At least for my test case of using it to maximise a window, and zooming in still worked.

---

### Post by brownbat on 2009-07-27
Ah, that's encouraging!

What keys to you press to maximize a window, and what to zoom in? Is it on compiz or KDE or anything different than out of the box Ubuntu? Did you configure the shortcuts through the keyboard shortcuts item in  preferences? What item did you check under Preferences>Keyboard>Layouts>Layout Options>Alt/Win Key Behavior?

Thank you for your feedback!

---

### Post by CatKiller on 2009-07-27
> **brownbat said:**
>  What keys to you press to maximize a window, and what to zoom in? 

I set the Maximise window shortcut in System &#8594; Preferences &#8594; Keyboard Shortcuts to "Super_L" (just by clicking in the box and pressing the button) as something painless to test with. I've got Super+mousewheel set to zoom in the screen in Compiz (that's probably the default). That was just my test to see if the key still worked as a modifier.

> What item did you check under Preferences>Keyboard>Layouts>Layout Options>Alt/Win Key Behavior?

It's set to "Default." I don't think I've ever changed it.

---

### Post by brownbat on 2009-07-27
Ah, when you try to assign them both in the Keyboards-Shortcuts menu, the Super+x shortcut cannot be assigned, saying that Super is already assigned. 

Maybe Compiz is designed to accept combos of keys more liberally. Maybe that's because it seems the Keyboard>Shortcuts menu interprets keys on "key down" rather than "key up".

When you zoom in on an unmaximized window, does the machine try to do both, or does Compiz intercept the first Super event?

Either way, that keyup/keydown distinction seems to be the issue. This seems like a deeper problem than I originally thought.

---

### Post by CatKiller on 2009-07-28
> **brownbat said:**
> Ah, when you try to assign them both in the Keyboards-Shortcuts menu, the Super+x shortcut cannot be assigned, saying that Super is already assigned. 

I'd imagine that the shortcuts are stored as GConf keys. You could probably use gconf-editor to manipulate the shortcuts directly to see if it works despite the warning.

>  When you zoom in on an unmaximized window, does the machine try to do both, or does Compiz intercept the first Super event?

I think it depended on how long I pressed the Super key for before I used the scrollwheel.

---

### Post by coffeecat on 2009-07-28
> **brownbat said:**
> Ah, when you try to assign them both in the Keyboards-Shortcuts menu, the Super+x shortcut cannot be assigned, saying that Super is already assigned. 

I managed to get Super alone, Super+Alt and Super+Ctrl assigned as shortcuts without the warning message, but I get the warning if I try combinations of Super + alphanumeric. I couldn't find a way round that.

---

