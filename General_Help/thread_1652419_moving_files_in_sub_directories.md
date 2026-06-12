---
title: "moving files in sub directories?"
date: 2010-12-24
forum: General Help
---

### Post by sr_guy on 2010-12-24
I just recovered some photos that were deleted by accident, and the way the photos were stored is a bit of a pain to re-organize. So I was wondering if there was a quick way to move files stored in this fashion:

Directory structure:

pictures  ----- main dir
 
  a --- subdirectory
  b --- subdirectory
  c --- subdirectory
  d --- subdirectory


jpg's are in each sub dir. So is there a way to scan/move all jpg's in the "pictures" sub directories and move them all to the pictures directory easily?

---

### Post by nice_like_rice on 2010-12-24
How about...

find -iname *.jpg -exec mv {} ./ \;

from inside the pictures directory.

Check if they are called .jpg, there's also the JPEG naming convention I believe :)

---

### Post by sr_guy on 2010-12-24
Ok that works.

But what does this section do?

{} ./ \;

---

### Post by nice_like_rice on 2010-12-24
mv takes 2 arguments.

mv source destination

So for every jpg "find" finds, it does mv {} ./

Where {} is source, ./ is destination

{} is the path of the file it has found, like /path/to/pictures/a/something.jpg.

./ just means current folder

So overall mv moves whatever jpgs it finds to the current folder.

The \; bit is required by -exec. It just tells exec that the command has ended with the semicolon. The \ is required to escape the semicolon, otherwise the shell would interpret it as being the end of the command!

I don't think thats an amazing explanation, but hopefully you'll understand what I mean?

---

### Post by sr_guy on 2010-12-24
I did not know that about {} ./


I hate syntax stuff, but it's nice to pick up something new in a simple way, unix books explain stuff in a way too complex way =)

---

