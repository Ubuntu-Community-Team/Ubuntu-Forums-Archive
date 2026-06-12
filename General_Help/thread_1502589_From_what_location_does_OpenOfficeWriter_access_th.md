---
title: "From what location does OpenOfficeWriter access the fonts?"
date: 2010-06-05
forum: General Help
---

### Post by Cariboo1938 on 2010-06-05
When I double click the .ttf font file, located on my Desktop, a window opens and the font is described in detail and a install button is shown. 
Where-to exactly will the font be installed when I click the "Install Font" button?
At which location does OpenOffice access the fonts?

---

### Post by Ranko Kohime on 2010-06-05
> **Cariboo1938 said:**
> When I double click the .ttf font file, located on my Desktop, a window opens and the font is described in detail and a install button is shown. 
Where-to exactly will the font be installed when I click the "Install Font" button?
At which location does OpenOffice access the fonts?
For the first question, probably the user folder, which I believe is ~/.fonts

As to the second, OOo will draw from the system directory, current user folder, and any other places I probably don't know about.  I'm afraid I can't point you in the direction of that knowledge, as I've never checked into it myself.

---

### Post by Cariboo1938 on 2010-06-06
> **Ranko Kohime said:**
> For the first question, probably the user folder, which I believe is ~/.fonts

Thanks, you are right, it is installed to /home/<user>/.fonts
> **Ranko Kohime said:**
> 
As to the second, OOo will draw from the system directory, current user folder, and any other places I probably don't know about. I'm afraid I can't point you in the direction of that knowledge, as I've never checked into it myself.

I expected to have the new font available in OOo and YES i had! 
[COLOR="Blue"]**Certainly OOo does draw from /home/<user>/.fonts.**[/COLOR] 
Maybe it checks somewhere else too, but I couldn't figure out that yet. Perhaps somebody else knows more?

---

