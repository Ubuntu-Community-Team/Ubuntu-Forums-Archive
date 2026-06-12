---
title: "Monospace fonts not rendered in Firefox and Epiphany"
date: 2011-02-07
forum: General Help
---

### Post by e.s.t on 2011-02-07
I have some strange problem with rendering monospace fonts in FF and Epiphany.
There is some attached example - most pages with some code blocks look like it, it is not possible to see the text, even after selecting it.
I tried to change settings in FF of fonts, tried to change size, colors, font, but still it is not visible at all no matter what.
However pages like that are displayed fine in "Chromium". Does anyone have an idea where do I begin solving this? 
Thank you.

---

### Post by e.s.t on 2011-02-07
This is strange, as Epiphany now runs on webkit, so this probably system related:

On thing I tried:

sudo fc-cache -f

Nothing changed though.

---

### Post by drogers141 on 2011-02-20
Hey e.s.t,
This is an *extremely* annoying problem.  One fix I found is to adjust your font preferences in firefox.  Open Edit->Preferences->Content->Fonts and Colors Advanced and deselect "Allow pages to choose their own fonts..."
This fixed the problem for me, however you may want to turn this back on again at times when you want to see special fonts rendered.  At this point, I am toggling this setting depending on what I need.
Any one else have any solutions?

---

### Post by drogers141 on 2011-04-18
Another possible solution:
Ultimately, I found that my problem was due to file permissions on font files.  I had copied some of Microsoft's fonts (Consola, etc, I believe) from my Vista installation and the read permissions were not lenient enough.  I suggest looking at your font files to check.

I believe that the fact that the font files existed, but couldn't be read by whatever program was reading them, caused the problem of the disappeared text.  In this case the Consola was suggested in the css for the afflicted page (in the pre tags, for example), but if Consola wasn't available, monospace would have been used instead.  Since it *was* available, the rendering engine called to render it, but nothing was rendered due to the permissions.  Not my realm of expertise if anyone with more knowledge wants to chime in.

---

