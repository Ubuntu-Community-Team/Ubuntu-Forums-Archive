---
title: "i am sure i have all gstreamer codecs installed.  Muine wont play anything :("
date: 2006-06-09
forum: General Help
---

### Post by TOPPEL on 2006-06-09
i am sure i have all gstreamer codecs installed.  Muine wont play anything :(

first time i tried to get it to play something.  it failed.  i'm not sure what the problem is but i'm sure i didn't miss a codec on the restricted codec wiki.  

help !

:confused: 

they were mp3s

reinstalled win32codecs

no work

restarted muine too

did apt-get update ; apt-get upgrade.  major upgrades.  Muine still no sound :(

---

### Post by Chris03 on 2006-06-09
For MP3 support you can:

sudo apt-get install gstreamer0.10-fluendo-mp3

It works with Rhythmbox pretty well.

---

### Post by scpike on 2006-06-10
muine uses gstreamer8, make sure you have those plugins installed

---

### Post by TOPPEL on 2006-06-10
hi

thank you

i'm afraid that did not work either.  

i installed all the codecs mentioned.  there was one part where i had 3 codecs or something download stall.  i ctrl-c and apt-get install again.  it said they were installed.  no way of knowing which 3 codecs are bad -- if that is the case.  

any ideas ?

---

### Post by TOPPEL on 2006-06-10
[QUOTE=TOPPEL]hi

thank you

i'm afraid that did not work either.  

i installed all the codecs mentioned.  there was one part where i had 3 codecs or something download stall.  i ctrl-c and apt-get install again.  it said they were installed.  no way of knowing which 3 codecs are bad -- if that is the case.  

any ideas ?[/QUOTE]

could someone please quote all the different gstreamers needed for Muine to work.  everything else does.  also have win32codecs installed so thats not a factor.  thanks

---

### Post by TOPPEL on 2006-06-10
i'm using dapper drake ubuntu

---

### Post by Chris03 on 2006-06-11
You could try:

sudo apt-get install gstreamer0.10-plugins-*

It'll install every gstreamer plugin package. If that doesn't work, then the Muine doesn't use gstreamer for audio playback.

---

### Post by TOPPEL on 2006-06-11
thank you -- you rule :)

---

