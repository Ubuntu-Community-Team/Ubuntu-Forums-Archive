---
title: "Keyboard shortcuts not working on update to 12.04"
date: 2012-05-18
forum: General Help
---

### Post by fizikz on 2012-05-18
Several keyboard shortcuts are no longer working after an upgrade to 12.04. Media keys for controlling play/pause, previous/next track no longer work. I set the shortcuts in System Settings -> Keyboard -> Shortcuts, but when I use the shortcuts I get a big black square with a "no" symbol, and no action. 

[IMG]http://img705.imageshack.us/img705/5845/screenshotwvy.png[/IMG]

Other keyboard shortcuts just won't work unless I open the Keyboard preferences dialog first, as above. 

Finally, one really weird problem is that to launch gnome-terminal, I would like to use Alt+T, but no matter what I do, the only shortcut that works is Ctl+Alt+T. 

None of these problems were there before 12.04!

---

### Post by fizikz on 2012-05-20
Ok, I've figured out that the problem is not with Ubuntu, but with Clementine player. Clemetine seems to be unable to make use of the media hotkeys, whether I set them in Gnome's preferences or disable them there and set them directly within Clementine. However, the hotkeys do work with rhythmbox.

Now the question is, why is Clementine able to set the media keys as shortcuts, but unable to have them perform the action specified when pressed?

---

### Post by ricolai on 2012-05-24
Same problem here since the upgrade to 12.04 with Clementine:
[LIST]
[*]'mute' works, 'unmute' doesn't
[*]other keys (previous, next, play/pause, stop) don't
[/LIST]

...

---

### Post by fizikz on 2012-05-24
So far, I think this is a Clementine problem, at least on the surface. The media keys work for system function, but not in Clementine. In fact, it's not just the media hotkeys, but other keyboard combinations, that are not working in Clementine's keyboard shortcuts. Right now, I found some shortcuts that work, such as Ctrl+Shift+E for play/pause, etc. I found that Alt+P or most Alt combinations didn't work in Clementine. The confusing part is that Clementine will register the keypresses and record them as the shortcut combination, but when they are pressed again later, the action (play, etc) will not be performed. I still haven't found a solution, but my workaround for now is to find shortcut combinations that work, just through trial and error.

---

### Post by 001neeraj on 2012-10-31
hi,
    i use 12.04 and got the same problem. The problem was solved when i select 'use gnome shortcut keys' from clementine's keyboard configuration settings(tools->preference).  Then i assigned these media keys in Ubuntu's keyboard settings for play,pause,next track, etc.  Hope this helps...:)

---

