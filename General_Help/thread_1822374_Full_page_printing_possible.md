---
title: "Full page printing possible?"
date: 2011-08-10
forum: General Help
---

### Post by landersohn on 2011-08-10
I am not sure this is the right forum, if not, please let me know whether there is a better one.

I would like to print full page on a HP Deskjet F4280 using any kind of software (GIMP for example).
I tried to edit the printer ppd file, turned hardware margins off in the print properties in GIMP, yet when I try to print an image 8.5 in wide on letter size paper, GIMP still leaves approx. 1/8in gap on the paper edge.
The printer hardware can do it: when I simply use the copy function it can print to the very edge of the paper.

Question: does anybody know how I need to edit the ppd file (or other config files) to convince GIMP (or other programs) to print using the full page?

---

### Post by HermanAB on 2011-08-10
Hmm, no idea.

However, I'm wondering how wise that would be in terms of gumming up the printer works due to overspray?

---

### Post by papibe on 2011-08-10
Try this: in the print window, go to the page handling tab. There, set the field 'Page Handling' to either 'Shrink to Printable Area' or 'Fit to Printable Area'.

Hope it helps.
Regards.

---

### Post by dFlyer on 2011-08-10
Have you installed hplip-gui. This is what I use for full page photo photo printing with 11.04 and 10.10.

---

### Post by landersohn on 2011-08-10
Thanks for your help, I'll try these suggestions

---

