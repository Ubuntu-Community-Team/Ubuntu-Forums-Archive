---
title: "Sound Problem... gstreamer10 only?"
date: 2006-06-09
forum: General Help
---

### Post by scpike on 2006-06-09
Sound works fine in xmms and muine(compiled for gstreamer8) but when I try to play a playlist in rhythmbox/listen/banshee using gstreamer10, the 1st song plays fine and then it rapidly goes through the rest of the playlist, playing a short bit from some of the songs and just skipping the rest.  a little red circle with a line through it shows up in the left column in rhythmbox next to the name of the songs on the playlist as it goes through.  Any ideas why I'm having this problem?

---

### Post by Stephen_96611 on 2006-06-09
Sounds similar to my situation, although my problem is closer to the one described in [this thread]("http://www.ubuntuforums.org/showthread.php?t=188956"), in that no music usually plays. However, seemingly at random, the first second or so will play.

I wonder if this is only happening to those who upgraded in situ? I know that I did, however more data would certainly help.

On Start of Rhythmbox:
(```
rhythmbox:17340): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

(rhythmbox:17340): Rhythmbox-WARNING **: Unable to load icon media-eject

(rhythmbox:17340): Rhythmbox-WARNING **: Unable to start mDNS browsing

``` 
It will then play the first track fine for both Ogg Vorbis and MP3, then it runs through the playlist. Both types of music file are marked with a red no-entry sign. In the properties window of the track it states "Not Negotiated"
[Example]("http://img.photobucket.com/albums/v83/Mjki3se2/rhythmbox.png")

I think the problem might be related to the critical error output, but there appears to be two different critcal error messages referenced, mine and the one mentioned in the above link.

A few times I have had an "application has unexpectedly quit" error.
During/after the error:
```
** (rhythmbox:17340): CRITICAL **: Resources for ring buffer 0x88c86d0 still acquired

GThread-ERROR **: file gthread-posix.c: line 160 (): error 'Device or resource busy' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
aborting...
``` 

I am going to attempt the possible fix laid out in [this thread]("http://www.ubuntuforums.org/showthread.php?t=173543")


NB: I originally had output similar to Howard P, in that it would have several lines of similar to the following appear:
```
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
``` 
This appears to be fixed after I removed all gstreamer0.8 packages I could find and install pretty much every gstreamer0.10 package. That was the limit of the change though.

---

### Post by Stephen_96611 on 2006-06-09
Apologies for the double post, but the first was big enough, I feel.

Using the fix supplied [here]("http://www.ubuntuforums.org/showthread.php?t=173543") has not solved the problem. Some new and some old error messages though. The first is most common, with the second being almost impossible to replicate after removing the "gstreamer0.10-pitfdll" package.

The first type. Fails as above:
on start
```
(rhythmbox:32149): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
``` on close
```
(rhythmbox:32149): Rhythmbox-WARNING **: Unable to stop mDNS browsing: MDNS service is not running
``` 
The second type. Failed as above, crashed to desktop:
on start
```
(rhythmbox:31933): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running
``` after crash
```
Segmentation Fault
``` 

The third on unexpected termination is:
```
** (rhythmbox:17340): CRITICAL **: Resources for ring buffer 0x88c86d0 still acquired

GThread-ERROR **: file gthread-posix.c: line 160 (): error 'Device or resource busy' during 'pthread_mutex_destroy ((pthread_mutex_t *) mutex)'
 aborting...
``` 
I will attempt to get the MDNS service working.

---

### Post by tenshi-no-shi on 2006-06-11
I had the same problem and seamed to have fix it. First remove all gstreamer packages other then the ones that are shipped with ubuntu (just go into synaptic and mark for complete removal of any gstreamer packages without the ubuntu logo next to them). next reinstall all the gstreamer packages that came with ubuntu. Finally try to play a .ogg and see if it works. I haven't played around with installing the extra gstreamer plugins so I don't know if they will work or not.


Edit: also I don't know if just removing the gstreamer plugins works the same way or not.

EDIT(part2): I installed the gstreamer-0.10-plugins-ugly and gstreamer-0.10-plugins-ugly-multiverse and it didn't seam to cause any problems, it was when I installed the rest of the gstreamer plugins [here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28RestrictedFormats%29") that it crashed for me. So probably one of those plugins is either bad or is conflicting with the other ones.

---

