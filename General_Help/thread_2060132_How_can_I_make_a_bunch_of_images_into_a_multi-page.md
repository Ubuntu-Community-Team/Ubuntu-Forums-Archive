---
title: "How can I make a bunch of images into a multi-page .pdf?"
date: 2012-09-19
forum: General Help
---

### Post by t0p on 2012-09-19
I've got a bunch of image files (some .jpg, some .png) that I want to make into a .pdf document - a multi-page document, with a single image file per page (like a comic book).  I did some searching and found an app called sam2p.  But looking at its README is confusing as heck.  If you want to make a multipage .pdf with sam2p you have to create a workfile, with all sorts of parameters and stuff.  Whoosh over my head.

What I'm trying now is copying the images and pasting them into LibreOffice Writer, one image/page after another.  And there are a fair number of images.  Can someone suggest a way to create my comic book pdf without all the repetitive copy > paste, copy > paste, copy > paste, copy... see, you're getting bored just *reading* about it.  Imagine what it's like for me, actually *doing* it!!

Please, someone save me from death by copy > paste!  A nice single-liner command would be good.  But please... anything but cop... nah, I'm sick of doing it, I'm not gonna keep writing it too!

Please?

---

### Post by Statia on 2012-09-19
I use gscan2pdf. Nice GUI and it works with pre-existing image files as well, in fact I have never even used the scan functionality.

---

### Post by cmont899 on 2012-09-19
You can insert the pictures into a open/libre office document and export as a PDF

---

### Post by HermanAB on 2012-09-19
Imagemagick has a program called convert, that can do pretty much anything with pictures, including multi-page pdfs.  Read the convert man page.  It is well worth the effort to add convert to your toolbox.

---

### Post by t0p on 2012-09-19
Thanks for the suggestions.  Tomorrow, when my brain reconstitutes itself from the slime currently oozing out my ears and down my cheeks, I will explore them.  Then I'll report back, hopefully to stick a [SOLVED] flag on this thread.

cmont899: what you suggest seems to be what I've already been doing.  And as I may have hinted in my original post, it's tedious tedious tedious.  Are you saying there's a way of inserting the pics without the slavish copy > paste for each image?  If so, please spell it out for me, cos I just can't see it.

Cheers all, and good night!

---

### Post by qyot27 on 2012-09-19
> **HermanAB said:**
> Imagemagick has a program called convert, that can do pretty much anything with pictures, including multi-page pdfs.  Read the convert man page.  It is well worth the effort to add convert to your toolbox.
Indeed, ImageMagick's convert command can do exactly this.  I've used it to create multi-page PDF files before.

It's ridiculously simple:
```
convert file1.png file2.png file3.png output.pdf
```
You could also use wildcards to avoid listing every page, if that's what you'd prefer.

---

### Post by crwalter on 2012-09-20
> **t0p said:**
> I've got a bunch of image files (some .jpg, some .png) that I want to make into a .pdf document - a multi-page document, with a single image file per page (like a comic book).  I did some searching and found an app called sam2p.  But looking at its README is confusing as heck.  If you want to make a multipage .pdf with sam2p you have to create a workfile, with all sorts of parameters and stuff.  Whoosh over my head.

What I'm trying now is copying the images and pasting them into LibreOffice Writer, one image/page after another.  And there are a fair number of images.  Can someone suggest a way to create my comic book pdf without all the repetitive copy > paste, copy > paste, copy > paste, copy... see, you're getting bored just *reading* about it.  Imagine what it's like for me, actually *doing* it!!

Please, someone save me from death by copy > paste!  A nice single-liner command would be good.  But please... anything but cop... nah, I'm sick of doing it, I'm not gonna keep writing it too!

Please?
You could also try selecting all of the files then print them to PDF.
This has worked for me in the past with Cute PDF in Windows.

It may also work in Ubuntu.

---

