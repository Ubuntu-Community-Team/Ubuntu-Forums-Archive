---
title: "ATI RADEON x1600 not recognized?"
date: 2006-05-29
forum: General Help
---

### Post by laix1234 on 2006-05-29
So I have an ati radeon x1600, and you'd think that would make graphics stuff run really well, but I have a sneaking suspicion that it's not being recognized (or something) because both screen savers and dvd movies are jumpy.  If it was just dvd movie files I would think it was an issue with codecs and such, but if any screen saver runs that is at all complicated (for a screen saver) it has a horrible frame rate and gets jumpy.  Running dvds in xine, I get a message saying my framerate is too low and something about not enough resources. 

I also have 1 gig of ram (divided between 4 256 cards sadly, but what can I say), so there should be plenty of resources unless the graphics card isnt being used....

Any way to check if it's being used/is recognized, and if it's not, how to make it so?

Oh, and I'm using vesa, which seems to work, but I did try radeon and ati and neither of them worked...

---

### Post by AirRaven on 2006-05-29
If you're using Vesa it's no wonder things are jumpy. It's just not using your video card's advanced features at all.

---

### Post by laix1234 on 2006-05-29
Is there something else I can use that will?  Like I said, ati and radeon didnt work...

---

### Post by Ramses de Norre on 2006-05-29
Install the fglrx driver:```
sudo aptitude install xorg-driver-fglrx

```
Then back up and edit your xorg.conf ```
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf.bak && sudo gedit /etc/X11/xorg.conf
``` and replace the line Driver "vesa" by Driver "fglrx" in the device section of your video card.
Save and press ctrl-alt-backspace to restart X (closes all open applications).
Or run sudo dpkg-reconfigure xserver-xorg and choose fglrx as driver.

---

### Post by laix1234 on 2006-05-29
Well, that certainly seems to work, the movies play just fine, and obviously the desktop shows up and all, so something went right, but the screen saver is still jumpy, might just be the screen saver tho...

is there a command to find out if the graphics card is fully recognized and able to be used and such?

---

### Post by laix1234 on 2006-05-29
and when i use lspci, the thing about cards reads:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c2
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 71e2

---

### Post by yatt on 2006-05-30
[QUOTE=laix1234]and when i use lspci, the thing about cards reads:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c2
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 71e2[/QUOTE]
fglrxinfo in a terminal. If it says stuff about ATI, then it is good. If it mentions Mesa, something isn't right.

---

