---
title: "How can I merge two images into one PNG?"
date: 2012-02-21
forum: General Help
---

### Post by nrundy on 2012-02-21
Is this possible?

I can use PDFShuffler to "combine" two PDFs into one PDF. Is there a way to combine two PNGs into one PNG? It'd be nice to be able to open a PNG that shows two images side by side.

---

### Post by cbanakis on 2012-02-21
I have a Photoshop script for creating 2 page pdf's
The only other way I know of, is to us Acrobat. (Acrobat, NOT Acrobat Reader)
(I'm sure there are other ways, but thats how I do it)
With my script, you can combine any 2 files that Photoshop can open, into a 2 page pdf file. 


If you have Photoshop, let me know, and I'll post the script with some instructions.
Photoshop CS2 works perfect in Ubuntu with Wine.
(No tweaking at all, it just installs, and works as if you were using Windows)
Or at least it works perfect for me.

I do not think png's support multiple pages.
The closest you can get to that, would be if you used Photoshop, or Gimp, to have a 2 layered png.
(1 Layer for each image)

But that method would only be useful if you view the file using either Photoshop, or Gimp.
(Otherwise, you would only be able to see whatever layer is on top)

---

### Post by nrundy on 2012-02-21
don't have photoshop. JPEg WOULD BE FINE IF PNG DON'T WORK

---

### Post by cbanakis on 2012-02-21
I'm pretty sure pdf if the only "universal" format that allows multiple pages.
Maybe you can with a Microsoft XPS document, but I have never seen any tools for editing them.

You can convert anything into a pdf with the right tools.

but you cannot have a multiple page jpg, png, psd, bmp, or really anything, other than pdf.

---

### Post by nrundy on 2012-02-21
I'm not specifically asking for multiple pages.

Consider this: I'm submitting a bug report to Launchpad. I want to upload two PNGs, each of a small screenshot from my desktop. Is there a way to make one PNG that displays each image (i.e., one image on the left and one image on the right)? Or must I upload two sepearate PNGs?

---

### Post by cbanakis on 2012-02-21
Oh, thats all?

Thats actually pretty simple.
You can do it in Gimp, or in any image editor.

All you do is create a new document, change the size so its double the width of your images.

then copy, paste, arrange, and save.

Gimp is in the software center.

there is a bit of a learning curve to figure out how to use Gimp, but it will definitely get the job done.

> **nrundy said:**
> I'm not specifically asking for multiple pages.

Consider this: I'm submitting a bug report to Launchpad. I want to upload two PNGs, each of a small screenshot from my desktop. Is there a way to make one PNG that displays each image (i.e., one image on the left and one image on the right)? Or must I upload two sepearate PNGs?

---

### Post by nrundy on 2012-02-21
How exactly do I get the pngs into GIMP. Is there an Import function that GIMP provides?

---

### Post by Dy1anW on 2012-02-21
"File>Open as layers..." is the function you are looking for. There's probably a few ways of doing it, but this way you can move the image around and align them as necessary.

---

### Post by nrundy on 2012-02-21
Thanks a lot guys for helping me out! 

I'll be trying this out later today.

---

### Post by aeronutt on 2012-02-21
[http://www.fmwconcepts.com/imagemagick/](http://www.fmwconcepts.com/imagemagick/)

Check out the 'adjoin' script.

---

