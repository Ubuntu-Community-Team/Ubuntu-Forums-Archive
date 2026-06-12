---
title: "BP Gulf Crisis Live Streaming Problems"
date: 2010-05-30
forum: General Help
---

### Post by jrg3 on 2010-05-30
Like most everyone else, I've been keeping an eye on the crisis in the Gulf. However, I'm unable to play the streaming video on my Lucid box. It's just a black screen.

[http://www.bp.com/liveassets/bp_internet/globalbp/globalbp_uk_english/homepage/STAGING/local_assets/bp_homepage/html/rov_stream.html](http://www.bp.com/liveassets/bp_internet/globalbp/globalbp_uk_english/homepage/STAGING/local_assets/bp_homepage/html/rov_stream.html)

Any ideas on what codec I might be missing, or other issues that might be causing this?

I'm in Chrome 5.0.375.55 beta but it doesn't seem to be working in Firefox either.

---

### Post by davidmohammed on 2010-05-30
works fine here using firefox - I've got mplayer installed - whatever the stream is, on mine, mplayer plugin is used and is displayed correctly.

---

### Post by frostschutz on 2010-05-30
The live stream broke down for me several times today, sometimes producing only a black, sometimes a green image, and I could reproduce this issue on several machines so I doubt it was an issue on my end. ;)

atm it does work fine although there is not much to see

