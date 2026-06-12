---
title: "downloading videos of youtube into mp3"
date: 2009-07-03
forum: General Help
---

### Post by sanozuke02 on 2009-07-03
i dont know where should i post this but i wish that someone could help me..


i want to dowload videos coming from youtube but i dont know how using ubuntu,, and how should i convert it into mp3. file..

pls.. help me.. 

thanks ..

godbless..

---

### Post by earthpigg on 2009-07-03
in firefox: tools->addons-> get addons -> search for 'youtube'

that has several addons that will download youtube videos to your computer

:D

---

### Post by synapsys on 2009-07-04
I think you mean mp4 as mp3 is an audio format....

Anyways here's how to download videos:

[http://ubuntuforums.org/showthread.php?t=547848](http://ubuntuforums.org/showthread.php?t=547848)

And here's how to convert them:

[http://ubuntuforums.org/archive/index.php/t-393284.html](http://ubuntuforums.org/archive/index.php/t-393284.html)

---

### Post by frvf on 2009-07-04
theres a addon called youtube 2 mp3 , does all the work.

or u can copy the flv off the cache (tmp) folder,
then convert with winff
or natilus or 
with what ever u choose 
to mp3. format.

---

### Post by Bradj47 on 2009-07-04
This site should help: 
[https://addons.mozilla.org/en-US/firefox/addon/10137](https://addons.mozilla.org/en-US/firefox/addon/10137)

And you can use FFMPEG to convert it to MP3. Open a Terminal (Applications -> Accessories -> Terminal) and type: 
```
sudo apt-get install ffmpeg
```
then type: 
```
man ffmpeg
```
to learn how to use it.

If ffmpeg seems too complicated you can use Sound Converter. In a terminal type: 
```
sudo apt-get install soundconverter
```
then go to Applications -> Sound & Video -> Sound Converter to launch the application.

---

### Post by synapsys on 2009-07-04
Quick question... why would anyone want to make mp3s of youtube videos? Just curious....

---

### Post by Alias1407 on 2009-07-04
Or you could use...

[http://mediaconverter.org]("http://mediaconverter.org")

If you are only doing a few, it's fast, easy and has a great interface.
If uses the Open Source, OpenLaszlo system or something extremely similar.

You can also download a firefox extension made by the same man that made the website.

Check it out...

---

### Post by 7raTEYdCql on 2009-07-04
Audacious can be used to convert video pretty easily.

---

### Post by earthpigg on 2009-07-04
> **synapsys said:**
> Quick question... why would anyone want to make mp3s of youtube videos? Just curious....

apparently, youtube music videos are the new napster ;)

---

