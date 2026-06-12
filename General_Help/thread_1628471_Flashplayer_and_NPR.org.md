---
title: "Flashplayer and NPR.org"
date: 2010-11-22
forum: General Help
---

### Post by Calcipher on 2010-11-22
Time once again for a crazy problem.  I have Ubuntu 10.10x64 running and the latest available Flashplayer found in the archives.  Everything that requires flash usually works, with one recent expection, the NPR.org media player (example: [http://www.npr.org/2010/11/16/131356479/new-mix-paul-simon-the-decemberists-john-vanderslice-and-more](http://www.npr.org/2010/11/16/131356479/new-mix-paul-simon-the-decemberists-john-vanderslice-and-more) and click 'Listen To The Show').  What happens is that the player loads up, starts streaming, and then, usually after a few minutes, stops playing.  When I say stops, I mean the audio just stops playing and the pause button switches back to a play button (as if I had paused the stream).  Clicking play does not resume playback, clicking on the item in the playlist causes the audio to start over and then freeze at some other random point.  

I've tried a few things.  First, I assumed it was something going on with Firefox (after all, I have a few plugins running), so I tried Chromium Daily and Midori; both of these browsers had the same problems.  Because Chromium is pretty much a default install, I decided to use it as my testing grounds (as there are too many moving pieces in my Firefox install).  Next, I purged the flashplay pluggin, disabled the x64 repository, closes out all browsers, and deleted the .adobe/ folder in my home directory.  After reinstalling the standard, non x64, flash pluggin I found that I was still having the problem.  Next, I made a VM in VirtualBox running 10.10x64 and loaded Chromium Daily (and Flash) onto it - no surprises, the NPR Media Player worked...  

Clearly there is something wrong with my install, I have no idea what nor how to test things to find out what it might be.  There are, to my knowledge, no log files created by flashplayer.  I cannot manually run the Media Player swf file to test things, and I really don't want to reload Ubuntu (though my /home/ dir is on a different partition, so it wouldn't be the end of the world).  Any ideas?

---

### Post by lovinglinux on 2010-11-22
Try to delete the ~/.macromedia folder. You will lose game scores if you play flash games, so you may want to back it up.

---

### Post by Calcipher on 2010-11-22
> **lovinglinux said:**
> Try to delete the ~/.macromedia folder. You will lose game scores if you play flash games, so you may want to back it up.Well, guess who feels stupid now?  Me.  Thank you so much for pointing out that flash creates a .macromedia folder on top of the .adobe folder...  On the other hand, it is good to feel stupid when you find that a new solution has worked!  Again, thanks so much.

---

### Post by lovinglinux on 2010-11-23
> **Calcipher said:**
> Well, guess who feels stupid now?  Me.  Thank you so much for pointing out that flash creates a .macromedia folder on top of the .adobe folder...  On the other hand, it is good to feel stupid when you find that a new solution has worked!  Again, thanks so much.

You are welcome. Glad to read that it worked.

---

