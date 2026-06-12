---
title: "OCR with cuneiform and YAGF"
date: 2011-03-25
forum: General Help
---

### Post by duamau on 2011-03-25
If you are looking for a decent OCR solution for Ubuntu, try installing cuneiform from the package tree and YAGF from their site. Cuneiform delivers pretty accurate results while YAGF provides a good user interface to this otherwise command line driven software.

[IMG]http://symmetrica.net/cuneiform-linux/yagf-en.jpeg[/IMG]


[http://gnu.ethz.ch/debian/yagf/yagf_0.8.1-1_i386.deb]("http://gnu.ethz.ch/debian/yagf/yagf_0.8.1-1_i386.deb")

Hope this is of use.

---

### Post by legatek on 2011-04-08
Are there any 64-bit builds out there?

---

### Post by robert shearer on 2011-04-08
I too have had a lot of success with this combination.
Cuneiform, unlike tesseract, can recognise and maintain columns.

Mostly I use my Dslr to photograph pages of text then open the files in Fotoxx and select the 'Art effects - simulate drawing' to enhance the contrast and sharpness.
This really works well for text !.

Next, still in Fotoxx I use the 'Transform - rotate' option to get text lines as horizontal as possible. Fotoxx allows rotates of points of a degree in real time.

If images still show some localised aberrations  (bowing,bending etc) I use the 'Warp area' option to drag areas and apply some 'un-warp'. Try it and you will see what I mean.

Finally I crop and move to YAGF for  final adjustment and ocr processing.

Using this workflow I achieve 100% ocr results about 8 out of 10 uses and the other 2 have minor corrections needed, usually less than 5 errors.

Cheers,
Bob.

@legatek  64bit YAGF here...
[http://www.getdeb.net/software/yagf](http://www.getdeb.net/software/yagf)

Cuneiform is in the repos.

---

### Post by duamau on 2011-04-08
> **legatek said:**
> Are there any 64-bit builds out there?

I am not certain about 64 bit.

---

### Post by duamau on 2011-04-08
> **robert shearer said:**
> I too have had a lot of success with this combination.
Cuneiform, unlike tesseract, can recognise and maintain columns.

Mostly I use my Dslr to photograph pages of text then open the files in Fotoxx and select the 'Art effects - simulate drawing' to enhance the contrast and sharpness.
This really works well for text !.

Next, still in Fotoxx I use the 'Transform - rotate' option to get text lines as horizontal as possible. Fotoxx allows rotates of points of a degree in real time.

If images still show some localised aberrations  (bowing,bending etc) I use the 'Warp area' option to drag areas and apply some 'un-warp'. Try it and you will see what I mean.

Finally I crop and move to YAGF for  final adjustment and ocr processing.

Using this workflow I achieve 100% ocr results about 8 out of 10 uses and the other 2 have minor corrections needed, usually less than 5 errors.

Cheers,
Bob.

@legatek  64bit YAGF here...
[http://www.getdeb.net/software/yagf](http://www.getdeb.net/software/yagf)

Cuneiform is in the repos.

Robert, tell us more about fotoxx. I have missed this one over the years.

---

### Post by robert shearer on 2011-04-09
> **duamau said:**
> Robert, tell us more about fotoxx. I have missed this one over the years.

It is in the repos, search in Synaptic or Software centre and install.

Home page and info/manual from here....
[http://kornelix.squarespace.com/fotoxx/](http://kornelix.squarespace.com/fotoxx/)

---

