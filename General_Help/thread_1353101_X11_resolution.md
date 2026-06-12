---
title: "X11 resolution"
date: 2009-12-12
forum: General Help
---

### Post by gpetris on 2009-12-12
Hello,

I have installed Ubuntu 9.10 (64 bit, desktop) and I am now installing a bunch of stuff that I need to work, such as liveTex, emacs, etc. 

My problem is that X applications (gv and xdvi among them) seem to have a poor definition - making the characters hard to read - compared to other applications like firefox or the default terminal window. 

Anybody has suggestions on how to fix that?

Thank you in advance,
Giovanni

---

### Post by s3MA00RRNY on 2009-12-12
Add these lines to .Xdefaults

Xft.antialias: 1
Xft.dpi: 96
Xft.hinting: 1
Xft.hintstyle: hintfull
Xft.rgba: rgb

Note that the last line has to do with your subpixel order. It may be different for your computer.

Then add this to Startup Applications:
xrdb -m .Xdefaults

---

### Post by falconindy on 2009-12-12
> **pcdude2143 said:**
> Add these lines to .Xdefaults

Xft.antialias: 1
Xft.dpi: 96
Xft.hinting: 1
**Xft.hintstyle: hintfull**
Xft.rgba: rgb

Note that the last line has to do with your subpixel order. It may be different for your computer.

Then add this to Startup Applications:
xrdb -m .Xdefaults
On an LCD screen, you should use 'hintslight'. Also, I've never seen the antialias and hinting set numerically. If this gives you any errors, change them to 'true'.

---

### Post by s3MA00RRNY on 2009-12-12
Why hintslight? Hintfull works for me with xterm.

---

### Post by hugmenot on 2009-12-13
I don&#8217;t think this will affect PS and DVI viewers. They often display fonts unhinted.

---

### Post by gpetris on 2009-12-14
Thank you for your suggestions. Unfortunately, adding those lines to .Xdefaults and reading the defaults via xrdb did not make any difference. Is there anything else I can try? 

Thank you,
Giovanni

---

### Post by hugmenot on 2009-12-14
Can you post a screenshot?

---

### Post by gpetris on 2009-12-17
Here is a screenshot, showing a gv window, much less readable than the firefox window. 

Do I need to install other fonts?...

Thank you in advance,
Giovanni

---

### Post by hugmenot on 2009-12-17
> **gpetris said:**
> Here is a screenshot, showing a gv window, much less readable than the firefox window. 

Do I need to install other fonts?...

Thank you in advance,
Giovanni

Sorry, but it&#8217;s pointless to scale down a screenshot when you want to demonstrate how your font rendering looks. The font rendering quality is determined by how the glyphs are mapped to the pixel grid. 

Anyhow, here is what I think: You will not find a DVI or PostScript viewer that displays fonts nice and crisp. I&#8217;m positive that they all have simple gray antialias and no hinting, which gives you bad contrast.

What I do is that I compile directly to PDF with pdfTeX or XeTeX and then view the resulting PDF in Evince. The DVI-PS-PDF route is pretty much deprecated nowadays anyway.

Then to get good font rendering in Evince you may install patched packages from [my PPA]("https://launchpad.net/~improved-lcd-filtering/+archive/ppa") that give you LCD filtered, sharper fonts for PDFs in Evince. 


You can see the result in the third screenshot below. You can improve on-screen readability further by not using computer modern font. It has very thin outlines that are hard to render well on screen. At least use Latin Modern &#8211; \usepackage{lmodern} &#8211; it will render better because it is a Type1 font, not Type3 like cm.

---

### Post by hugmenot on 2009-12-17
Here&#8217;s how it looks with MinionPro package. Readability is much better.

---

### Post by gpetris on 2009-12-17
Thank you so much: I will follow your suggestions.

---

