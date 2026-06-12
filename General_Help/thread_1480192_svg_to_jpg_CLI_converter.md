---
title: "svg to jpg CLI converter"
date: 2010-05-11
forum: General Help
---

### Post by flapane on 2010-05-11
Hi,
any way to convert via a command line program a vectorial svg image into a pre definied-size jpg?

ie.
Input -> SVG
Output -> JPG 800x600

---

### Post by dv3500ea on 2010-05-11
[install]("apt:imagemagick") [imagemagick]("http://www.imagemagick.org") - that should do the trick

---

### Post by flapane on 2010-05-11
I already tried that, but it doesn't convert the y-axis tics of this **attached svg** file... as you can see in the output jpg it is empty:

convert dist.svg -font Times-Roman -pointsize 72 -resize 150% -antialias -unsharp 1.5x1.2+1.0+0.10 -quality 100 focal_lenghts_dx.jpg

[[IMG]http://i.imgur.com/JOaXOs.jpg[/IMG]]("http://i.imgur.com/JOaXO.jpg")

---

### Post by flapane on 2010-05-12
bump
Ne1 managed to succesfully convert the svg attached?

---

### Post by flapane on 2010-05-15
please :(

---

### Post by StuartN on 2010-05-15
> **flapane said:**
> please :(

Your svg file appears to be at fault - I don't see the graph in your post using gThumb, EoG or Gimp.

---

### Post by flapane on 2010-05-15
Weird, if you open it with Firefox it will work, and if you convert it with imageshack, it will work unless the y-axis tics (the main problem).

---

### Post by StuartN on 2010-05-15
> **flapane said:**
> Weird, if you open it with Firefox it will work, and if you convert it with imageshack, it will work unless the y-axis tics (the main problem).

Yes, I see it in Firefox, but it looks faulty if the other applications can not open it.

Perhaps you could open it with Inkscape and save as or export to bitmap. Even opening and re-saving with Inkscape should fix the file.

---

### Post by flapane on 2010-05-15
The problem is that I need to produce an automatized plot, so manually opening and saving it with 3rd pt sw isn't great.
The plot is produced by ploticus.
Any way to understand where's the problem?

---

### Post by StuartN on 2010-05-15
> **flapane said:**
> Any way to understand where's the problem?

You can open the .svg file with gedit and try to untangle why it is incompatible with other applications.

Can Ploticus generate the bitmap file directly?

I also see that the Ploticus site [http://ploticus.sourceforge.net/doc/svg.html](http://ploticus.sourceforge.net/doc/svg.html) recommends using rsvg [http://librsvg.sourceforge.net/docs/man-rsvg.php](http://librsvg.sourceforge.net/docs/man-rsvg.php)

---

### Post by flapane on 2010-05-15
No, it can only generate b/w bmp.
I tried with rsvg without luck (I obtain a 2px x 2px png or jpg file).
I finally fell back to eps, which works well (as long as you follow the chain eps->pdf->jpg, otherwise you'll have a black background, if -resize option is in use).

> convert dist.eps -resize 150% -font Times-Roman -pointsize 72 -quality  100% -compress lossless focal_lenghts_dx.pdf

convert -antialias -unsharp 1.5x1.2+1.0+0.10 -quality 100% -compress  lossless focal_lenghts_dx.pdf focal_lenghts_dx.jpg[[IMG]http://i.imgur.com/669R3s.jpg[/IMG]]("http://i.imgur.com/669R3.jpg")

Do you like it? Anyway I may consider raising the unsharp mask values:)

Thanks.

---

### Post by Hman242 on 2010-05-15
I don't know why I'm posting this, but oh well. Since yours isn't the dimensions you posted it's not completely useless.
[Here you go.]("http://img208.imageshack.us/img208/7884/distj.jpg")

---

### Post by flapane on 2010-05-15
Weird, seems like you managed to convert** y-axis tics** from that svg.
My ImageMagick 6.5.1-0 2009-08-27 should be bugged, then.
Thanks

---

### Post by Hman242 on 2010-05-15
If it matters I can tell you how I converted it.

---

### Post by flapane on 2010-05-15
Sure, thanks.

---

### Post by Hman242 on 2010-05-15
I use Inkscape to edit .svg images. I opened this .svg up, then click **File>Export Bitmap**. I click on the **Page** tab. I then enter 800 as the width. I press **browse** and I choose the save location and new file name. I press **Save** and then **Export**.

Since the dimensions aren't what you wanted, but you don't what to stretch the image you'll save it like I said and then open the .jpg in GIMP. Go to **Image>Scale Image**. Click the chain-link icon and then enter 600 as the image height. Click **Scale**. You will need to create a new layer by right-clicking [here]("http://img194.imageshack.us/img194/4303/screenshotog.png"). When the box pops up after you select **New Layer** you need to check the box next to **White**. You will then need to move the new layer to the bottom by dragging it there. Now all you need to do is save it.

---

### Post by flapane on 2010-05-16
Thanks.
Seemingly Inkscape can handle this a-little-bit-corrupted svg, while imagemagik doesn't.

---

