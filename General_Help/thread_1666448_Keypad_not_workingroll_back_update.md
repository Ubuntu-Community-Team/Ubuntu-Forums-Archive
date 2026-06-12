---
title: "Keypad not working/roll back update?"
date: 2011-01-13
forum: General Help
---

### Post by vacco on 2011-01-13
Yesterday I discovered that my keypad suddenly does not work anymore. Its LED indicator reacts as normal when NumLock is pressed, but no matter if NumLock is on or off, there is no reaction on any of the numkeys. The normal number keys (over the keyboard) are working as usual.

When I was writing this post I actually discovered that pressing 5 on the numpad enters the text that I most recently erased (or something like that). This is true both with NumLock turned on and off. Still no reaction from the other numkeys though.

My system has also been quite unstable after I discovered the numpad problem. I just had a weird chrash that forced me to reboot (managed to avoid hard reboot though). I had the same type of chrash yesterday, and I had a less serious chrash earlier tonight that the system managed to survive without a reboot.

I have a theory (well, actually more of a hypothesis) that the system update yesterday may have caused this. Is there any way to roll these updates back?


System info:
I have not enabled backports or proposed updates, but I have added the Medibuntu and Ubuntu tweak repositories.

My hardware is a Packard Bell EasyNote TJ71 laptop with AMD Athlon II X2 M300 processor.

---

### Post by vacco on 2011-01-14
I found the solution for the numpad problem here: [http://ubuntuforums.org/showthread.php?p=4444700](http://ubuntuforums.org/showthread.php?p=4444700).
The numpad had in some way been set to control the mouse pointer.

In Ubuntu Maverick: System-->Preferences-->Keyboard. Uncheck the checkbox in the fourth tab.

Although I have not figured out why my system is so unstable, I will mark this thread as solved. By now it seems like chances are slim I will get any replies on this.

---

### Post by jackdale on 2011-02-05
Thank you very much!  This just started happening for me in maverick since the penultimate update.  (I have changed nothing else).  The keypad would work well until after login, when it stopped working.  Deceptively simple solution and I feel like a total noob not checking that tab in the keyboard settings!:lolflag:

---

