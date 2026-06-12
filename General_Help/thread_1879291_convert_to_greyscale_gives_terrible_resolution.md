---
title: "convert to greyscale gives terrible resolution"
date: 2011-11-11
forum: General Help
---

### Post by Paddy Landau on 2011-11-11
I wish to convert pictures to greyscale. I need to use a script for this.

Now, if I open a picture with GIMP and convert to greyscale, the result is usually excellent.

But if I use the command line (as I say, I need to use a script), I get shocking results. I've tried the following commands:
```
convert -monochrome colour.jpg mono.jpg
convert -flatten -monochrome colour.jpg mono.jpg
convert -monochrome -quality 100 colour.jpg mono.jpg
```None of those produces a useable picture.

As an example, I have attached three pictures. The first is the original; the second, converted with GIMP; the third, converted with convert. Despite having terrible quality, the file size of the last is double that of each of the others.

I notice that convert also has the option -separate, but that produces three different pictures with differing shades, and I don't know what to do with them.

How can I convert a picture to greyscale using the command line?

---

### Post by Paddy Landau on 2011-11-11
I've solved it. I need to use -flatten with -separate. Seems obvious in hindsight.

---

### Post by JKyleOKC on 2011-11-11
> **Paddy Landau said:**
> I notice that convert also has the option -separate, but that produces three different pictures with differing shades, and I don't know what to do with them.I can't help with your main question, but I can tell you what this option does: it creates "color separation" images that a printer could use to set up color printing. However I don't know whether it separates out the red, green, and blue components, or creates the cyan, magenta, and yellow that a printer would need -- and the man pages for all the ImageMagick tools are quite lacking in details.

I've come across web sites devoted to the ImageMagick suites, but don't have them bookmarked so cannot provide direct links. The ones I found, however, were quite detailed and told me much more than I really wanted to know about the "convert" options for which I was looking!

Your sample images show that the bad one actually used dithering to reduce the colors to just black and white, no shades of grey at all. I don't find any other option for converting to "greyscale" however...

---

### Post by Paddy Landau on 2011-11-11
Thanks for the answer. I suspected that about the separation, yet (as you can see from [post=11446818]post #2[/post]), it works provided I flatten it.

Oh, well, so I'm a bit confused, but at least it works.

---

### Post by Paddy Landau on 2011-11-11
I spoke too soon, because it seems the way I do it saves only one of the three separated parts.

First: To be clear about this, because it makes a difference in some cases:

You need to separate first, then flatten.

```
convert bird-original.jpg -flatten -separate bird.tif  [COLOR=Navy]# Gives a TIF with three pages.[/COLOR]
convert bird-original.jpg -separate -flatten bird.tif  [COLOR=Navy]# Gives a greyscale TIF with one page.[/COLOR]

convert bird-original.jpg -flatten -separate bird.jpg  [COLOR=Navy]# Gives three numbered JPG files.[/COLOR]
convert bird-original.jpg -separate -flatten bird.jpg  [COLOR=Navy]# Gives a single greyscale JPG.[/COLOR]
```But the result is not the same as that saved by GIMP; the quality is quite obviously worsened.

So, I still need to know...

---

### Post by JKyleOKC on 2011-11-11
Here's a link to the full documentation:

[http://www.imagemagick.org/script/convert.php?ImageMagick=dvf3bb378goushi0nkseihuvi2](http://www.imagemagick.org/script/convert.php?ImageMagick=dvf3bb378goushi0nkseihuvi2)

And here's the site I mentioned earlier in this thread:

[http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

From the detailed descriptions of "convert" on the first site, it looks as if adding "-channel ALL" to your options just might improve the quality...

EDIT: Check this link; looks like exactly what you want: [http://www.imagemagick.org/Usage/color_mods/#grayscale](http://www.imagemagick.org/Usage/color_mods/#grayscale)

---

### Post by Paddy Landau on 2011-11-11
@JKyleOKC: Thank you, thank you!

The various options are flexible indeed, and the first one there (-colorspace Gray) is the perfect one; even better than GIMP.

I can mark this as solved.

---

### Post by JKyleOKC on 2011-11-11
You're quite welcome!

As always happens in such threads, I learned a lot too that will help me in putting together the 40-page quarterly magazine that I edit for my school's alumni association. It has 8 pages of full color in each issue, and I try to average more than one photo per page since just type looks so boring.

I have to use Windows to do the final file that goes to our printing firm, but can use anything I like prior to doing that final version, which means I can use ImageMagick for all the pre-press manipulation of the photos -- which can vary widely in quality. While searching for the grayscale information I came across a major article (it's on that "usage" page) showing how to deal with underexposed images. It truly works wonders with the groups I tested on, in which the flash intensity had fallen off so sharply that the person at the right edge of the photo was almost washed out while the person at the left was almost lost in darkness. I still have a lot of experimenting to do with it, but it certainly seems to be more powerful than GIMP!

I was already set up with a script using "convert" to re-size the original digital images to my standard 2-column width of 1485 pixels at 300 dpi resolution, while improving saturation and contrast somewhat at the same time. Now I can correct those pesky lighting imbalances, too!

---

