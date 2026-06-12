---
title: "Collage maker for Ubuntu"
date: 2010-09-17
forum: General Help
---

### Post by EgoGratis on 2010-09-17
I don't know if the "collage" is the right term. Example:

I have folder and 10 pictures in it. I would like to make one picture out of that 10 pictures. And i would like to make that automatically. One or two clicks or one or two command lines...

Picture should remain original size. Different each other. And they should not overlap.

If drop shadow would be created it would be cool. And if i could add some text to it would be cool too. But i can add text in some graphical program so this isn't a must!

I tried commercial software:

[http://www.shapecollage.com/](http://www.shapecollage.com/)

It is cool. But i didn't manage to make one picture where pictures would not overlap. And free version embeds "program logo" on picture. 

And in the end maybe i am searching for something else. Not "collage" maker. So any suggestion would be appreciated. But please don't say something like do it with GIMP. I could. But it would take very long time. And i am looking for quick solution.

---

### Post by stevepetmonkey on 2010-09-18
Picasa from Google can do what you want.

---

### Post by MooPi on 2010-09-18
Possibly  > fehcould fill that need. Very small light command line options. I use it for desktop background and slideshows. It does have a collage feature that I'm not fully versed on.

---

### Post by nothingspecial on 2010-09-18
There is a collage mode and a montage mode, I don`t know which would fit your needs better. Montage will display each picture in order, collage mode is random and places the pictures all over the place

If you have photos in multiple directories you will need to use the -r option which will search through any directories inside the specified directory

The -o option will save the result to a file

There are loads of options, luckily the feh man page is one of the best written, easily understandable man pages I`ve ever seen

```
feh -m -r /path/to/photos 
feh -c -r /path/to/photos 

man feh
```

---

### Post by MooPi on 2010-09-18
This has given me a fun idea to script feh to a screensaver using collage and multiple folders in rotation.

---

### Post by nothingspecial on 2010-09-18
I have a netbook with a broken keyboard I use as a digital photo frame. It displays photos from my "server".

```
ssh -X ns@192.168.1.6
export DISPLAY=:0.0
sshfs -o idmap=user ns@192.168.1.4:/media/backup/snaps ~/snaps && feh -rzF -D 3 ~/snaps
```

---

### Post by EgoGratis on 2010-09-18
First of all thanks for all your answers. It really helped me a lot. Now the summary of your suggestions.

First i tried feh (from synaptic). It is very cool. And does 99% of what i need. The only problem is i can not set width and height of the thumbnails other than in pixels? So i can't make in collage mode or montage mode thumbnails that would be 100% wide and 100% height? And use different sizes of pictures without scaling or changing aspect.

If i could do that feh would be a winner. It is very easy and useful application. I will use it in the future.

Google Picasa. I must say i am surprised. I installed 3.0 beta from here:

[http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)

2.7 didn't work first time in Lucid Lynx. So i used 3.0 beta version (.deb package). And it works without problems. And basically i can do with nice GUI what i was looking for.

So thank you very much again. You solved my problem. Gave me 2 wonderful suggestion. And i can do collage in matter of few clicks with mouse now.

I will mark this thread as solved. But still it's open to comments. If anybody wishes to comment anything else.

Thank you all for comments and finally for really great software solution!

P.S. Picasa doesn't have the setting to set width and height of thumbnail to 100%!

---

### Post by EgoGratis on 2010-09-18
OK i found better solution! Built in ImageMagick and tool it has montage.

Example of usage. This is just a simple example.

Let say i have four .JPG pictures i want in a row and don't want to be scaled.

cd <to picture folder path>
montage *.jpg -mode Concatenate -tile 4x collage.jpg

More options:

[http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)

---

