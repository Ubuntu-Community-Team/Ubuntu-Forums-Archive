---
title: "Is there an equivalent to Ctrl-Alt-Del in KDE?"
date: 2006-05-03
forum: General Help
---

### Post by RobTN on 2006-05-03
Yesterday I was uploading a picture to Blogger and while uploading Konquerer totally locked up.  In fact, the whole KDE desktop locked up.  The mouse was able to move around the screen, oddly enough.  I tried to close Konquerer but nothing would happen.  I also tried to right-click anything...click on any KDE menu button...and I even tried Ctrl-Alt-Del, Alt-Break, and various other key combos...but nothing would let me kill Konquerer.  I couldn't do anything at all except for running my mouse all over my screen...so my system was useless.

Is there anything I can do in the future if this happens again?  What would cause KDE to completely lock up like that?  I was able to move my mouse around...so at least one or more programs were running to allow that to happen.  Even the clock froze.  I tried everything I could think of...to no avail.

---

### Post by nanotube on 2006-05-03
well, you could try switching to another virtual console with shortcut ctrl-alt-f2
logging in there, and killing the process from commandline.

or, to restart the entire X system+kde, hit ctrl-alt-backspace

---

### Post by RobTN on 2006-05-03
Perfect.  That's the kind of key combos I was looking for.  Thanks a lot...I'll write them down.  Hopefully I won't have to use them...but you never know.

---

### Post by nickle on 2006-05-03
Normally Ctrl-alt-del should work. However, I have also had such KDE freeze ups in the past, albeit with older versions of SuSE. The only solution was the nasty system reset button... scarey...

---

### Post by RobTN on 2006-05-03
Yeah, that's what I had to do, Nickle.  I had to reset....and I haven't booted back into Kubuntu since then.  I hope it still works.

---

### Post by aysiu on 2006-05-03
What about *xkill*--Control-Alt-Escape?

---

