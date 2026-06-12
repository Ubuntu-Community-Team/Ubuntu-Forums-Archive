---
title: "Creating flash from jpg to enhance website"
date: 2010-11-11
forum: General Help
---

### Post by darkdesire on 2010-11-11
What   tools are available in order to create flash files from several JPGs?
This would be to enhance a website

Thanks for any advice

---

### Post by coffee412 on 2010-11-11
Iam also interested in this. Hope someone can provide some type of answer!

---

### Post by Elfy on 2010-11-11
test

---

### Post by Elfy on 2010-11-11
ing

---

### Post by lykeion on 2010-11-11
Adobe Flash is the obvious answer, but this is Windows software so you can't use it in Ubuntu. You might be able to run it using wine but that's probably more of a hassle than a working solution.

You might try jpeg2swf in swftools.
```
sudo apt-get install swftools
```
jpeg2swf is a command-line utility. Get usage like this:
```
jpeg2swf --help
```

---

### Post by lykeion on 2010-11-11
There are other tools on the net, googling around I found this: [http://www.flash-here.com/downloads/fhslide.html](http://www.flash-here.com/downloads/fhslide.html) (it will display their logo at top-left)

Does it have to be flash? Other alternatives is to create an animated GIF in GIMP, or maybe use JavaScript. Like this one here: [http://www.leigeber.com/2008/12/javascript-slideshow/](http://www.leigeber.com/2008/12/javascript-slideshow/)

---