The whole situation sucks :( and stinks :(

The worst part is, it was not the first leak, and it won't be the last. Let's hope it was the worst.

Just seen a report the other day, made by Greenpeace, and they're showing images of oil platforms operated by BP, Shell, and others, all leaking oil constantly during normal operation... since apparently what they get out of the well is a mix of oil, gas and sea water, and apparently the sea water simply goes back into the sea, even if it has a certain (visible) amount of oil in it.

Not sure if it's true but it sure sucks. Let's hope that in another 100 years or so, we won't be needing any of that stuff any more...

---

### Post by jrg3 on 2010-05-31
It's horrible, yes.

The problem I'm having with the video is definitely codec related. I've an XP install in VirtualBox and the steaming video works fine in it. On Chrome even. 

The video is in WMV format but embedded using an ASX playlist. Perhaps a brainfart, but I can't figure out how to scour the ASX for the direct WMV links. I really should be able to play this video in Chrome on Linux... I just don't know how.

Any help would be appreciated.

---

### Post by no2498 on 2010-06-02
just a ? but you do this yet

sudo apt-get install ubuntu-restricted-extras

---

### Post by Fir3chi3f on 2010-06-05
Sad really that it has been going on this long, but I am also having the same problem. If I open the stream with the video player outside of firefox or chrome it simply states ```
Could not write to resource.
```

I have tried installing the mentioned extras and restarted firefox to no avail.

edit: the video player tried is totem.

---

### Post by Fir3chi3f on 2010-06-06
Update tried installing some additional codec and ended up installing "GStreamer fluendo MPEG2 demuxing plugin" from Ubuntu Software Center because of it's mention of streaming media framework. 

Now when attempting to view the stream it asks to search for codec :)
But, after searching it does not find anything. Screen Shot attached.

---

### Post by 23dornot23d on 2010-06-06
I went through most things I know checked for codecs and extras .... unstriped ...
but I could not get this streaming in Ubuntu Lucid .... MMS was missing from what
I can remember ...... 

I will boot into Lucid and have another try ......... ( still no luck and no error messages ... bizarre )

Also just loaded up the Chromium Browser and the same results ...
no video

but it works fine in Linux Mint ....... don't know if this will help anyone work out the
problem at all ........ 

here is the Link with all the cameras ...... [All Cameras]("http://newsusa.myfeedportal.com/i/LIVE-BP-video-Feed-Oil-Leak-Gulf-of-Mexico")

---

### Post by emarkay on 2010-06-06
Yea, all I have been getting is "Waiting for Video".  Even the direct link does not play in FF:

[http://mfile.akamai.com/97892/live/reflector:46566.asx?bkup=54013](http://mfile.akamai.com/97892/live/reflector:46566.asx?bkup=54013)

The VLC plugin does not "autostart" - and neither does Mplayer (there is no FF plug in for Mplayer, correct?). 
I can load and view the files manually in VLC player, however.
[I][B]
EDIT:
[/B][/I][B]I added the following packages and their dependencies via Synaptic and it now works:
FFMPEG, Mplayer (additional files) and Mozplugger.

[/B]
Solved!

---

### Post by drs305 on 2010-06-07
> **emarkay said:**
> EDIT:
[/B][/I][B]I added the following packages and their dependencies via Synaptic and it now works:
FFMPEG, Mplayer (additional files) and Mozplugger.

[/B]
Solved!

Thank you emarkay. Your solution worked for me as well. 

If this works for the OP it would assist others looking for a solution by marking the thread SOLVED via the "Thread Tools" link at the top right of the original post.

---

### Post by Fir3chi3f on 2010-06-09
Thanks emarkay! works like a charm

---

### Post by luigi_mb on 2010-06-09
Note the warning on the BP site:

"Please be aware, this is a live stream and may freeze or be unavailable from time to time."

/luigi

---

### Post by mocha on 2010-06-12
Below is a playlist of 10 live oil gusher cams.  Use smplayer or VLC (my favorites) to view and change streams.  Just copy and paste the following into a file with .pls extension.  Stupid forums won't let me upload a pls file!!

```
[playlist]
File1=mms://a1686.l9789245685.c97892.g.lm.akamaistream.net/D/1686/97892/v0001/reflector:45685
Title1=Skandi Neptune
Length1=-2147483648
NumberOfEntries=10
Version=2
File2=mms://a288.l9789244287.c97892.g.lm.akamaistream.net/D/288/97892/v0001/reflector:44287
Title2=mms://a288.l9789244287.c97892.g.lm.akamaistream.net/D/288/97892/v0001/reflector:44287
Length2=-2147483648
NumberOfEntries=10
Version=2
File3=mms://a839.l9789244838.c97892.g.lm.akamaistream.net/D/839/97892/v0001/reflector:44838
Title3=Oceaneering International III
Length3=-2147483648
NumberOfEntries=10
Version=2
File4=mms://a567.l9789246566.c97892.g.lm.akamaistream.net/D/567/97892/v0001/reflector:46566
Title4=Osprey-230
Length4=-2147483648
NumberOfEntries=10
Version=2
File5=mms://a1031.l9789255030.c97892.g.lm.akamaistream.net/D/1031/97892/v0001/reflector:55030
Title5=Viking Poseidon
Length5=-2147483648
NumberOfEntries=10
Version=2
File6=mms://a1236.l9789237235.c97892.g.lm.akamaistream.net/D/1236/97892/v0001/reflector:37235
Title6=Canyon
Length6=-2147483648
NumberOfEntries=10
Version=2
File7=mms://a459.l9789222458.c97892.g.lm.akamaistream.net/D/459/97892/v0001/reflector:22458
Title7=Oceaneering
Length7=-2147483648
NumberOfEntries=10
Version=2
File8=mms://a1176.l9789247175.c97892.g.lm.akamaistream.net/D/1176/97892/v0001/reflector:47175
Title8=Oceaneering International
Length8=-2147483648
NumberOfEntries=10
Version=2
File9=mms://a1146.l9789221145.c97892.g.lm.akamaistream.net/D/1146/97892/v0001/reflector:21145
Title9=Osprey-230
Length9=-2147483648
NumberOfEntries=10
Version=2
File10=mms://a1524.l9789235523.c97892.g.lm.akamaistream.net/D/1524/97892/v0001/reflector:35523
Title10=Canyon
Length10=-2147483648
NumberOfEntries=10
Version=2
```

---

### Post by RCRedneck on 2010-06-23
Many thanks Emarkay! Your fix worked for me as well

Mike

---

