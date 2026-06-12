---
title: "Help! Print Color Is Too Pale - How To Setup?"
date: 2010-01-23
forum: General Help
---

### Post by tokyo-joe on 2010-01-23
I am using Canon Pixus MP800, an equivalent model to Canon PIXMA iP4200, on Ubuntu Karmic 9.10.

Print color on the printer is too pale on all applications (such as web page printing on Firefox, and picture printing on the image viewer). I run Windows XP on the same computer with dual-boot, and the print color is perfect on Windows XP. So, this is not a printer hardware issue, but a Ubuntu system issue.

How can I setup the printer to let it work properly?

OS: Ubuntu Karmic Koala 9.10
Printer: Canon Pixus MP800
Printer Driver: Canon PIXMA iP4200
Some Printer Driver Settings:
  -Color Model: CMYK
  -Color Precision: Normal
  -Ink Type: CMYK Color (this is the only choice with the driver) 

Thanks in advance.

---

### Post by theozzlives on 2010-01-23
Sounds like your print properties is set to economy or draft, change it to normal or maybe best.

---

### Post by tokyo-joe on 2010-01-23
> **theozzlives said:**
> Sounds like your print properties is set to economy or draft, change it to normal or maybe best.

How can I change it to normal or bast? Which parameters are you referring to?

---

### Post by theozzlives on 2010-01-23
> **tokyo-joe said:**
> How can I change it to normal or bast? Which parameters are you referring to?

Go to System>Administration>Printing, right-click your printer and select properties. It should be on the Quality tab, or something to that effect.

---

### Post by tokyo-joe on 2010-01-23
Thanks, the problem has just been solved!

I right-clicked on the printer icon on the systems menu, and found that the printer(and the printer settings too maybe) was not set "effective". I checked it and the print color turned normal.

---

