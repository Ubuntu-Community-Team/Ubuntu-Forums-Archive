---
title: "left edge of the screen is beyond the monitor and resolution issues"
date: 2009-11-03
forum: General Help
---

### Post by Mustafa Ismail Mustafa on 2009-11-03
I'm a complete linux noob but in the last 10 days its proven to be an interesting experience.

I'm setting up my laptop as a web development workstation as a replacement to the one I had which was windows based.  Now, there is something I noticed 2 days ago and that's the left edge of the desktop extends beyond the monitor.  Its not stopping me from working, but its becoming extremely annoying. How can I fix this?

Also, on Windows, my laptop could offer 1680x1050 but now it maxes out at 1024x768 which weird.  Googling has yielded answers about changing the Xorg.conf file and after changing that it still didn't work.

TIA

---

### Post by P4man on 2009-11-03
which videocard do you have ?
If you're unsure run
```
lspci
```
in a terminal

---

### Post by Mustafa Ismail Mustafa on 2009-11-03
Intel 915GM and sure enough :

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

---

### Post by P4man on 2009-11-03
Then I got to ask which version of ubuntu are you using, and are you using an external monitor or the built in one?

---

### Post by Mustafa Ismail Mustafa on 2009-11-03
Sorry, I should have stated that in the first post.

I'm running Jaunty.

Also, this was happening on the secondary screen.  You made me realize I had to double check if this was also happening on the laptiop's original screen. Its not. There's something else happening. I get 1024x768 @75MHz but the viewable area is to small for the screen size and I end up with a good inch from either side being black and unused.  It needs to be stretched out.

I should also mention that the screens are not mirrored and this stretch issue is not apparent on my viewsonic monitor (2nd).

Another thing I just realized, is that when I click detect screens, it does detect them but the dialog box in the upper left corner sticks and doesn't go away until I restart.

---

### Post by P4man on 2009-11-03
Is the external monitor an LCD and CRT ? Which type and brand, and how is it connected (VGA or DVI) ?
perhaps also post the contents of your

/etc/X11/xorg.conf

---

