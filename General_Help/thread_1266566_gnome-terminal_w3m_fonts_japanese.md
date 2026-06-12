---
title: "gnome-terminal w3m fonts japanese"
date: 2009-09-14
forum: General Help
---

### Post by Esthellin on 2009-09-14
I have installed Japanese onto Jaunty from the gnome-language-selector and switched to it. Somehow this has broken w3m in gnome-terminal.
When trying to view for instance a wikipedia page, the placement of the links are off, the letters in each line of text are all over the place, making it completely unreadable. 
I tried changing the monospace font used, but the effect was still there.
As a test, I changed the font to a non-monospace font, and still the page was not displayed correctly.

This occured with any w3m page visited.

As a separate test, I checked the page with xterm instead of gnome-terminal, and the page was displayed correctly. What is with this?
It seems the font of xterm doesn't change no matter what language I have (as opposed to gnome-terminal where the font's appearance changes slightly when switching languages but keeping the same font).

Is there anyway of fixing the font in w3m to work, or wether it is an incompatibility with gnome-terminal?

Or instead I could get the font that xterm uses and use that as the monospace font (changed with gnome-appearance-properties). 
Any ideas where this information would be shown (e.g. where is the exterm font options)?

EDIT:I found where the xterm's fotn definitions are, but can't find the fonts themselves. The file listing all the fixed fonts is /etc/X11/fonts/misc/xfonts-base.alias showing the font "fixed" is "-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1".
I have tried enabling bitmapped fonts to get this font into the gnome-appearance-properties listing, but it brings heaps of other uneeded fonts. Plus, the font named "Fixed" looks nothing like the font used in xterm.

Where would the font be within the system, so that I can install that font into my ~/.font folder, and maybe have it work?

---

### Post by Esthellin on 2009-09-16
Inputting Japanese characters into search engines is also broken. With both yahoo and google, trying to search any kana or kanji when using w3m will wipe out the japanese characters before doing the search.
SCIM (Anthy) is being used to input these characters, and works with all other programs. It is inputting the characters into w3m correctly, just won't add them to a search.

---

### Post by Esthellin on 2010-03-08
I have had a look in the options of w3m under Charset Settings. There is a whole stack of options there but I am not sure as to which one is wanted to add on the function of searching in Google and Yahoo with japanese characters. I have almost enabled everything to try and get it working but nothing so far has worked.

Any ideas people?

---

