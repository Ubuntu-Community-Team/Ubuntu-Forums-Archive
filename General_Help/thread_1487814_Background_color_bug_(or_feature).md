---
title: "Background color bug (or feature?)"
date: 2010-05-19
forum: General Help
---

### Post by Objekt on 2010-05-19
I like to customize my Ubuntu Netbook Remix installs by setting the background color to a solid shade, matching the netbook's case color (blue or red for my Aspire Ones).  I noticed that when I do so, many choices result in a solid black background underlaying the UNR menus, even though I thought I was picking a color.  A very bright color, in some cases.

For example, if I type in bright red (255 Red, 0 green, 0 blue), I get...a black background, even though the dialog box shows bright red.

Likewise bright green (0 R, 255 G, 0 B) and blue (0 R, 0 G, 255 B).

It also seems to happen if I manually click near the points of the color triangle on the left of the dialog.  I have to select a color closer to the middle of the triangle, or I get either black or a sufficiently dark shade as to be indistinguishable from black.

What's going on here?  Am I just really ignorant about picking colors, or is it a bug?

---

### Post by dino99 on 2010-05-19
some video screens are built and sold without good factory calibration and then have weird colors.
An other reason can be lucid kernel not sending the good harware vertical & horizontal frequencies, in this case, user have to specify them into xorg.conf

---

### Post by Objekt on 2010-05-19
I'm not using Lucid, I run Ubuntu Netbook Remix 9.10.

Haven't had any other display problems on my Acer netbooks w/UNR.  Go figure.

---

### Post by -humanaut- on 2010-05-19
I'd recommend giving Kubuntu netbook edition a try if the colors are a major problem for you I've `heard` it's far easier to customize.

---

### Post by Objekt on 2010-05-19
It's not a major problem.  Mostly, I'm not sure whether it's a bug, or I'm just not understanding the controls.

There seems to be a mismatch between the color selected in the dialog box, and the color applied to the screen.

I usually use landscapes, astronomy photos etc. as a background on my desktop machine.  I prefer solid colors on netbooks, because it seems less cluttered on the small screen.

Now I'm curious whether this problem occurs on a standard Ubuntu 9.10 install.  I'll play with it later & post results.

Edit:
Yes, this is definitely a bug particular to UNR 9.10.  On my regular Ubuntu 9.10 install, I can set any of the extreme shades of red, green, or blue mentioned above, and have the desktop turn the appropriate color.

---

