---
title: "Network Printer - Out of Memory problems"
date: 2010-01-27
forum: General Help
---

### Post by bigstoo on 2010-01-27
I have a HP Business Inkjet 2600 that I access via my network using a Jetdirect card.

I have created an image using GIMP. When I try to print it, I get an "Insufficient Memory" error on the printer and it is not printed.

Strangely though, I can print the exact same image from Windows XP (also using GIMP) with no problems.

I assume the Windows driver is able to send part of a page to the printer at a time, or something. Is there any way to do something similar in Ubuntu?

---

### Post by bigstoo on 2010-01-27
I've changed the driver from the default "HP Business Inkjet 2600 PS-RC-2.0" to "HP Business Inkjet 2600 Foomatic/Postscript" and it seems to have worked...

---

### Post by bigstoo on 2010-01-28
It seems I was a little hasty with my solution. Although it does print, it appears to be in a very low resolution and few colours.

I've since tried to use the latest HPLIP, which also causes problems. PS driver complains about insufficient memory. PCL3 driver complains about a personality error. I have a PCL3 card in it.

---

