---
title: "Firefox 3/4 web pages font is too small"
date: 2011-04-03
forum: General Help
---

### Post by enim64 on 2011-04-03
Hello everyone

   I have a problem with firefox since the first time I installed ubuntu:
 The default font  for web pages is toooooooooooooooo small !
 I did several searches on google and forums but no hope ....

 the solutions I tried:

[LIST]
[*]Chager dpi value in about: config
[/LIST]
  -> no effect


[LIST]
[*]Change the value of the dpi of the system
[/LIST]
  -> all fonts on my system changed exept firefox web pages fonts


 The 1 / 2 solutions:

[LIST]
[*]  change the screen resolution
[/LIST]

[LIST]
[*]Change the minimum size of the fonts in firefox péferances
[/LIST]

[LIST]
[*]  install an addon for firefox to enlarge the font
[/LIST]
  The last 2 options may cause the change of the layout of web pages (very bad)

 my screen resolution : 1680 x 1050

---

### Post by VastOne on 2011-04-04
I use a fantastic plugin called NoSquint..

It has site and global settings and a easy click to enhance option...

I would use Chromium but b/c it does not have a suitable plugin or one even close to NoSquint, I will not use it..

Give it a try, it may be just what you are after.

---

### Post by Vaarp on 2011-04-12
Gonna share my solution,

First I downloaded via System > Administration > Synaptic Package Manager the **ttf-mscorefonts-installer** and installed it (this will install MS Windows fonts such as Arial, Georgia, etc.. I did this because I wanted to read the website texts on their original fonts, not on some unix predefined fonts)

Then I downloaded **Chromium Browser** ("aka" Windows Google Chrome) via Applications > Ubuntu Software Center, installed it,  and went to Preferences > Customize Fonts and there you can set the **Minimum Font Size to (the ones I recommend) 11pt, 12pt or 13pt** with the slider, which is proportionally the most alike font size you can see when navigating with any internet browser under Windows. It's almost the same size and you it's really comfy for reading the websites texts.

---

### Post by walt.smith1960 on 2011-04-12
> **enim64 said:**
> Hello everyone

   I have a problem with firefox since the first time I installed ubuntu:
 The default font  for web pages is toooooooooooooooo small !
 I did several searches on google and forums but no hope ....

 the solutions I tried:

[LIST]
[*]Chager dpi value in about: config
[/LIST]
  -> no effect


[LIST]
[*]Change the value of the dpi of the system
[/LIST]
  -> all fonts on my system changed exept firefox web pages fonts


 The 1 / 2 solutions:

[LIST]
[*]  change the screen resolution
[/LIST]

[LIST]
[*]Change the minimum size of the fonts in firefox péferances
[/LIST]

[LIST]
[*]  install an addon for firefox to enlarge the font
[/LIST]
  The last 2 options may cause the change of the layout of web pages (very bad)

 my screen resolution : 1680 x 1050

**WAY** simpler solution.  Hold a "ctrl" key down and tap the "+" sign. That will increase the type size and leave everything else alone. Works the same as Windows.  Not every problem requires editing a config file ;)

---

### Post by SeijiSensei on 2011-04-12
> **walt.smith1960 said:**
> **WAY** simpler solution.  Hold a "ctrl" key down and tap the "+" sign. That will increase the type size and leave everything else alone. Works the same as Windows.  Not every problem requires editing a config file ;)

Holding down Ctrl and scrolling with the mouse wheel accomplishes the same thing as repeatedly using Ctrl-Plus/Minus.  I find that the quickest way to zoom a page to the size I need.

That said, I always bump up the default font size in Edit > Preferences > Content > Fonts as well.

Pages that don't zoom properly are poorly designed.  Usually they're the work of someone trained in print layouts who thinks of web pages as newletters or brochures.  Proper HTML should zoom seamlessly.

---

### Post by KarlHegbloom on 2011-05-08
I believe that the number in the Firefox font settings dialog is the pixel size, not the point size of the font. So here's how I've set it up to make it look a lot better for me:

I have a screen that is 1400x1050 pixels, and 245x185 mm in size. I divided 1400 / 245, and 1050 / 185, and found that the closest average dpi is 144 dots per inch. So, in the xorg.conf, I have:

  DisplaySize 247 185

... in the Monitor section. I found that was not enough; for some reason the intel driver is not using that setting, so I had to switch to KDM, and add the -dpi 144 option to the X server commands... So now when I check 'xdpyinfo', it shows the correct dpi for this monitor.

After all of that, I get the right font sizes in Gnome and KDE. But Firefox doesn't do what I expect, and so to get the right font sizes, I calculated:

   1 point = 1/72 in
 10 point = 0.1389 in
 0.1388 in * 144 pixel / in = 20 pixel

... so, for a 10 point font, I need to set Firefox to 20. I have both proportional and monospace set to 20, and minimum font size set to 18, which is a 9 point font. Works for me, more or less.

Oh, and I have both layout.css.dpi and layout.css.devPixelsPerPx set to default values.

---

