---
title: "Simple HTML help"
date: 2011-01-12
forum: General Help
---

### Post by West201 on 2011-01-12
I'm trying to add an image to a HTML document. However Firefox is not adding the image. Even after saving the HTML doc & refreshing Firefox several times

I tried it using these codes:
> <IMG SRC="jesse/Photos/?.jpg"/>
<IMG SRC="?.jpg"/> (imaging being in the same folder as html doc)

This method works with Windows, but I don't if I have to do anything different with Ubuntu.
 
Thanks :)

---

### Post by James_Lochhead on 2011-01-12
Try renaming the file, the question mark might be causing problems. Also, I think your first attempt has an incorrect path.

Try renaming the file: questionmark.jpg

Then try:

<img src="/home/jesse/Photos/questionmark.jpg" />

OR

<img src="questionmark.jpg" />

OR maybe this:

<img src="./questionmark.jpg" />

P.S. This is probably the wrong place the post HTML questions. The programming forums might be better.

---

### Post by West201 on 2011-01-13
Thank You for replying ! It worked like a charm :popcorn: 

Great Answer :)

---

