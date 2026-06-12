---
title: "Put multiple avi in a DVD"
date: 2006-03-30
forum: General Help
---

### Post by mschievano on 2006-03-30
Hello,
like the topic title say, how can i put multiple separate avi in a dvd building also a menu?
The goal is to view that avi's on a dvd player.

thanks

---

### Post by mschievano on 2006-03-30
[QUOTE=mschievano]Hello,
like the topic title say, how can i put multiple separate avi in a dvd building also a menu?
The goal is to view that avi's on a dvd player.

thanks[/QUOTE]

noone?

---

### Post by yamagami on 2006-03-30
Hi, 

Try to take a look at this tutorial:

[http://www.linuxjournal.com/article/6953](http://www.linuxjournal.com/article/6953)

it should work just fine under ubuntu, though I haven't tried it myself. 
I'm about to try it myself when I get a spare moment. Please let me know how you got on. 

Good luck,
Harel

---

### Post by mschievano on 2006-05-13
[QUOTE=yamagami]Hi, 

Try to take a look at this tutorial:

[http://www.linuxjournal.com/article/6953](http://www.linuxjournal.com/article/6953)

it should work just fine under ubuntu, though I haven't tried it myself. 
I'm about to try it myself when I get a spare moment. Please let me know how you got on. 

Good luck,
Harel[/QUOTE]

I find also this:

[http://sistemist.wordpress.com/2006/05/13/video-editing-videoavi-to-dvd-transcoder-videotrans/](http://sistemist.wordpress.com/2006/05/13/video-editing-videoavi-to-dvd-transcoder-videotrans/)

It give a set of various commands. From example:

```

movie-to-dvd -m pal -M movie1.avi movie2.avi movie3.avi
dvdauthor -o dvd_directory movie1.vob
dvdauthor -o dvd_directory movie2.vob
dvdauthor -o dvd_directory movie3.vob
dvdauthor -o dvd_directory -T

``` 

that can merge multiple avi in one DVD ;)

---

### Post by Drain on 2006-05-13
[QUOTE=mschievano]Hello,
like the topic title say, how can i put multiple separate avi in a dvd building also a menu?
The goal is to view that avi's on a dvd player.

thanks[/QUOTE]

Take a look into [Tovid]("http://tovid.wikia.com/wiki/Main_Page"), a nifty little GUI application for linux.  I burned a good number of xvid .avi files to DVD with that, that played in my parent's DVD player just fine.  The GUI is straightforward although the install can be tricky. 

There are several [threads ]("http://www.ubuntuforums.org/showthread.php?t=125587") that discuss the installation and operation.  Good luck.

---

