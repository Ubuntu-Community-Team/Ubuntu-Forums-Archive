---
title: "100% CPU (what is Backend?) + video issue"
date: 2010-04-30
forum: General Help
---

### Post by joel.whitney on 2010-04-30
Hi, guys.

I've just installed the Netbook Edition of Lucid on my MacBook, and it works great, with two issues:

First, each time I start, the computer is extraordinarily laggy (pretty much unusable), until I run System Testing for video, and go through the whole process.   Then it seems to work great.

Also, I'm having a 100% CPU issue, which switches between my two CPUs.  There was nothing under "my processes" that showed any kind of heavy use.  But, under "all processes" was something called Backend.  I killed the process and now everything seems to be working just fine.

I didn't find any info on these by searching, but as you can see from my total posts here, I'm a total noob, so I may have just missed something.

Any ideas? Thanks!

---

### Post by joel.whitney on 2010-04-30
An update with other observations:  The Backend issue seems to be connected to the video issues -- it doesn't show up until I run the test which cycles through "detected video modes."
Also, the video issue doesn't seem to go away for good after that workaround... I've had the Netbook Edition menu panel freeze up again and get laggy, until I did the same workaround.  Which then fired up the Backend issue again...

Thoughts?
Thanks!

---

### Post by kill4killin on 2010-04-30
There is currently a known issue with Gnome (I think, it's something to do with graphical). I'll see if I can find the bug report on it so you can see if it seems similar.

It has to do with a memory leak that ramps up the system usage to ridiculously high levels.

I'll put the page up if I find it again...

---

### Post by kill4killin on 2010-04-30
> A major memory leak was introduced into the X.org server which causes the computer to get slower and slower over some hours, and finally becoming totally sluggish.

This does not affect cards using proprietary drivers or not using DRI2 because it is specific to the glx module that the open drivers use. Intel will always be affected since DRI2 is used with and without KMS, ATI uses DRI1 without KMS.

This bug has not been fixed so far. In order to make the Ubuntu 10.04 LTS deadline, the Ubuntu developers reverted 3 patches and posted an update to the "ubuntu-x-swat/x-updates" PPA so users can test it. The deadline is set to Friday - when we'll find out if the fix actually works. If not, the update might only come in an early Stable Release Update.

It was X.org, not Gnome...

[http://www.webupd8.org/2010/04/ubuntu-1004-lts-lucid-lynx-release.html](http://www.webupd8.org/2010/04/ubuntu-1004-lts-lucid-lynx-release.html)

I can't find the actually bug report though, it also was reported back in Beta2 and RC...I'm not sure if they fixed it yet...

---

### Post by no2498 on 2010-04-30
i do not know if you can run 1 of these 2 programs if you can it top or htop to see what is running

open a terminal type, top or htop
it tells you how to install them

after 1 or both are loaded type top (or) htop

see what is running

hope you can use them

---

### Post by joel.whitney on 2010-04-30
Hi guys.
Thanks for your help.

When it's happening, Top shows this:

14963 root      20   0  8188 4444 2096 R  100  0.2   4:49.57 backend 

Htop shows the same thing, though it shows the command as (instead of simply "backend" as above):

/usr/bin/python /usr/share/checkbox/backend /temp/checkboxG6ZPIR/input /temp/checkboxG6ZPIR/outpu

...and then it runs off the right side of the window and disappears.

Does that make any kind of sense?

Also, I'm convinced that it has to do with the video test, because it has happened a couple of times, each time after trying to fix the lagging.  One more thing, it seems the crazy lagging issue mostly seems to affect the UNE main menu.  Other programs seem to run fine on top of it.  Weird?

Thanks again for your help!

---

### Post by Sepero on 2010-05-23
[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

---

### Post by no2498 on 2010-05-23
i have a dell 6400 with 910 on it and it was running hot 
all i did was change the plugin in gstreamer-properties video
and it stoped it

---

