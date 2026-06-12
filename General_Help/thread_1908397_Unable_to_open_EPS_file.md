---
title: "Unable to open EPS file"
date: 2012-01-13
forum: General Help
---

### Post by Paddy Landau on 2012-01-13
I have been asked to help someone open an EPS file. The file is several years old, and the original creator, unfortunately, is long gone, so we don't even know what software was used.

However, looking at the file in a hex editor reveals this:```
 PS-Adobe-3.0 EPSF-3.0
```When I save the file on my desktop, I can see the image in the icon, but only its black-and-white outlines.

However, I cannot do anything else with it.

[LIST]
[*]Libre Office Writer: Shows a blank outline.
[*]Libre Office Draw: The same.
[*]GIMP: "Encapsulated PostScript image plug-In could not open image"
[*]Inkscape, convert and gs all give:```
Error: /undefined in 
```
[/LIST]
Unfortunately, I do not know what else to do.

Are you able to help? I have attached the EPS file, bzipped because Ubuntu Forums won't allow me to load EPS directly.

---

### Post by Wayne_V on 2012-01-13
try:

$ convert file.eps file.jpg

== never mind - I see you tried that already

---

### Post by Wayne_V on 2012-01-13
The file was created with corel draw so I would try that if possible:

> %!PS-Adobe-3.0 EPSF-3.0
%%BoundingBox: 5413 4007 5646 4276 
%%LanguageLevel: 1
%%Creator: CorelDRAW 12
%%Title: Kennington Parish Shield#1.eps
%%CreationDate: Fri Jun 18 12:27:06 2010
%%DocumentProcessColors: Black 
%%DocumentSuppliedResources: (atend)
%%EndComments
%%BeginProlog


---

### Post by Paddy Landau on 2012-01-13
> **Wayne_V said:**
> The file was created with corel draw so I would try that if possible:
Thanks for the idea. I downloaded a trial version, installed onto Windows, and... it also could not open it!

I have discovered that I can view it in Evince. So, I have viewed it at the largest my screen will take, taken a screen-shot, and trimmed it.

There is no colour (only outlines), but I can add colour. By no means is it ideal, but I have something!

If you have any further ideas, I'd love to hear them.

---

