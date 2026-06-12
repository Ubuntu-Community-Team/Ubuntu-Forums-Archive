---
title: "Open Office slow loading odp, but fast loading ppt.  Normal?"
date: 2009-07-02
forum: General Help
---

### Post by laptoplinux on 2009-07-02
I've noticed that if I load an image-heavy odp presentation in Impress, it takes a long time to load, making the window turn grey (the "not responding" indicator) several times in the process.  It does eventually load and become responsive, though.

If I convert the same presentation to ppt format, and open it again (on a reboot to make sure it isn't given an advantage due to the cache), the ppt presentation loads much more quickly and responsively.  

I'm using OpenOffice 3.1 on 8.04 Hardy (it did the same thing on vanilla 3.1 from the website and on the 3.1 package from the in the hardy PPA.)

Is this normal?  Or is there something I can do to tweak it so that odp files will load faster?  I had wanted to use odp as my primary presentation archiving format, but I may need to use ppt if the performance difference is going to be like this.

---

### Post by laptoplinux on 2009-07-30
Bumping to see if anyone new might find this and know something.

---

### Post by forestforger on 2011-03-19
The same behavior here. ODP with lots of images is absolutely unresponsive and the window grays out all the time, but it works fine when saved as PPT. On Ubuntu 10.10, open office 3.2 running on an eee pc 1018p.

---

### Post by Zimmer on 2011-03-19
[http://blogs.sun.com/abhi/entry/embedding_images_in_openoffice_text](http://blogs.sun.com/abhi/entry/embedding_images_in_openoffice_text)

May go some way to answering your query..

EDIT:
Sending an ODP file without embedding.
If you create a presentation normally with images/objects it is important that you save the file and the images objects in a discreet folder and send the whole folder to the recipiant...

---

### Post by forestforger on 2011-03-19
Thank you for the helpful answer. I copy-pasted a lot of images from PDF files into my ODP presentation on my home computer. Then I copied the presentation to my portable computer. On my portable the ODP then became super unresponsive. When saved as a ppt solved the problem. But based on my work process of copy-paste from PDF's I do not have the pictures saved anywhere. Is there an option in open office that I could change in order to solve this problem? Would be nice if I would not have to save it as a ppt everytime.

---

### Post by Zimmer on 2011-03-19
As per that link, it is required that when you have pasted the images into Impress that you BREAK the links and embed the images.

It is worth noting that you should also think to optimise the images before inserting into Impress else you may end up with a very large odp file... 

I may look into this further for more tips on image embedding etc.

---

### Post by Hagar Delest on 2011-03-20
You can also try the vanilla version, perhaps the Ubuntu version has a glitch: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

