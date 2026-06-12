---
title: "Relatively large filesize when resizing images"
date: 2010-04-24
forum: General Help
---

### Post by paulsp on 2010-04-24
Hi there,

I resize images a lot for use on the internet. I am used to doing this with Fireworks. My regular output is JPG / quality 80. Filesize is very acceptable and image quality as well. However, when I resize in Ubuntu the file size is always larger, and I can not find a way to bring this down. 

Here a comparison of resizing a random picture from original 2560x1920 size (1.6MB) -

**New filesize: Ubuntu image resizer vs Fireworks**
1024x768: 140.2 KB vs 52.5 KB
640x480: 71.0 KB vs 24.6 KB
400x300: 46.6 KB vs 12.2KB
100x75: 29.2 KB vs 1.8KB

I have tried resizing with the nautilus image converter, with gThumb, and with the "convert" command in the terminal. When converting in the terminal or with gThumb, I indicate quality = 80, just as in Fireworks. In Nautilus I have no way of indicating quality.

OBSERVATION: If I first lower the quality in Fireworks from the original 95 to 80, and then convert with the terminal (using the exact -quality 80 command), then the images DO reduce to a nice size, similar to Fireworks. However, I need to use Fireworks in the first place so this defeats the purpose.

Anybody any idea how to improve compression? Am I doing something wrong?

Regards,
Paul

---

### Post by utnubuuser on 2010-04-24
Try resizing using GIMP.  You'll be able to control the quality as well as the meta-data, which is probably what's causing the large file sizes.

Image-magick also does a good job of resizing from the command-line.

---

### Post by paulsp on 2010-04-24
Thanks for your reply. But what I want to prevent is having to open a relatively heavy program for something as 'simple' as resizing. Do you really think it is the meta data? See from the table that the extra filesize varies between 20KB and 90KB... if it were mainly meta info this difference would be pretty much the same independently from the image dimensions, I think. 

Wouldn't it be possible to somehow configure the other tools to compress better? Regarding imagemick: this is what I already use when typing "convert..." in the command line, or not?

---

