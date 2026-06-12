---
title: "Need pdf darker, recommend tool or utility, please!"
date: 2010-08-17
forum: General Help
---

### Post by aaronchall on 2010-08-17
Greetings,

I have a pdf from my wife that is too light/gray. I would like to make it completely black where the gray is, and completely white where white is. Please recommend a utility or tool that can accomplish this!

Thank you!

Aaron

---

### Post by HermanAB on 2010-08-17
The Gimp.

---

### Post by KeyserSoze93 on 2010-08-17
Install the package "imagemagick". It can deal with images and pdfs, and perform all manner of tasks on them.

You'll basically want to convert the pdf to a set of images, change the brightness, and then convert all of them back to a PDF.

This can all be done with the "convert" and "mogrify" commands which come with imagemagick. Check out the online documentation.

One thing that it is worth noting is that imagemagick  names the pages without padding the numbers, so after you've converted the pdf to images, you'll need to run a command such as:

```

rename 's/blah-(\d*).png/sprintf "blah-%03d.png", $1/e' *.png

```

Where blah is the prefix for your images.

It sounds rather confusing, but it's quite easy once you get used to it.

---

### Post by junapp on 2010-08-17
something like imagemagick should do the trick.
for example:
convert mywifesfile.pdf -monochrome darker.pdf
or if that's not quite what you are after, maybe the black-threshold option
convert myfile.pdf -black-threshold 50% darker.pdf
Sort of depends on what the original file looks like - does it have any colour?

---

### Post by aaronchall on 2010-08-17
I've tried opening it with the Gimp, but it opens everypage in different screens, and i'll wind up with 40 or so screens. A batch approach would be great, I'd like to try imagemagick, but I'm no pro on the command line, so I'd need someone to walk me through it (actually, just an example of how to batch a contrast curve would be great, and I could tweak the numbers until it looks good). Otherwise, I'm going to have to make them rescan their stuff darker. 

I know there's batch processing for the Gimp too, and I have a single curve that should work for each page, but that looks even more complicated than imagemagick...

Aaron

---

### Post by aaronchall on 2010-08-17
> **junapp said:**
> something like imagemagick should do the trick.
for example:
convert mywifesfile.pdf -monochrome darker.pdf
or if that's not quite what you are after, maybe the black-threshold option
convert myfile.pdf -black-threshold 50% darker.pdf
Sort of depends on what the original file looks like - does it have any colour?

Thanks for this, Junapp, but can you suggest a curve approach? Or perhaps it's in the documentation? It looks like it would do all pages at the same time...

I saw this only after posting my first reply...

Aaron

---

### Post by aaronchall on 2010-08-17
After a bit of experimentation with the imagemagick tool convert, this gives a result in the right direction:

```
convert music1.pdf -contrast-stretch 2%x20% music1C.pdf
```

This command means to "Convert the old file with contrast stretch with at most 2% black pixels and at most 20% white pixels to the new file."

It's a music score, so the ranges are appropriate (actually, it changes very little even making white 1%), but I think my problem is that it's stretching it linearly while I really need a curve. 

The problem with this is it gives a pixelated looking result, which is inferior to what I got with Gimp. It appears to be losing resolution. (My original pdfs are high resolution, high detail, while my new pdfs are lower resolution and lower detail.)

I learned about the function from this page: [http://www.imagemagick.org/script/command-line-options.php#list](http://www.imagemagick.org/script/command-line-options.php#list)

I don't know if imagemagick is the way to go, though. 

Based on my experience with Gimp, I believe my best curve, where black to white is a scale of 0 to 100, is f(x) = (x^3)/10000, where x is the original pixel and the function is the new pixel.  This curve takes most gray to black pixels and makes them darker, while only leaving the whiter pixels white.

Thoughts?

---

### Post by aaronchall on 2010-08-17
Ok, I figured out how to convert with a curve:

```
convert music1.pdf -function polynomial 1,0,0,0 music1C.pdf
```

This reads "Convert original file with a function, polynomial, with f(x) = 1*x^3 + 0*x^2 + 0*x^1 + 0*x^0, into a new file."

This gives my result from the previous post, but black is 0 and white is 1. 

The problem with resolution remains. I am losing resolution. I have identified it by making a 1 to 1 conversion with the above command substituting 1,0,0,0 with 0,0,1,0.

Is there an option to keep my resolution? 

Aaron

---

