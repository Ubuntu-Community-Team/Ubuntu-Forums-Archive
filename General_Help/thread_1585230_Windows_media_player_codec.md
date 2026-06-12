---
title: "Windows media player codec ?"
date: 2010-09-30
forum: General Help
---

### Post by navets on 2010-09-30
I am using Lucid lynx and trying to play a video files with 300++ megs on it but only shows 21 seconds .. 
and a writing in the screen Codec Error : Use windows media player 

I can play all files and already download the ubuntu restriced format .. But why can't i play this one ? 
Really liked the movie tough .. so it will be a really great help :)
Sometihing i miss ? 

Cause i already had problems before and calling for help but it seems that i can't open it besides in windows .. 

thx .. :)

---

### Post by philinux on 2010-09-30
> **navets said:**
> I am using Lucid lynx and trying to play a video files with 300++ megs on it but only shows 21 seconds .. 
and a writing in the screen Codec Error : Use windows media player 

I can play all files and already download the ubuntu restriced format .. But why can't i play this one ? 
Really liked the movie tough .. so it will be a really great help :)
Sometihing i miss ? 

Cause i already had problems before and calling for help but it seems that i can't open it besides in windows .. 

thx .. :)

Have you tried playing it with VLC?

---

### Post by Mark Phelps on 2010-09-30
+1 for VLC.  I believe it comes complete with its own codecs, so it often works when other media players don't.

Also, I've found it works so well that I use in in Win7 instead of WMP!

---

### Post by Banned. on 2010-09-30
> **navets said:**
> I am using Lucid lynx and trying to play a video files with 300++ megs on it but only shows 21 seconds .. 
and a writing in the screen Codec Error : Use windows media player 

I can play all files and already download the ubuntu restriced format .. But why can't i play this one ? 
Really liked the movie tough .. so it will be a really great help :)
Sometihing i miss ? 

Cause i already had problems before and calling for help but it seems that i can't open it besides in windows .. 

thx .. :)

Sometimes when you have a movie and it is fake, it says that open in windows media player. That message is a video itself, not an error message.

Do you get error from Media Player? Like in a Dialog Box or does it just display it in black screen? If it displays in black screen, then probably that video is fake.

---

### Post by navets on 2010-09-30
I opened it with VLC , Movie player , gnome player ..

It's fake ?? the screen not showing black it's showing the opening video .. and with white writings :

 Codec Error : Use windows media player , And then .. 
Aborting Video , redirecting to microsoft codec download page .

---

### Post by dnguyen1963 on 2010-09-30
> **navets said:**
> I opened it with VLC , Movie player , gnome player ..

It's fake ?? the screen not showing black it's showing the opening video .. and with white writings :

 Codec Error : Use windows media player , And then .. 
Aborting Video , redirecting to microsoft codec download page .

Have you tried smplayer?

---

### Post by SeijiSensei on 2010-09-30
+1 for smplayer

If (when) it crashes, look at the mplayer logs.  Or just trying viewing the video from the command line with mplayer itself (it installs with smplayer).

$mplayer /path/to/my/videofile

will open a window to display the video and write a log on the Terminal.  Usually the log is pretty detailed and will show you what's wrong right away.

---

### Post by marin123 on 2010-09-30
haha :D
i'm sure your video is a fake. i downloaded few videos (couple of gigs in size) and had only 10 sec of video showing me that i should visit a webpage and download codec so i could see the video. (do i have to say that codec is a virus, trojan or something like that)
just in case, open it in wmp, you should see the same message

---

### Post by Banned. on 2010-09-30
> **navets said:**
> I opened it with VLC , Movie player , gnome player ..

It's fake ?? the screen not showing black it's showing the opening video .. and with white writings :

 Codec Error : Use windows media player , And then .. 
Aborting Video , redirecting to microsoft codec download page .

Well, my friend, I can't guarantee that it is fake but there are lots of fake videos around the internet. 

Have a look over here:
```
http://forum.videolan.org/viewtopic.php?f=14&t=64879
```
```
http://in.answers.yahoo.com/question/index?qid=20100926052404AAZoxtl
```

---

### Post by navets on 2010-10-01
I tryed running VLC through the console .. this is the error message .. 

VLC media player 1.0.6 Goldeneye
[0x9417668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x981e8d8] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
QPainter::begin: Paint device returned engine == 0, type: 1

I think it is fake .. but no spyware on linux right ? hehehe thx god i haven't tryed in windows machine .. 

btw thx the people here are really helpfull ..

---

### Post by Banned. on 2010-10-01
> **navets said:**
> I tryed running VLC through the console .. this is the error message .. 

VLC media player 1.0.6 Goldeneye
[0x9417668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x981e8d8] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
QPainter::begin: Paint device returned engine == 0, type: 1

I think it is fake .. but no spyware on linux right ? hehehe thx god i haven't tryed in windows machine .. 

btw thx the people here are really helpfull ..

I would not say that there are no spywares for Linux. There are, but not that many. You should not worry!

---

