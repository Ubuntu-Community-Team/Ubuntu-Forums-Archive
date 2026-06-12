---
title: "GIMP 2.6.10 question"
date: 2011-03-05
forum: General Help
---

### Post by Bowserdog on 2011-03-05
I'm running Ubuntu 10.10, and seem to be confused about how to do something with GIMP.  I have a rectangular image (about 600 X 600) with lots of area full of unwanted uniform static foreground color.  I guess what I want to do is a &quot;reverse crop.&quot;  If I crop an image, I select an area to KEEP and I eliminate everything outside of it.  Only what I want to do is select an area to REMOVE,  and keep everything outside of it.  Can this be done?  How?  It is easy to use the rectangle select tool and select a horizontal band (L to R).  But where can I go from there?  I've been trying a lot of ideas, but so far nothing seems to work.  I want to remove every image data point between 120 vertical and 200 vertical, and to put the retained image back together - only 80 pixels shorter.  I suspect there's a reasonable way to do something this simple.  Any help would be greatly appreciated.

---

### Post by flipper T on 2011-03-05
make your selection as described

go to select and choose invert

that should do the trick

---

### Post by WorMzy on 2011-03-05
Once you've drawn your selection box, make sure you have the right layer active, then press delete; GIMP will then discard all colour information inside the selection box. If the layer has an alpha channel, it'll make the selected area transparent, otherwise it'll replace the area with the background colour.

EDIT: I guess I misunderstood the question.

If you're just trying to make the image 80px shorter, would the Image -> Canvas Size tool do what you need?

---

### Post by Bowserdog on 2011-03-05
Didn't seem to help.  Perhaps I'm not actually selecting the area.  I open the unedited drawing, choose the rectangle select tool, mark out my rectangle - and I get a dashed line on my image where the rectangle SHOULD be.  But Select -> Invert seems to do nothing whatsoever.

---

### Post by flipper T on 2011-03-05
you won't **see** anything

invert inverts the selection

from there you can copy/cut/paste to your heart's content

---

### Post by Bowserdog on 2011-03-05
OK.  Now it's closer.  I can select the rectangular area I want to edit out, and pressing delete leaves me with a blank white rectangle formerly occupied by data I want to remove.  I now have two disjoint bands, one with the top of the info I want to save, and a separate band with the bottom of the info I want to save.  Any attempts to save that image yield a white band through the image's middle.  But what I want is to top band + the bottom band with NO white band in the middle.  I want to reverse crop a L-R band from the image.  Can I create just one image containing only the data I want to save?  Obviously, I could crop only the top portion I want to save, as a new image.  Also, I could also crop only the bottom portion as another new image.  Is it possible to copy these two images into a different new image - and put the top directly above the bottom?  In other words: can one eliminate the L-R band in the middle?

---

### Post by flipper T on 2011-03-05
ok now i understand

the answer is......no

as far as i know

just copy & paste into new image & join up manually

---

### Post by Bowserdog on 2011-03-05
Thanks  That worked!  Whoop! Whoop!

---

