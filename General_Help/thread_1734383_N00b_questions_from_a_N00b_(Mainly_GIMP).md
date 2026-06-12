---
title: "N00b questions from a N00b (Mainly GIMP)"
date: 2011-04-20
forum: General Help
---

### Post by BK2FUT on 2011-04-20
Hey there!

So, I'm a dedicated Android user on my mobile devices, but I've just jumped into Ubuntu as a desktop operating system.

My work computer runs Ubuntu 10.10 - the Maverick Meerkat, and I'm floundering a little.

Until now I've been a Windows user (not all that happily I might add.)

Anyway, I was hoping you kind, wonderful people might help an amateur become a little more productive at work. :D:D:D

Firstly, I love GIMP, works well, I'm using 2.6.10.

The thing is, I have to create specific-sized images as part of my job, 200 x 200 thumbnails.

I've figured out a fairly quick way to crop to a maintained 1:1 aspect ratio.

What I'd like to know** is there any way of creating keyboard shortcuts to then "Crop to selection" and "Scale image"?**

Having to go to the top menu twice each time is a little slow.

Then again, there might be a better way of doing things in general that I'm missing...

Thanks again for your time, and my Editor thanks you for making me more productive:D

Sincerely,

Alex.

---

### Post by supergrav on 2011-04-20
Try Edit->Keyboard Shortcuts.

---

### Post by BK2FUT on 2011-04-20
Dude... I'm so sorry for wasting your time with such an obviously, easily solved issue.
lol

Man, do I feel like a d00sh.

:confused: - "Duuuuuhh..."

Thanks so much for not calling me an idiot.

Much obliged...

:P:P:P

---

### Post by Zimmer on 2011-04-20
For quick stuff, like crop to aspect ratio and scale have a look at Gthumb image viewer.. I find that great for cropping to screen ratio for backgrounds as it has a drop down list in the cropping tool of common ratios.

---

### Post by BK2FUT on 2011-04-20
Thanks Zimmer!

---

### Post by BK2FUT on 2011-04-21
Is there a way to set a keyboard shortcut in gimp that will automatically size an image down to 200x200?

:confused:

---

### Post by SeijiSensei on 2011-04-21
> **BK2FUT said:**
> Is there a way to set a keyboard shortcut in gimp that will automatically size an image down to 200x200?

It's a lot easier to use [Imagemagick]("http://www.imagemagick.org/script/convert.php") convert for these kinds of tasks. 

```
convert input.png -resize 200x200 output.png
```

That assumes that input.png is already square.  

If you have a bunch of images in a single directory to resize you can use a simple shell script to iterate over all the pictures and resize them. Do a search of this forum for imagemagick, and you'll find sample scripts to do this.

You can install Imagemagick from the repositories.

---

### Post by Zimmer on 2011-04-22
There was a Batch process add on for GIMP, too . I forget how I found it, it may be already installed these days and is normally found in the Filters menu , next to last item, I think.

Also a command line way .. see
[http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/)

I think this is the one I found long ago..
[http://members.ozemail.com.au/~hodsond/dbp.html](http://members.ozemail.com.au/~hodsond/dbp.html)

---

