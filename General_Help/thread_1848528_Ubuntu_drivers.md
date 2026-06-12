---
title: "Ubuntu drivers"
date: 2011-09-22
forum: General Help
---

### Post by Netocp-3 on 2011-09-22
Hello I'm Samuel and a few days ago I've been installing ubuntu 10.04 'cause I had known that it was good. And in deed, it was, but I found a very critical problem. My computer has no internet conection and thus when installing I can't get the right drivers and codecs to make my ubuntu plays almost any kind of media I'd like. As for example MP3, DVD, AVI, MP4, etc.
 
So I want to know, how can I do to get ubuntu drivers to play all the above formats without having an internet connection?
 
Sincerely, Me :confused:

---

### Post by zvacet on 2011-09-22
You can try to download that things from another comp using [Keryx.]("http://keryxproject.org/")

---

### Post by plant pot on 2011-09-28
I am not sure I would go so far as you and say ubuntu is 'good'. This stuff should just work, without posting on a forum!

On ubuntu 11.04 at-least, there is a checkbox on the first screen to press when you first install the machine. A checkbox to enable third party stuff like video codecs etc. that have dubious licences. Might be worth grabbing 11.04, having another go and make sure you pressed it.

That will probably solve your problem. If that does not solve it:
Then I suggest you use my following guide for off-line instillation of packages:

"Keryx v1.0 Ubuntu 11.04 mini-guide --it DOES work"
  [http://keryxproject.org/forums/index.php?topic=130&limit=1#p556](http://keryxproject.org/forums/index.php?topic=130&limit=1#p556)

What packages do you need?
To be honest, just getting 'mplayer' would probably be enough.

Me? I'd Download every package whose name starts with 'ffmpeg', 'VLC', 'mplayer', 'quicktime', and 'xine'. Just to be extra sorted!



You should then, at a console, be able to type:
  cd   <the-place-where-your-video-file-is>
  mplayer   <your-video-filename-here>

...and have a great chance of success.
On the off-chance that 'mplayer' doesn't play it, I would try running (in this order):
  ffplay <your-video-filename-here>
  vlc <your-video-filename-here>
  xine <your-video-filename-here>


You also want to play an actual DVD disc?
 Playing actual DVD's from mplayer requires some cleverness that is explained at the bottom of the mplayer 'man page', type:
        man mplayer

I think you need to do something along the lines of
 1, insert the DVD in your DVD drive
 2, type what it tells you to in the 'man' page, its something like:
     mplayer dvd://1

Also read:
    man xine
...as that may have support for DVD menus by now.


Hopefully someone more 'Ubuntu' on the list can tell you how to run the named video players from the GUI rather than using the command line (if that is your preference).

I think that should sort you out -Big Style-!
--

---

