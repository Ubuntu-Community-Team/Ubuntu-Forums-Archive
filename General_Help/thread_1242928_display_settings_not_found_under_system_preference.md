---
title: "display settings not found under system preferences"
date: 2009-08-17
forum: General Help
---

### Post by tompoe on 2009-08-17
I'm running 8.04 hardy.  There's no Systems->Preferences->Display on my menu.  I got suckered into plugging in my computer to a iogear KVM switch, and learned the hard way that their equipment is for Windows only.  I got my display adjusted to what appears to be 800x600 or worse.  I can't find an option for resetting the display to 1074x780 or whatever it was, before.  Any help appreciated.

I ran the sudo /dpkg-reconfigure xserver-xorg commands, but that did nothing.

---

### Post by wojox on 2009-08-17
Open System > Preferences > Main Menu
On left side click preferences and look for it in the Items and check it.

---

### Post by asmoore82 on 2009-08-17
You can also hit Alt+F2 and run:
```
gnome-display-properties
```

---

### Post by tompoe on 2009-08-17
I already tried that, but it just is not listed.  Weird.

---

### Post by tompoe on 2009-08-17
Thanks, much.  Worked like a charm.  You guys are good.

---

### Post by jerrrys on 2009-08-17
or right click on main menu, choose edit, go to preferences and choose **Screen Resolution**.  this will now appear in preferences of your main menu, you should then be able to choose proper screen resolution.
this usually works with 804.

---

### Post by tompoe on 2009-08-17
The only main menu I know, is found by clicking on System then selecting preferences, then clicking on main menu.  What main menu are you referring to?

---

### Post by wojox on 2009-08-17
If you right click the ubuntu logo you can select edit menus and it brings up the Main menu as well.

---

### Post by tompoe on 2009-08-17
You've hit on the problem.  I do that, and there's no display link listed.  It just isn't there.  However, the gnome-display-properties worked well.

---

### Post by jerrrys on 2009-08-17
sorry, got ahead of myself in my last post.  i have edited and should now make sense...

---

### Post by tompoe on 2009-08-17
FOUND IT!  Amazing!  Maybe I'll stay retired, and not try a new career in IT.  :)

---

### Post by jerrrys on 2009-08-17
na, don't stay retired, its no fun...you didn't say, did it work??

---

### Post by tompoe on 2009-08-17
It worked wonderfully.  Actually, on the retirement thingy.  I had to take the VA pension for health reasons.  It didn't take too long to fill my time with learning about Linux.  Can't get past the beginner stage, though.  I managed to get asterisk far enough along to be able to say goodbye to my phone landline, and VoIP is now the name of the game. Feeling good about that.

---

### Post by jerrrys on 2009-08-17
the forum is what sold me on ubuntu, love it.  look forward to talking to ya again...

---

