---
title: "Quicktime plug-in for Firefox?"
date: 2009-10-28
forum: General Help
---

### Post by onespeedbiker on 2009-10-28
Hello, I read a lot about playing Quicktime movies and installing mplayer for Monzilla. The problem I have is with Comcast. Comcast saves my phone messages so I can listen to them later. Unfortunately, when I try and listen to the messages through their website, it tells me I need a Quicktime plug-in. Is there such a thing for Linux?

---

### Post by fluffman86 on 2009-10-28
Even if you've installed mplayer and the mozilla-mplayer plugin, firefox is still probably using totem-mozilla to play the quicktime files, and I've never had much luck with that.  Here's what I do in Applications > Accessories > Terminal:

sudo apt-get remove totem-mozilla && sudo apt-get install mozilla-mplayer ubuntu-restricted-extras

First thing I do every time I install Ubuntu. :)

---

### Post by onespeedbiker on 2009-10-28
> **fluffman86 said:**
> Even if you've installed mplayer and the mozilla-mplayer plugin, firefox is still probably using totem-mozilla to play the quicktime files, and I've never had much luck with that.  Here's what I do in Applications > Accessories > Terminal:

sudo apt-get remove totem-mozilla && sudo apt-get install mozilla-mplayer ubuntu-restricted-extras

First thing I do every time I install Ubuntu. :)Well that almost worked. I can listen to the messages now, but I have to right click on the message, click on the "Download" option and then use the "MPlayer (default)" option  to play the *.wav file. I checked the Appication preferences that show *.wav files should be opened with the windows media plug-in, but the "Download" drop down menu only gives the "Movie Player (default)" option.  Any idea whats wrong?

---

