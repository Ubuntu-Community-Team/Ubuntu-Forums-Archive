---
title: "Create Animated .gif in command line"
date: 2011-03-13
forum: General Help
---

### Post by JCM_Pico on 2011-03-13
hello there,
Usually when I want to transform a couple of figures in a animated .gif file, I simply open Gimp, open al the figures as layers and save it as an animated .gif...

My question is, is there any way that allow me to do this procedure in the command line, or with some sh, bash, script?

---

### Post by SeijiSensei on 2011-03-13
[http://www.lcdf.org/gifsicle/](http://www.lcdf.org/gifsicle/)

---

### Post by kaibob on 2011-03-13
> **JCM_Pico said:**
> hello there,
Usually when I want to transform a couple of figures in a animated .gif file, I simply open Gimp, open al the figures as layers and save it as an animated .gif...

My question is, is there any way that allow me to do this procedure in the command line, or with some sh, bash, script?

The following command will convert all PNG files in the current directory to an animated GIF with the name output.gif. Instead of *.png, you can show the names of the individual files you want included in the animated GIF. Convert is a part of the Imagemagick suite of command-line tools and can be installed by way of synaptic. It's a small install that doesn't take up much disk space.  

```
convert -delay 100 -loop 0 *.png output.gif
```

---

### Post by JCM_Pico on 2011-03-14
thank you =) Problem solved

---

### Post by regnw on 2011-08-17
[gifgear.com]("http://gifgear.com") - free online service to create animated images

---

