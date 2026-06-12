---
title: "Really quick question..."
date: 2010-09-21
forum: General Help
---

### Post by pjrandall on 2010-09-21
I'm trying to use RecordItNow to record some generic tutorials in Chrome, and it records it just fine, but during playback, it's very choppy and not smooth at all. How can I increase the quality, or should I just use a different recorder?

---

### Post by SmokeyThePanda on 2010-09-21
You could try this site: [http://blogcritics.org/scitech/article/make-a-movie-of-your-linux/](http://blogcritics.org/scitech/article/make-a-movie-of-your-linux/)

Or, gtk-recordmydesktop.

---

### Post by uRock on 2010-09-21
I have never used it, but this may help with troubleshooting. What are you system specs?

RAM?
CPU?
Graphics?

---

### Post by Rasa1111 on 2010-09-21
every desktop recording app with a GUI ive ever used was less than pleasing in quality.

But Check this out..
[http://ubuntuforums.org/showthread.php?t=1570467](http://ubuntuforums.org/showthread.php?t=1570467)

 it's the best way to record my desktop that ive used yet. 
Basically flawless quality. 

Just one simple command, 
and a Ctrl C to stop it.
SO easy, and works so well. 

 you'll need ffmpeg installed first.

 ```
sudo apt-get install ffmpeg
```

---

### Post by pjrandall on 2010-09-21
> **uRock said:**
> I have never used it, but this may help with troubleshooting. What are you system specs?

RAM?
CPU?
Graphics?
I've got a 2.5 Ghz dual-core proc, 6 gigs of RAM and an Nvidia GX 260M with 1GB memory.

---

### Post by pjrandall on 2010-09-22
> **Rasa1111 said:**
> every desktop recording app with a GUI ive ever used was less than pleasing in quality.

But Check this out..
[http://ubuntuforums.org/showthread.php?t=1570467](http://ubuntuforums.org/showthread.php?t=1570467)

 it's the best way to record my desktop that ive used yet. 
Basically flawless quality. 

Just one simple command, 
and a Ctrl C to stop it.
SO easy, and works so well. 

 you'll need ffmpeg installed first.

 ```
sudo apt-get install ffmpeg
```
Tried it, and it has really great quality, but took about 3 hours to render. XVidCap is working pretty well. Thanks for the advice.

---

### Post by Rasa1111 on 2010-09-22
3 hours! yikes! lol :lol:

yeah, longest video ive made that way was only 2 minutes long. lol
How long is the vid you made, that took 3 hours?
*for future reference.

 thanks,
and no problem. :)

---

### Post by pjrandall on 2010-09-22
> **Rasa1111 said:**
> 3 hours! yikes! lol :lol:

yeah, longest video ive made that way was only 2 minutes long. lol
How long is the vid you made, that took 3 hours?
*for future reference.

 thanks,
and no problem. :)
About a minute. I have a pretty fast comp, it shouldn't have taken that long...

---

### Post by Rasa1111 on 2010-09-22
> **pjrandall said:**
> About a minute. I have a pretty fast comp, it shouldn't have taken that long...

oh wow, yeah that isnt right. 

Im sure your PC is faster than mine, (just by your comment) lol..
and it only took me about 7 minutes to render a 2 minute video, and upload it to youtube. 
(i think 6 & 1/2 of those minutes were the youtube uploader)lol

 as soon as i hit Ctrl C to stop ffmpeg in the terminal,
I was able to open and watch it in VLC.

---

### Post by pjrandall on 2010-09-22
Hmmm..... I'll give it another shot. But also, it recorded it in the wrong resolution. I have a widescreen monitor, but it only recorded part of my screen.

---

### Post by Rasa1111 on 2010-09-22
> **pjrandall said:**
> Hmmm..... I'll give it another shot. But also, it recorded it in the wrong resolution. I have a widescreen monitor, but it only recorded part of my screen.

ahh, 

 then , when you put the command into the terminal, 
you just change the 1024x768, [below, in bold]
 to whatever your resolution is..


```
ffmpeg -f x11grab -s **1024x768** -r 15 -i :0.0 -s **1024x768** -r 15 -sameq video.avi
```

---

### Post by FakeOutdoorsman on 2010-09-22
This guide will give you a high-quality screencast using FFmpeg:

[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by pjrandall on 2010-09-23
Thanks for all the advice. I think I'm all set!:)

---

