---
title: "Package conflicts, trying to install pidgin"
date: 2010-05-25
forum: General Help
---

### Post by whalogreg on 2010-05-25
Running Ubuntu 10.04 64bit on a Gateway md7818u...

When trying to install Pidgin today, I found that I could not do so in the software center due to to a "Software Dependencies Cannot Be Resolved" error. So I went to Synaptic and attempted there. One package after another kept saying "dependent on (insert package name here) but will not be installed" so I went to manually install these packages, with the same results, leading me to "libdirac-encoder0" which would install but conflicted with many of my installed programs... it said that

electricsheep
gstreamer0.10-ffmpeg
libavcodec52
libavformat52
libdirac0c2a
mencoder
mozilla-plugin-vlc
mplayer
vlc
vlc-plugin-pulse

all had to be removed to install this package, which will allow me to install all of these other packages, which will allow me to install Pidgin. Any help here?

---

### Post by whalogreg on 2010-05-26
bump

---

### Post by spotted zebra on 2010-05-27
try this in a terminal

```
 sudo apt-get install pidgin 
```

---

### Post by whalogreg on 2010-05-27
> **spotted zebra said:**
> try this in a terminal

```
 sudo apt-get install pidgin 
```

I tried that earlier and got this output

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libpurple0 (>= 1:2.7.0) but it is not going to be installed
E: Broken packages

```

---

### Post by spotted zebra on 2010-05-27
have you tried using aptitude yet

```

sudo aptitude install pidgin

```

if that doesn't work try this

```

sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade
sudo apt-get pidgin

``` 

if neither of these works post back and ill try to think of something else.

---

### Post by whalogreg on 2010-05-28
Well, I tried aptitude and it did the trick.. Don't know why I didn't try that. I guess I figured if apt-get didn't work, aptitude wouldn't either... 

Thanks!

---

