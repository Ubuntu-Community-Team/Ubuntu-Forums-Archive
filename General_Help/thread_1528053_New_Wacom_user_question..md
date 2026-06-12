---
title: "New Wacom user question."
date: 2010-07-10
forum: General Help
---

### Post by robert shearer on 2010-07-10
Using wacom Bamboo Fun, CRT monitor, and Lucid 10.04.

Recently I tried using a template set to produce some circles.
They all came out as ovals.

Mapping ? But the tablet maps to the screen. I can run my stylus around the edge of the tablet and it runs around the edge of the screen.

So tried changing 'Mypaint" settings from 'screen' to 'window'.
That fixed the circles but now the cursor is offset @15mm from the on-screen drawing point.

Any enlightenment appreciated :)

Thanks, Bob.

---

### Post by Favux on 2010-07-10
Hi Robert,

It sounds like there might be a difference in aspect ration.  Although the monitor is probably 4:3 and the Fun is 6x8.

To correct the ellipses you use KeepShape.  It maps the tablet to the monitor, keeping proportion, starting in the left upper corner:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)  Which may mean you lose some screen space.  Since there is no xsetwacom equivalent, you add it to the 10-wacom.conf usb snippet below the 'Driver "wacom" line:
```
Option "KeepShape" "on"
```
As always remember to back up your 10-wacom.conf and be ready to restore it from the command line if the change breaks X.

---

### Post by robert shearer on 2010-07-11
Thanks again Favux,

```
Option "KeepShape" "on"
```

Worked perfectly !

(less tablet area available but, hey, that is why I ordered a Fun medium instead of a P&T, as it is larger I lose less overall. :D )

---

