---
title: "Video to iTouch with ubuntu"
date: 2011-06-07
forum: General Help
---

### Post by DRSorensen on 2011-06-07
I'm trying to put some videos on my iPod touch. (2nd gen, 8GB, does not connect to internet -- water damage)

I'm looking for some free software that I can use to put videos on it. Banshee gives me the error that it doesn't work with mp4, and there isn't a converter found. I haven't gotten iTunes to work with WINE. I can't find any other programs that have video support. 

Any help is appreciated.

---

### Post by linuxinstalledfromhdd on 2011-06-07
Have you tried installing gtkpod? 

[http://www.gtkpod.org/wiki/Home](http://www.gtkpod.org/wiki/Home)

---

### Post by super newbie on 2011-06-09
i'm also trying to transfer video to my ipod. i"ve been trying to install gtkpod 2 for the last 2 days. when i try to add the ppa to my software sources, i get a message sayig it can't find the webpage (404).  when i try to compile the code, i get a message saying i'm missing a package called "libanjuta-1.0"  Also i've tried using Amarok, but it won't recognize my ipod.  i've tried using the new Banshee that comes with 11.04, but that gives me an error like "the m4v format is not supported"  the original video was a .avi file and i used Arista Transcoder to convert to .m4v format.  any ideas on an easy way to get video onto a ipod (5th gen 30gb video)

thanks

---

### Post by super newbie on 2011-06-10
@DRSorensen, i found a great solution to my problem, it might work for you too.  i'm using 2 free programs, the first one is "floola" (google it).  it's a super simple app that let's you add/remove music/video to and from your ipod.  dowload the program, unzip the file and all you have to do is double-click the "floola" icon and it's up and running (no compiling code, no adding ppa's, no BS trying to install it, IT JUST WORKS - i wish all programs worked this way).

2nd program i'm using is called "mobile media converter" by a company called Miksoft. (google it)  scroll down to the bottom of the website and hit "download" then on the new page find the "for ubuntu linux" version and save the .deb file.  once downloaded, double click on the .deb file and it "should" install the program.  run the program and "add" the file you want to put on your ipod, then under the "conversion to" tab select "quicktime video" and then hit the convert button.  when it's done, i use "floola" to add the .mov file to my ipod.  works like a charm

not sure if Floola supports ipod touch...if not try using "mobile media converter" to convert your video to a .mov file and try using Banshee

hope that helps (i can't believe in 2011 it took DAYS to get video onto an ipod...it shouldn't be this complicated)

---

