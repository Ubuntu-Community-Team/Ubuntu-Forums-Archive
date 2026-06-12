---
title: "How to render a video of the Mandelbrot-Fractal-Set on linux???"
date: 2010-09-23
forum: General Help
---

### Post by Vigh on 2010-09-23
Just wondering if its possible and how to render a video of the Mandelbrot-Fractal-Set on linux??? I've seen some fractal generation programs, but am unsure how I would go about rendering a full video zoom of the Mandelbrot set. Thanks. 

Ant

---

### Post by gzarkadas on 2010-09-25
You can use the _XaoS_ program to make a video of a fractal animation. Steps (assumes step 0-install XaoS, is already done):

1. Open the XaoS application (Applications|Graphics|XaoS), select your fractal and rendering options (use the online documentation for learning how to do it; the application is quite easy in its use) and go to your starting viewpoint.

2.  Click menu `File|Record' and start to navigate in your fractal until you are finished; then click menu `File|Record' again to make the X selection mark go away.

3. You now have a *.xaf animation file inside your home folder (or in a dedicated subdirectory if you chose so in #1, which I strongly recommend). Go to menu `Misc|Render Animation'. A dialog box opens.

4. Select there your rendering options (width, height, frame rate, etc.) and the name of the sequence of PNG images that will be created. Note, that you do not get a video immediately but first a sequence of thousands of PNG images. I am now at ~14000 images for a few minutes of video and still before halfway! Hence, it is better to do this inside a dedicated directory.

5. Use ffmpeg to convert the sequence of PNG images into a video with the desired format. You will need to install ffmpeg and read the documentation to find the appropriate options. winff is a GUI front-end which I believe is available for GNU/Linux also; you may want to try it.

---

### Post by Vigh on 2010-09-26
thanks

---

### Post by gzarkadas on 2010-09-27
You are welcome :). I had never used seriously xaos before; but now, as a side-effect, I am experimenting with sequences rendered at very low fps to create an animated gnome wallpaper.

---

### Post by Vigh on 2010-09-28
Yeah in the process of making a 15minute mandelbrot zoom, to top it off, additional rendering effects have been applied and I have also put split-second displays of random images of objects in the world- places, animals, people, objects etc. to provide a theme to the set, then right at the end an image of planet earth is displayed! Looking forward to the finished product but having some difficulties with FFMPEG and batch image conversions, but will figure it out eventually

---

### Post by gzarkadas on 2010-09-28
You need to set input format to image2 (you can type `ffmpeg -formats | less' to see available formats; anything in there you can also use as -target) and specify the filename mask, which in this case is just `basename%0Xd.png' where X is the number of digits in the filename.

Have a look also at [http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html); you may find it more convenient to read than the terminal.

I have some time to do it, and this is an untested example, but if I am correct the line below will accept PNGs named as baseXXXXX.png (X is a digit) as input and produce a 25 fps (PAL) dvd video with name myvideo.mpg in the current folder. 

```

ffmpeg -f image2 -i [path-to-images]/[base-name]%05d.png -r 25 -target dvd ./myvideo.mpg

```It may need further tweaking, but the input options will more or less remain the same. 

Note that you can also specify sound files with the -i option to make a more dramatic video animation.

---

### Post by Vigh on 2010-09-30
Well thanks to all the fantastic help from everyone at ubuntu forums, and alot of research, I am now rendering a 9 minute zoom of the newton mandelbrot fractal in 1280x720p high defintion format. So excited. Thanks for everything. 

The final command i used was-
ffmpeg -f image2 -i NEWTONPRIME%04d.png -r 8.928571429 -s 1280x720 /home/user/Desktop/NEWTONPRIME.mkv

to use the frame rate command properly, from experimentation- lower is better, for example 
25 = defualt settings = 25 frames/second 
12.5 = 50 frames/second

and of course the option i used
8.928571429 = 70 frames/second

although I could be wrong, will find out shortly

Regards

---

