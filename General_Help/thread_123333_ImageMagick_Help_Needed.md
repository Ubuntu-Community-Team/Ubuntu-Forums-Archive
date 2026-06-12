---
title: "ImageMagick Help Needed"
date: 2006-01-29
forum: General Help
---

### Post by peterbrowne on 2006-01-29
I currently use
```
peter@peter:~$ composite -gravity SouthEast watermark.gif image.jpg image.jpg 
```
to watermark my images, but I now have a folder with ~80 images that i need to watermark.

Is this possible (to do them all at once) or will i have to spend a few hours doing it?

---

### Post by dickohead on 2006-01-29
how much do you know about bash scripts?

You could always write a loop that takes every *.jpg file and applies the gif watermark to them...?

---

### Post by ivancruz on 2006-01-29
Welcome to the wonderful word of find command. Try:

find <pathOfImageFiles> -name '*.jpg' -exec composite -gravity SouthEast watermark.gif \{\} \{\} \;

I don't know ImageMagick, so I'm supposing image.jpg are both input and output files. In the find command, the special character pair {} substitutes the name of file found. Semicolon is used to tag the end of -exec parameter list. All those symbols must be escaped.

Also pay attention to -name parameter. When using patterns, always enclose it on single quotes to avoid shell expansion.

Ivan

---

