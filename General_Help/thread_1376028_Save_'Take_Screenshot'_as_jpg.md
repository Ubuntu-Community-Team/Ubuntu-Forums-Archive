---
title: "Save 'Take Screenshot' as jpg?"
date: 2010-01-08
forum: General Help
---

### Post by Moozillaaa on 2010-01-08
What's the best way to do this?

Thanks...

---

### Post by mk1w86 on 2010-01-08
You could convert the png image to jpg using Gimp or use another screenshot program such as Scrot which will save jpg images. :)

---

### Post by blur xc on 2010-01-08
Out of curiosity, what do you have against png?

BM

---

### Post by Slim Odds on 2010-01-08
> **blur xc said:**
> Out of curiosity, what do you have against png?

The p and the n    :D

But seriously, PNG is great format and it's not that hard to convert. You could also use "convert" program that is part of ImageMagick

---

### Post by malspa on 2010-01-08
Or maybe you can use a different screenshot application.  KSnapshot lets you save images as .png or .jpg.  When you take the snapshot and click on "Save As" there's a drop-down window next to the "Filter" field where you can choose which format you want to use.

---

### Post by Moozillaaa on 2010-01-08
> **blur xc said:**
> Out of curiosity, what do you have against png?

BM

[PNG causes global warming?](http://www.numberwatch.co.uk/warmlist.htm)



Just more familiar with .jpg, I suppose... 






Just kiddin' about gw ;) .

---

### Post by LoneWolfJack on 2010-01-08
as an idea, you could also just open a console window and type

```
convert screenshot.png screenshot.jpg
```

---

### Post by andrew.46 on 2010-01-09
Hi Moozillaaa,

> **Moozillaaa said:**
> What's the best way to do this?

I am not sure if it is the best way but the Gimp has a nice option to take screenshots. I attach a screenshot to demonstrate this :).

Andrew

---

### Post by malspa on 2010-01-13
> **LoneWolfJack said:**
> as an idea, you could also just open a console window and type

```
convert screenshot.png screenshot.jpg
```

This works but for me, I had to install **imagemagick** first, because when I first ran the command (in Mint 5) I got the following:

```
$  convert top1.png top1.jpg
The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: convert: command not found
```

I installed imagemagick and ran the command again.  Nice!  It keeps the .png image but creates a .jpg from it.

---

### Post by Slim Odds on 2010-01-13
> **malspa said:**
> This works but for me, I had to install **imagemagick** first, because when I first ran the command (in Mint 5) I got the following:

```
$  convert top1.png top1.jpg
The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: convert: command not found
```I installed imagemagick and ran the command again.  Nice!  It keeps the .png image but creates a .jpg from it.

Gee, I think that I said this 4 days ago.

---

### Post by malspa on 2010-01-13
> **Slim Odds said:**
> Gee, I think that I said this 4 days ago.

indeed

---

### Post by VCoolio on 2010-01-13
Or use the built-in screenshot command for imagemagick:

import /path/to/filename.extension

use whatever filename and supported image extension you want; the mouse becomes a crosshair and you can drag over the area you want in the screenshot.

---

