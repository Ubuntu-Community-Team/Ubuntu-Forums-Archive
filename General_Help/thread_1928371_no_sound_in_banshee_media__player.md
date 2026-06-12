---
title: "no sound in banshee media  player"
date: 2012-02-20
forum: General Help
---

### Post by iamhealed on 2012-02-20
hello, id like to ask help with banshee media player. i can play .mov files but with no sound. i tried using vlc player and it played the movie with sound but it cannot read the entire file. i find it weird because banshee can actually play the entire movie with no error...only that it has no sound. 

i dont have any other media in my laptop because i have just fresh installed my OS . so i have not tested any other media files aside from .mov files.

will be happy to hear from you!

im using ubuntu 11.10 ..

---

### Post by maxplanck on 2012-02-20
Hey there,

I saw that you mentioned this was a clean installation.

Ubuntu does not come installed by default with the packages necessary for playback of certain kind of media.  

During installation, you would have had an option to install them however.

If you didn't, they can be installed via the software center.  The package is entitled "Ubuntu Restricted Extras".  Once you do this, playback should function properly.

---

### Post by HavarN on 2012-02-20
Banshee uses a gstreamer backend to play back media files. The actual magic happens in gstreamer.

Gstreamer is plugin based, and you need to install the right codecs. Search for gstreamer0.10 in synaptic. gstreamer0.10-ffmpeg should solve a lot of playback issues.

---

### Post by maxplanck on 2012-02-20
The package I mentioned already contains the GStreamer plugin that would enable mp3 playback for banshee along with other formats he'll likely want to make use of.

---

### Post by Bromden on 2012-02-20
I've a similar problem.
Until yesterday everything was working fine, then I've discovered that Cheese Webcam couldn't work because of a Gstreamer problem.

So i've installed gstreamer0.10-gconf:
"sudo apt-get install gstreamer0.10-gconf"

And now I've Cheese Webcam working, while Banshee doesn't work anymore... :confused: :confused:

In the terminal i get this:
"GStreamer core error: StateChange"

UPDATE:
"envy24control"  outputs this
"No ICE1712 cards found"

---

### Post by arthurzennig on 2012-06-08
Hey guys,
a little bit late for a solution, ok.

Just a question: *did you guys use HDMI cable at any point? Did the problem started after using a HDMI cable?*

If that happend, just check this post:
[http://ubuntuforums.org/showthread.php?t=1851870](http://ubuntuforums.org/showthread.php?t=1851870)

Hoped it helped;

---

