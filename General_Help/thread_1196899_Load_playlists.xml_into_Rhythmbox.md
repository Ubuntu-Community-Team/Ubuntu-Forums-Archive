---
title: "Load playlists.xml into Rhythmbox"
date: 2009-06-25
forum: General Help
---

### Post by DouglasCaixeta on 2009-06-25
Hi,

I saved my playlist.xml and rhythmbox.xml from the following folder:
~/.gnome2/rhythmbox

And now I format my pc and installed again, but I can't make Rhythmbox load my old playlists.
There are all the information on those files. I can see!
But Rhythmbox do not recognize it.
I also put it into /usr/share/rhythmbox, but still nothing.

Any suggestions? How can I load my playlists?

---

### Post by godspeed_72 on 2009-11-14
Same problem.  Would really love some help.

---

### Post by laman259 on 2010-11-25
Hey! Same problem here! did you guys get a result? HELP!

---

### Post by Rulius on 2012-10-06
Its an old thread, but I guess better late than ever...

I had the same issue and here is how I solved it:

I backed-up the playlist.xml file located in home/.local/share/rhythmbox (remember to have "show hidden files enabled" in order to see .local). In my new install (12.04) I went to the same folder deleted the playlist.xml~ file and replaced playlist.xml with the one I had backed-up.

 ATTENTION: you may have to modify the playlist.xml before copying it, making sure that all the paths are correct. In my case the name of the partition where I store my music was different and I had to change that. You can use gedit to easily do it with the find and replace feature (ctrl+H). 

Hope this works for u2.

:guitar:

---

