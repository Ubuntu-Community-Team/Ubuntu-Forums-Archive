---
title: "Keyboard layout keep changing..."
date: 2010-05-09
forum: General Help
---

### Post by gwu777 on 2010-05-09
Very annoying problem, my keyboard layout keep changing from windows to windows. When I am using my French keyboard, I set the keyboard to English and it doesn't make the change for all the open windows, despite having selected the "separate layout for each windows" unselected.

Plus if I am in firefox with a French layout go to another windows and come back to the firefox windows, the layout is back to GBR.

it is very annoying!!!

Any ideas. I am on lucid, but the problem was there on karmic.

Cheers

---

### Post by P4man on 2010-05-09
How are you switching between layouts? I just tried it, switching using the the tray icon and it seems to work fine for both open and new windows.

---

### Post by gwu777 on 2010-05-09
> **P4man said:**
> How are you switching between layouts? I just tried it, switching using the the tray icon and it seems to work fine for both open and new windows.

Mainly via the tray icon too, and it used to work fine a few weeks ago, however it has started behaving oddly as described above in the last few days..

---

### Post by odony on 2010-07-11
Got the exact same issue here on lucid, it's driving me nuts, and I can confirm that it didn't happen with jaunty.

Looks like it keeps a sense of per-application layout and sort off reverts to it when you open a new window, even though "per-window layout" is turned off in preferences.

It's quite annoying when you have an external keyboard on a laptop with a different keymap and you want to be able to quickly switch layout when you [un]plug it.

Only workaround so far is to force a single keymap using setxkbmap, which of course defeats the purpose of having multiple layouts.

I'm now forced to hit LShift+RShift (my shortcut for switching layouts) all the time..

---

### Post by gwu777 on 2010-09-16
It is now working... Go figure...

Odony do you have any luck. I had notice, that at one point, having the "Separate layout for each windows" selected had better result than not, very weird at the time...

---

