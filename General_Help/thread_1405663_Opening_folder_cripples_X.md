---
title: "Opening folder cripples X"
date: 2010-02-12
forum: General Help
---

### Post by celem on 2010-02-12
A strange problem has cropped up with gnome on 9.10 amd64. Everything seems fine until I open a folder of JPG images. The window opens, starts filling in the icons and then POOF everything disappears except the desktop background. I have to restart X with CTL-ALT-BACKSPACE. It happens every time. I have used this folder many times in the past without problem. The folder's contents appear ordinary - see below:

the contents of the folder are:
```

ecomer@pennyroyal ~/Documents/history/Research/maps $ ls -A
ConnesteeMap.jpg  IMG_3174.JPG  IMG_3177.JPG  IMG_3180.JPG  IMG_3183.JPG  IMG_3186.JPG  IMG_4049.JPG  IMG_4052.JPG  IMG_4055.JPG  IMG_4058.JPG  JeffFry.jpg      pisgah-1892.jpg  pisgah-1905m.JPG
IMG_3172.JPG      IMG_3175.JPG  IMG_3178.JPG  IMG_3181.JPG  IMG_3184.JPG  IMG_4045.JPG  IMG_4050.JPG  IMG_4053.JPG  IMG_4056.JPG  IMG_4059.JPG  map+overlay.psd  pisgah-1905.jp2  sc_trail.gif
IMG_3173.JPG      IMG_3176.JPG  IMG_3179.JPG  IMG_3182.JPG  IMG_3185.JPG  IMG_4048.JPG  IMG_4051.JPG  IMG_4054.JPG  IMG_4057.JPG  IMG_4060.JPG  pisgah-1892.jp2  pisgah-1905.jpg
ecomer@pennyroyal ~/Documents/history/Research/maps $ 

```

Any ideas??

---

### Post by celem on 2010-02-12
I have identified what crashes X. The folder contains two files of type .jp2. They can be read with GIMP and are a valid image type. I had placed them into this folder while working with them in MicroSoft XP and I guess that I never tried to open the folder after switching totally to Linux.

So - there appears to be a bug in gnome - trying to display a file of type jp2 crashes X.

See:
[http://en.wikipedia.org/wiki/JPEG_2000]("http://en.wikipedia.org/wiki/JPEG_2000")

---

### Post by MooPi on 2010-02-12
Through terminal remove the .gif and .psd files and then give it a try. Just a hunch. Forget what I said and get rid of those .jp2 files

---

### Post by celem on 2010-02-12
I am going to delete the .jp2 files, as I can live without them now. However, the files are actually OK and I used them on XP. There are several problems that can view them without issue on both Windows and MacOS. I consider this a bug as Linux should complain, not crash.

See:
[http://www.fileinfo.com/extension/jp2]("http://www.fileinfo.com/extension/jp2")

---

