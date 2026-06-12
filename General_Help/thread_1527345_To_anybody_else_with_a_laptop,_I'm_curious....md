---
title: "To anybody else with a laptop, I'm curious..."
date: 2010-07-09
forum: General Help
---

### Post by inameiname on 2010-07-09
Ok so after a year of having no audio when my laptop wakes up from suspend mode, which worked just fine in Jaunty but not in Karmic or Lucid, a random update or something repaired things from the last few days, and I'm posting here and now just to see if anybody else might know what it was that fixed things, as I'd like to learn just what was doing it, or keeping the sound driver or whatever from waking up when the rest of the laptop does to give me sound. 

Basically, I'd like to know in case this ever happens again, which I've learned happened years ago in Hardy or something, then was fixed for a version or two, only to mess up again. I just want to know for next time so I'll be ready.

I'm most wondering if anybody else who has had this issue has suddenly gotten the fix too. That and if it's a fix from the official Ubuntu repos, or a PPA of mine.

Oh, and I also marked as solved all the posts I have done over the past year in regards to this issue, so no, I'm not posting several times as I'm sure it seems from the number of posts I have when I hit post on this one here. Hehe. 

And I've been trying to figure out what PPAs I use might be the reason, and this one is a potential:

deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) lucid main

Of course it could be:

deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) lucid main #WebUpd8
or
deb [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu) lucid main
or
deb [http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu](http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu) lucid main
with their bunch of updates.

---

### Post by inameiname on 2010-07-09
Using the newest Ubuntu Software Center I was able to narrow down what  update it could have been and I copied and pasted the info here. 

It's one of these I believe among this list of all upgrades done in the past few days::

Friday:
gparted
gwibber-service
gwibber

Thursday:
indicator-application
indicator-applet
ubuntu-mono
python-appindicator
indicator-applet-sesson
libappindicator0
libpng12-0
indicator-sound

Wednesday:
libatk1.0-0
libpam0g
libpam-modules
libpam-runtime
app-install-data-partner
girl1.0-atk1.0
libatk1.0-data
autotools-dev

Seems to me it's an upgrade to ubuntu-mono or indicator-sound, but that's just a wild guess.

And using apt-history:

indicator-sound 0.3.5-0ubuntu1 and ubuntu-mono 0.0.19 were installed.

And finally, using apt-policy:

indicator-sound:
  Installed: 0.3.5-0ubuntu1
  Candidate: 0.3.5-0ubuntu1
  Version table:
 *** 0.3.5-0ubuntu1 0
        500 [http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/](http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     0.2.3-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     0.2.2-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages

ubuntu-mono:
  Installed: 0.0.19
  Candidate: 0.0.19
  Version table:
 *** 0.0.19 0
        500 [http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/](http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     0.0.18 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages

which tells me it is the guido-iodice/guiodiclucid experimental PPA that has the fix. That is, if it's one of those two. Still unsure about that.

---

### Post by inameiname on 2011-06-18
I was never able to narrow down the culprit for the problem, nor the solution to it. Ah well. This issue hasn't happened to me in quite a while, so I'm glad, regardless. I'm sure it was something regarding the audio and an update to something about it. No matter. I'll mark this as solved anyway.

---

### Post by dougalkerr on 2011-06-18
Just a note: I seem to remember this a while back too. I am sure it was a sound preference setting that had the default changed to off. Anyways like you say it did change back to on as default.
There was a time when using Skype that I and others could not get the microphone to work. I found that if you muted one of the stereo channels all would return to normal.
No-one else could explain this either other than a programmer somewhere had decided to go with a new driver and the sound system did not like it.
Fingers crossed that all is well from now.

---

### Post by inameiname on 2011-06-18
Yes...indeed. It was definitely something that was set to off on resume, but unfortunately, it wasn't someting in the sound preference menu or anywhere easy to get to to turn it back on. No biggie now.

---

