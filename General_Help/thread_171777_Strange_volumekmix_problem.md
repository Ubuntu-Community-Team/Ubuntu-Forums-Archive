---
title: "Strange volume/kmix problem"
date: 2006-05-07
forum: General Help
---

### Post by Zaventh on 2006-05-07
Hello,

I recently installed kubuntu on my Dell Inspiron 600m. This is my second 600m which I have loaded with kubuntu. The first one worked flawlessly. This one, however, seems to have a few quirks...

One of the most annoying things prohibits me from using KDE at all. On load of KDE, kmix instantly opens and I get a volume level bar with a large grey background which stays on top of any other window. If I move kmix so I can see it, I see that my volume level is all the way down. If I close kmix, it just reopens. If I move the maser volume up, it quickly goes back down to no volume. It acts like a volume down key is constantly being depressed.

I find this odd because my keyboard does have volume up/down hotkeys and also a mute key. I inspected these very closely and they appear to be fine and not depressed. However, I didn't think these keys would work anyway unless I did some custom key mapping. If I press the volume up or mute hotkey, nothing happens. The only other volume key is a function key where you have to hold down Function and depress Page Up/Down. These keys look fine too, and if I press Function Page Up, it doesn't change the volume.

With the big volume status window blocking the screen I cannot use KDE at all. I use fluxbox from time to time and installed it and everything works fine in fluxbox. I even opened kmix and volume controls work fine and I don't have this problem. How can I investigate further into this and/or disable whatever volume hotkey thinks is being depressed?

Thanks.

---

### Post by Blutack on 2006-05-07
In Kmix there is a menu for global shortcuts, just disable or change the ones affected.  Have you tried updating to latest kmix?  Or even KDE 3.5.2? You dont need kde to do that,just press cntrl-alt-F1 to get a bash prompt and use apt-get.  Have a looksie on the forum for info if you want to upgrade the whole of KDE.  Even maybe uninstalling and reinstalling Kmix would do the trick.  Good Luck...

---

### Post by Zaventh on 2006-05-07
Hi, thanks for the reply.

I had already checked for global shortcuts in kmix. There are none defined. I have KDE 3.5.2 and I even upgraded to dapper just to see if it would change anything, which it didn't. I went ahead and tried to uninstall kmix completely, which went fine, but I still have this big Volume window in the middle of my screen which I cannot get rid of...

EDIT:

I managed to trace it down to kmilo service just now. I remember enabling after reading it was a special key notifier or whatnot. Guess it works... kind of. Stopping it resolved the issue and I don't think I'll be missing anything.

---

