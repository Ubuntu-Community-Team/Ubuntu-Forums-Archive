---
title: "GIMP Command to process batch?"
date: 2010-12-24
forum: General Help
---

### Post by U2XS on 2010-12-24
I don't know if it's possible but GIMP is able to receive command line arguments, so why not?  Basically, I want to create a batch (action, macro or what it may be called) and then set up a cron job which will run every hour.  So, it would be something like "If an image is in X folder, then resize, watermark & move it to Y folder"

Is this possible?  If so, is a tutorial or a previous thread available?  I can't find one yet.

---

### Post by noah++ on 2010-12-24
I think you're looking for ImageMagick CLI tools such as [mogrify]("www.imagemagick.org/www/mogrify.html").

---

### Post by U2XS on 2010-12-24
Woah!  This is exactly what I wanted and it's *significantly*  easier than I expected.  Thanks!

---

