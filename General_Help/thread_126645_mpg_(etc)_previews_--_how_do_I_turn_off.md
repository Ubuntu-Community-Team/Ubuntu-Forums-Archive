---
title: "mpg (etc) previews -- how do I turn off??"
date: 2006-02-07
forum: General Help
---

### Post by ninotob on 2006-02-07
I just stopped some movie downloads from the Internet Archive because of extreme slowdowns to my system.  As far as I can tell, it was due to Nautilus trying to grind out a preview of the films while they DLed to my desktop.  Top reported Nuatilus chewing up more than 75% of my CPU (a not awesome but generally fast enough Athlon XP 2200+).

So anyway, how do I turn off this "feature" without losing it for pictures?  I found the option in Nuatilus preferences to turn off previews based on files size -- but where do I look to turn it off based on file type?

---

### Post by dcstar on 2006-02-07
[QUOTE=ninotob]I just stopped some movie downloads from the Internet Archive because of extreme slowdowns to my system.  As far as I can tell, it was due to Nautilus trying to grind out a preview of the films while they DLed to my desktop.  Top reported Nuatilus chewing up more than 75% of my CPU (a not awesome but generally fast enough Athlon XP 2200+).

So anyway, how do I turn off this "feature" without losing it for pictures?  I found the option in Nuatilus preferences to turn off previews based on files size -- but where do I look to turn it off based on file type?[/QUOTE]
There isn't, you can just make it "Local" or "Off" for the Thumbnails.

---

### Post by ninotob on 2006-02-07
Well that's silly!  It essentially means I can't DL video to my desktop because the cpu will get pegged.  I'm DL'ing the same files right now to a directory that isn't my desktop so Nautilus isn't trying to generate previews -- my system is running just fine now.  However, I typically like to DL files to my desktop and then move things around.  I can understand the filesize restriction but it's of no use *while* a file downloads.

EDIT:  maybe I shouldn't blame Nautilus too much.  First time when Nautilus was hitting 75% usage, I was DL'ing w/ firefox.  I gave up trying to figure out how to redirect a file before restarting a DL in Firefox's download manager so I just copied the links from the manager and I'm using wget.  Anyway, even when I open that folder and Nautilus trys to make previews, CPU usuage for Nautilus isn't over 8%.  Something called "gnome-video-thu" hits 20% from time to time though -- just saw it hit 27%.  Maybe I can just kill that without harming other things (ha!  we shall see!  ;-)

Edit-- that gnome-video-thu just surpassed 50% briefly -- slippery bugger, seems to stop and start -- there one second and gone the next with shifting PIDs.

---

### Post by ninotob on 2006-02-07
OK, I think I solved it.

The offender was:

/usr/bin/gnome-video-thumbnailer

which I renamed to:

/usr/bin/gnome-video-thumbnailer.JUNK

Now, when I open that folder to which the movies are downloading, previews aren't happening.  I have 77% idle in top ... and my picture previews are fine (which would stand to reason given the name of the offending program).

---

