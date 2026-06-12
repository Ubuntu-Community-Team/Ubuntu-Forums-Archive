---
title: "Need some way to right-click with keyboard (11.04)"
date: 2011-05-15
forum: General Help
---

### Post by darlyn on 2011-05-15
So I'm on a CR-48 (the Google Chrome notebook) and one of the things that are not possible is right-clicking and two-finger scrolling. I don't care much for the latter, but right-clicking is an obvious necessity. I need a way to emulate the right-click action with key press.

---

### Post by Larkspur on 2011-05-15
Is there a button which looks like a menu at the bottom of the keyboard, next to the spacebar?  That brings up a context menu in most programs.

---

### Post by darlyn on 2011-05-15
Nope. I just need a way to bind right-click to any key.

---

### Post by Larkspur on 2011-05-15
I see.  Well, the last poster on [this]("http://ubuntuforums.org/showthread.php?t=500116") thread did something similar, but with a "modified" version of btnx (I don't know what he means by "modified", but btnx is in the repositories) so you could give that a go.  There are also option in Mouse preferences to emulate a right click. but I haven't got it to work.  I presume you've ran xev to see if a right button has been mapped to the trackpad itself?

---

### Post by stinkeye on 2011-05-15
I don't know if this is possible on the Google Chrome notebook.
Works in Ubuntu.

```
sudo apt-get install xdotool
```

Bind a key to 
```
xdotool click 3
```

---

### Post by darlyn on 2011-05-16
xdotool almost did the trick. It doesn't work in certain places like the desktop, window titles, and where I most need it, Google Chrome.

---

### Post by darlyn on 2011-05-16
Okay, so it did it using another method.

Installed mouseemu in the Ubuntu Software Center, and ran
```
sudo mouseemu -right 0 63
``` to make F4 my right-click key. Hurray!

---

