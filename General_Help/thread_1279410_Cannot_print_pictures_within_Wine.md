---
title: "Cannot print pictures within Wine"
date: 2009-09-30
forum: General Help
---

### Post by bodam on 2009-09-30
I cannot seem to get pictures to print correctly under WINE.  I've tried both Evernote and Picasa 3.5 under WINE and I've tried printing to a Color LaserJet 2600n (network connected) as well as my HP PhotoSmart 7550 (USB connected).  The result is that text prints fine but pictures do not.

Here is a screenshot of an example note within Evernote.
[IMG]http://picasaweb.google.com/lh/photo/VGyNUm6plP68LGnsqEN1sg?feat=directlink[/IMG][http://picasaweb.google.com/lh/photo/VGyNUm6plP68LGnsqEN1sg?feat=directlink](http://picasaweb.google.com/lh/photo/VGyNUm6plP68LGnsqEN1sg?feat=directlink)

Here's how it prints:
[http://picasaweb.google.com/lh/photo/RnTGQazsv05vkJ9ya7fUPA?feat=directlink](http://picasaweb.google.com/lh/photo/RnTGQazsv05vkJ9ya7fUPA?feat=directlink)

Does anyone have any suggestions?
[IMG]http://picasaweb.google.com/lh/photo/RnTGQazsv05vkJ9ya7fUPA?feat=directlink[/IMG]

---

### Post by marmotapl on 2009-10-01
mmm... Maybe u can take a screenshot and then print it using a photo editor.

Cheers. (y)

---

### Post by akakingess on 2009-10-01
Can you use Gimp and print straight to the USB connected printer to bypass Wine? Or is that what you have tried and are getting the same result?

---

### Post by sedawk on 2009-10-01
I never tried printing with Wine - how does it work, do
you install windows printer drivers?

Like mentioned before, I recommend to do native Linux
printing.
This works as long as you want to print standard
documents and there is an application on linux
that can read the document:
gimp for images
evince for pdfs
OpenOffice for (older) M$-office formats.
...

For non-standard documents (which means there is no
Linux application that can read and display the
document properly) you could try to use a generic
postscript printer and print the document to a file.
Then view this file from Linux with ghostview or
evince and if the printout looks fine print it.
Either by sending it directly to the printer (if
you have a postscript printer) or by printing from
within evince.

(To simplify printing you could write a cronjob that checks if
some "print_it" directory contains newly exported print jobs
(e.g. postscript files) and send new files directly to the printer
without further actions from your side.)

---

### Post by bodam on 2009-10-01
> **akakingess said:**
> Can you use Gimp and print straight to the USB connected printer to bypass Wine? Or is that what you have tried and are getting the same result?

All of the native Linux-based printing work just fine.  I can print from Evolution, Firefox or GIMP just fine.  It's just the two WINE-based applications that don't seem to like printing pictures.

---

