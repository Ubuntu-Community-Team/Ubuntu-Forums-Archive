---
title: "Filling out a pre-printed form"
date: 2010-01-04
forum: General Help
---

### Post by natgwil on 2010-01-04
I have a pre-printed form that I need to fill in. Is it possible to scan it, fill it in on screen, and then put the original form in the printer and get things to print out on that original form? I know that I can scan the form and fill it in on screen and print out on a blank piece of paper, but I need to use the original form. Any suggestions would be much appreciated.

---

### Post by stoneage on 2010-01-04
It may be possible if you scan it to .pdf, then you could maybe use a .pdf editor to fill in the blanks.

If all else fails a simple hack is to open the .pdf with Gimp and enter the text that way.

---

### Post by pricetech on 2010-01-04
You can scan it as an image and add the text that way.

---

### Post by natgwil on 2010-01-04
Thank you for the above suggestions. However isn't that printing out a *copy* of the form (with my entries added), rather than printing out my entries on to the *original* form?

---

### Post by pete-the-meat on 2010-01-04
why not scan the form, then add it to a page in scribus - add text boxes to the page and add your text, then delete the image before printing?

---

### Post by underquark on 2010-01-04
Method 1
Scan it with high contrast, low-bit monochrome.  Recolour it to red or whatever.  Insert your text as black.  Delete (change to white) all the red bits.  Photocopy the original form a few times to practice printing the text onto it.

Method 2
OpenOffice has a means of placing a watermark onto a document.  I haven't done this in OpenOffice though have done it in MS Office.  Place the scanned form as a watermark.  Type text over it.  Print (again do some practice on photocopies) but don't print the watermark.

Method 3 (only for a few, big blocks of text)
Measure with a ruler where the blocks of text are to go.  Set paper margins to enclose first text block.  Type, print out, repeat with different measurements for different blocks.

Method 4 (my preferred method)
Bribe/flatter/seduce a secretary who is in possession of a real typewriter.

---

### Post by michy99 on 2010-01-04
Scan the form and open it in GIMP. Make a new, transparent layer and use the text tool to fill in the blanks. When you have all the text in position and sized correctly, merge all the text to the transparent layer. Hide the original layer and print the text onto the form.

---

### Post by natgwil on 2010-01-05
Thanks for the suggestions. I haven't had time to try them out yet but will soon.

---

### Post by natgwil on 2010-01-11
I have tried the Scribus method and the GIMP methods suggested above. The basic idea seems to work well. I can get everything just right on screen and then remove the original image as suggested. But I can't get the results to print out correctly. Through trial and error I've discovered that the problem is the scanned version of the form. No matter how many times I try to scan the original form, when I try printing it out it's smaller than the original. This obviously affects the placement of the text onto the form. How can I correct this?

---

### Post by stoneage on 2010-01-11
I'm guessing it is something to do with page margins. 

Try to find what the printer's settings are, maybe it imposes a margin. It could also be the application you print from.....

---

### Post by michy99 on 2010-01-11
You can use the Scale Image function in GIMP to get it to the right size.

---

### Post by todak on 2010-01-11
Is there an underlying reason that you cannot fill out the original form using a pen or pencil, rather than going through the complex processes outlined above? Not being a smartypants, I'm just curious as to why it must be printed instead of written.

---

### Post by junapp on 2010-01-11
I'd go the scribus route. Scan the form, place on a scribus page which is equal to the physical size of your form, then make sure your image fills the document boundaries. Might even be worth finding one of those little plastic rulers and scaning that right along with the pdf for comparison sake/scaling in scribus.

Will you be merging this with data from another app at some point? Not sure if scribus handles data merges, but I'm sure a python script could be adapted to accomplish. 

Might also be doable with going straight to pcl/ps (but only if you love that sort of thing) - would sort of depend on how frequently you are doing this and how customized you need it.

I'm sure someone else will post a link to some software already in the repos that does this exactly.

edit: care to upload your scanned form?

another link outlining a more complex method, but probably good if you had many to deal with (insert your language of choice for ruby):
[http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/60015](http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/60015)

---

### Post by natgwil on 2010-01-13
Used the scale image function in GIMP and it worked. Now everything's working. Thanks for the help guys!

---

