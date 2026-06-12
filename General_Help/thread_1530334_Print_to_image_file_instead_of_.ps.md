---
title: "Print to image file instead of .ps?"
date: 2010-07-13
forum: General Help
---

### Post by trentscott on 2010-07-13
Is it possible to print a page to an image file (gif, jpeg, etc.) instead of a .ps? Not looking to take a screenshot, rather print an entire page.

---

### Post by gsgleason on 2010-07-13
press the PrtScr button on the keyboard.  You can also print to PDF, then use gimp or something to export to an image.

Very weird request, though; seems very inefficient.

---

### Post by mike555 on 2010-07-13
if you mean a web page , there are add-ons for that ...

---

### Post by GuiGuy on 2012-04-25
Install imagemagick:
 
sudo apt-get install imagemagick


Then, to convert a single file:

convert mydoc.pdf mydoc.png


or, to convert a bunch of files

convert *.pdf *.png

See 

man convert 

for more options and usage.

---

### Post by coffeecat on 2012-04-25
Old thread closed.

---

