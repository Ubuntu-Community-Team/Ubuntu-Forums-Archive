---
title: "How do I create a video, what app do I need?"
date: 2010-11-05
forum: General Help
---

### Post by Wayne1987 on 2010-11-05
I'm just looking for an app that will allow me to create a simple youtube video with an mp3 and picture.  

What app would I need to do this with?

---

### Post by mr_black on 2010-11-05
You can use PiTiVi. It's in the standard repository. Here's the website [http://www.pitivi.org/]("http://www.pitivi.org/")

Cheers,
       Mark

---

### Post by ron999 on 2010-11-05
Hi
ffmpeg will do the job too.

Use a command like this:-
```
ffmpeg -loop_input -i picture.jpg -i sound.mp3 -shortest -b 1000k -acodec copy movie.mp4
```

:)

---

### Post by Wayne1987 on 2010-11-05
Thanks guys

I'm confused, on this code works?

That software doesn't work at all.

I would really rather just have a program that works as a sideshow and I can Import music video and pictures...

*[***Will this work**_?_*]*
[**PhotoFilmStrip is an application which can create a movie (slideshow) out of photos**. It uses the "Ken Burns" effect for the pictures transitions and you can also add music and captions to your photos. **The movie can be rendered in VCD, SVCD, DVD or FULL-HD.**]("http://www.webupd8.org/2010/08/make-movie-out-of-photos-in-ubuntu.html")


Why in the world does this site [http://sourceforge.net](http://sourceforge.net) LOAD soooo slow then crash all the time ONLY that site does this too me... ughh


(Does this look normal)
[IMG]http://i172.photobucket.com/albums/w29/PunkORama87/Screenshot-3.png[/IMG]

---

### Post by Wayne1987 on 2010-11-05
Bump

---

### Post by ron999 on 2010-11-05
> **Wayne1987 said:**
> I'm just looking for an app that will allow me to create a simple youtube video with an mp3 and picture.  


> **Wayne1987 said:**
> I would really rather just have a program that works as a sideshow and I can Import music video and pictures...



Mission creep.:)

---

### Post by Wayne1987 on 2010-11-05
> **ron999 said:**
> Mission creep.:)

How can I make this where the picture last longer with out making it look horrible?  and/or make it look cooler.  Any ideas?

```
[slideshow settings]
video format=576
background color=0;0;0;
distort images=true
number of slides=1

[slide 1]
filename=/home/wayne/Desktop/re6post.png
angle=0
duration=2
transition_id=-1
speed=4
no_points=1
points=2;0;0;1;
text=RE: 6--JAPANS COVER--LEAKED IMAGE--
anim id=2
anim duration=2
text pos=4
placing=0
font=Sans 12
font color=1;0.91268787670710305;0.91268787670710305;1;

[music]
number=1
music_1=/home/wayne/Music/Anti-Flag/Die For The Government/04 - Rotten Future.mp3
```

---

