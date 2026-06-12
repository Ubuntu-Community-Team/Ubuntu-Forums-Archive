---
title: "how to install imagemagick"
date: 2009-11-12
forum: General Help
---

### Post by tyler.mcg on 2009-11-12
So I got kubuntu 9.10 and I don't know how to install this program. When I go into package manager it says "X" and if I click it, it asks are you sure you want to remove imagemagick. Well, AFAIK it's not in my k-menu anywhere if I use the desktop search or alt-f2 cant find it either. So how can I install this? 

Or if all else fails how can I change a pdf to jpg?

---

### Post by oldos2er on 2009-11-12
imagemagick is just a bunch of CLI programs in one package, so there's not going to be a menu entry. Maybe this thread will help: [http://ubuntuforums.org/showthread.php?t=489877](http://ubuntuforums.org/showthread.php?t=489877)

---

### Post by delcypher on 2009-11-12
You may already have the program installed. In your terminal run
```
aptitude search imagemagick
```

If you see an i next to it, then it's installed. Like on my system I see
```
p   graphicsmagick-imagemagick-compat                       - image processing tools providing ImageMagick interface            
i A imagemagick                                             - image manipulation programs                                       
p   imagemagick-dbg                                         - debugging symbols for ImageMagick                                 
p   imagemagick-doc                                         - document files of ImageMagick  
```

As far as I know imagemagick is command-line based and doesn't come with a graphical frontend. To convert a pdf to jpg as you ask I believe the command would be as follows:
```
convert inputpdf.pdf output%d.jpg
```

This will create a series of images output1.jpg, output2.jpg,.. for each page of your pdf.

If you want a particular page out of your pdf then use
```
convert inputpdf.pdf[0] output.jpg
```
where 0 is the 1st page of the pdf, 1 is the 2nd page, etc...

If you'd rather work with a graphic user interface (GUI) then the GIMP can open your pdf file for you.

Have fun!

---

