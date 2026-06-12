---
title: "Ready to break down and cry - video conversion"
date: 2006-04-14
forum: General Help
---

### Post by jimmygoon on 2006-04-14
So I just bought a Cowon A2.. and I want to watch a Firefox flick ([http://www.firefoxflicks.com/flick/?id=19542](http://www.firefoxflicks.com/flick/?id=19542)) on it.

I have (attempted) to use ffmpeg, transcode, and other tools and can't figure out how to convert it to something the device will play.

It will play xvid, divx(3.11,4,5), wmv9

Please help. please... I'm very angry at this thing right now. If anyone can help I will be unbelievably appreciative. thanks

---

### Post by Third Thoughts on 2006-04-14
[QUOTE=jimmygoon]So I just bought a Cowon A2.. and I want to watch a Firefox flick ([http://www.firefoxflicks.com/flick/?id=19542](http://www.firefoxflicks.com/flick/?id=19542)) on it.

I have (attempted) to use ffmpeg, transcode, and other tools and can't figure out how to convert it to something the device will play.

It will play xvid, divx(3.11,4,5), wmv9
[/QUOTE]

I think mencoder should work. mencoder is the encoder that comes with mplayer. Here's an excerpt from the mplayer man page
>  
mencoder  (MPlayer’s Movie Encoder) is a simple movie encoder, designed to encode MPlayer-playable movies (see above) to other MPlayer-playable formats  (see  below).  It  encodes  to MPEG-4 (DivX/XviD), one of the       libavcodec codecs and PCM/MP3/VBRMP3 audio in 1, 2 or  3 passes. Furthermore  it  has  stream  copying  abilities, a powerful filter system       (crop, expand, flip, postprocess, rotate, scale, noise, rgb/yuv conversion) and more.


I'm currently sorting through the mplayer man page to see if I can figure out the specific command to use, and if I can I'll post up again. In the meantime if you don't already have mplayer you can get it with apt or synaptic. You'll also need the win32 if you don't already have those this thread should help. [http://www.ubuntuforums.org/showthread.php?t=75278&highlight=Win32](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=Win32)

~Andrew S.

---

### Post by jimmygoon on 2006-04-14
[QUOTE=Third Thoughts]I think mencoder should work. mencoder is the encoder that comes with mplayer. Here's an excerpt from the mplayer man page


I'm currently sorting through the mplayer man page to see if I can figure out the specific command to use, and if I can I'll post up again. In the meantime if you don't already have mplayer you can get it with apt or synaptic. You'll also need the win32 if you don't already have those this thread should help. [http://www.ubuntuforums.org/showthread.php?t=75278&highlight=Win32](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=Win32)

~Andrew S.[/QUOTE]

forgot to mention that I tried mencoder already and either couldn't figure out how to work it, or it didn't work. I was trying that thing above and it wouldn't convert correctly at all (even when mencoder wasn't throwing errors)

---

### Post by Third Thoughts on 2006-04-14
Okay I think I found the command.


```
mencoder Wheee\!.mov   -ovc   xvid -xvidencopts pass=1:bitrate=687  -oac pcm -o Wheee\!.mpeg
```


Just to break it down for everyone it goes, mencoder [original movie file] -ovc [video codec to be used] [video codec you used]encopts [whatever options you want to specify for that encoder] -oac [audio code you want to use] -o [file you want to out put to]
 
When I ran that command it out put a 5.8 meg movie file that Ubuntu recognized as a Microsfot Avi. I can't test whether or not it will work on your Cowon since I'm not as fortunate as yourself :), but I'm thinking it should. If not, you can probably tweak around with the command till you get something that works. The mplayer man pages are dense, but with some effort you can get a fair amount out of them.

~Andrew S.

---

### Post by jimmygoon on 2006-04-14
[QUOTE=Third Thoughts]Okay I think I found the command.


```
mencoder Wheee\!.mov   -ovc   xvid -xvidencopts pass=1:bitrate=687  -oac pcm -o Wheee\!.mpeg
```


Just to break it down for everyone it goes, mencoder [original movie file] -ovc [video codec to be used] [video codec you used]encopts [whatever options you want to specify for that encoder] -oac [audio code you want to use] -o [file you want to out put to]
 
When I ran that command it out put a 5.8 meg movie file that Ubuntu recognized as a Microsfot Avi. I can't test whether or not it will work on your Cowon since I'm not as fortunate as yourself :), but I'm thinking it should. If not, you can probably tweak around with the command till you get something that works. The mplayer man pages are dense, but with some effort you can get a fair amount out of them.

~Andrew S.[/QUOTE]


that did not work on the Cowon. it did however help me understand how to use mencoder (a bit more... I think I had all of that before aside from the xvidopts)

thanks a bunch... gonna do some more experimenting and post again

edit: where do you find out what you can use for -oac? (and for that matter -oav).. THANKS!

edit2: if this changes anything I found this for the cowon a2: > 1) Up to 640x480 30 fps for DivX 3.11
2) Up to 720x576 24fps, 720x480 30fps, 800x450 30fps for DivX 4/5/
3) Up to 352x288 24fps, 352x240 30fps for WMV ([http://www.cowonamerica.com/products/cowon/a2/tech_specs.html](http://www.cowonamerica.com/products/cowon/a2/tech_specs.html))

edit3: AHAHA! SUCCESS! OMG! (lol I said omg) ... thank you so much... all I had to do was RENAME to "*.avi" (after the conversion obviously)

THANK YOU SO MUCH!!

---

### Post by Third Thoughts on 2006-04-14
Awesome that you figured it out. Glad I could be of help. In regards to this though. 
[QUOTE=jimmygoon]
edit: where do you find out what you can use for -oac? (and for that matter -oav).. THANKS!
[/QUOTE]

You run the command ```
mencoder -oac (or -ovc) help
```

~Andrew S.

---

### Post by jimmygoon on 2006-04-14
[QUOTE=Third Thoughts]Awesome that you figured it out. Glad I could be of help. In regards to this though. 


You run the command ```
mencoder -oac (or -ovc) help
```

~Andrew S.[/QUOTE]

but the one that you used in the command line worked but wasn't displayed whenever I did the "help" as the codec to use... oh well... its not a big deal. I'm happy :)

---

### Post by jtpratt on 2006-04-25
I personally like ffmpeg better than mencoder as it works faster (for me) with cleaner video.  Read my [Ubuntu Video Conversion Guide]("http://smorgasbord.net/convert_video_linux") if you want another way to do it, and how ffmpeg might've worked for you.  I also have some examples for Tovid if you wanted to burn something to dvd as well.

---

### Post by beerorkid on 2006-05-12
thanks so much third thoughts.  works like a charm.

---

