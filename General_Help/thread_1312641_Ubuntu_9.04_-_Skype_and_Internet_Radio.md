---
title: "Ubuntu 9.04 - Skype and Internet Radio"
date: 2009-11-03
forum: General Help
---

### Post by kitebari on 2009-11-03
After a re-installation of Ubuntu on the netbook I have a few problems that were solved before. :p

In its previous incarnation I managed to have both Skype working with sound in and out, Audacity saving files as MP3s  and Radio Capital from Rome [http://www.capital.it/capital/player/live/lo](http://www.capital.it/capital/player/live/lo) - great playlist working fine in Firefox.

The Audacity I've solved by installing LAME so that's  cool.

Skype works in ( I can hear perfectly) but not out via the mic. Last time I merely, (after a lot of research ) unticked the adjust levels automatically and it worked fine. Thing is I now have no other choices listed other than 'pulse audio server' for the microphone whixch just issues static. 

With Capital Radio I get a message MMSH plug in reequired, which it then can't find. I did something last time and it worked but I just seem to find on the net that everyone has the same hassles. If I use [www.mediayou.net]("http://www.mediayou.net/") to access the internet radio stations, it does the same thing. 

 I've checked video with You Tube and CNN and that workes fine, the BBC also plays perfectly via its website as does Lst FM. Rythmnbox plays both Last FM and internet radios fine. 

I wondered whether you had any ideas?

---

### Post by ppirilla on 2009-11-03
For skype, I had to install a package that included a full internal sound system to get my microphone working.

---

### Post by kitebari on 2009-11-03
Could you give me a few more details about that please?

---

### Post by kitebari on 2009-11-05
Ok - solved it! For future reference you need to do the following:

Internet Radio - synaptic package manager enable gstreamer and the ubuntu one that enables all codecs and repositories, even non free ones such as Mp3 etc. Install - reboot and works fine. 

Skype - the odd thing that gave me a clue was a friend saying that, if he boosted the sound he could hear me. Opened up sound recorder and tried to record but got error message. From there went to preferences and clicked the mute / unmute for the microphone which unmutes it . Slid the volume sliders from the minimum all the way tpo the top and hey presto, a successful test call fololowed by a real one.

---

