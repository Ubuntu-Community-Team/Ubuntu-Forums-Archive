---
title: "w32 codecs help"
date: 2009-09-09
forum: General Help
---

### Post by sports fan Matt on 2009-09-09
When I ran sudo apt-get install w32codecs..im not sure but where are they stored so I can point to them with "windows media audio in FF Preferences??  Im trying to get WMP to play nicely with king.org. None of the Ausio Streams will launch..Any Advice?

---

### Post by sports fan Matt on 2009-09-09
I meant Audio Streams...lol

---

### Post by Vaphell on 2009-09-09
go to synaptic, find it, right-click it, Properties - and there you have the list of the files installed, with full paths

---

### Post by sports fan Matt on 2009-09-09
I assume I want the package "non free codecs"?  And in the prefs of FF, where should it be pointed to?

---

### Post by Vaphell on 2009-09-09
check in about: plugins if there are totem/gstreamer plugins that take care of playing media inside the browser.

you want to listen to the KING FM stream right? If that's the case you can simply paste [http://wm-live.abacast.com/king-kingfm-32](http://wm-live.abacast.com/king-kingfm-32) into your media player or you can make a bookmark of it and it will automatically launch your player to play the stream. Try to click the link above and see if that works.
If you want to change to let's say Evergreens channel, just find the proper, similar looking link on the page and copy it to your media player/bookmark it too.

---

### Post by sports fan Matt on 2009-09-09
Does anyone else notice Mplayer seem to "pop" while streaming radio stations..this one: [http://asx.abacast.com/wrr-wrr101-32.asx](http://asx.abacast.com/wrr-wrr101-32.asx) in particular?

---

### Post by sports fan Matt on 2009-09-09
And Vap, this worked..thank you

---

### Post by mc4man on 2009-09-09
> Does anyone else notice Mplayer seem to "pop" w,,,

Didn't notice that though it seems to sound better if substituting 64 for 32 in both examples 
using the link in post 5 directly in mplayer cli and your's in post 6 thru browser (mplayer plugin.


( still can't figure how Vaphell finds those links, ones like you posted, (ending in .asx) are more obvious

---

### Post by andrew.46 on 2009-09-09
Hi sox fan Matt,

> **sox fan Matt said:**
> Does anyone else notice Mplayer seem to "pop" while streaming radio stations..this one: [http://asx.abacast.com/wrr-wrr101-32.asx](http://asx.abacast.com/wrr-wrr101-32.asx) in particular?

Yes, I can hear a regular 'tapping' noise in the background of that particular stream. I have no idea what that is all about...

Andrew

---

### Post by Vaphell on 2009-09-09
> ( still can't figure how Vaphell finds those links, ones like you posted, (ending in .asx) are more obvious

well, i copied example by rightclicking and copying the url - I assumed they are similar for all channels at king.org, which is not true
some of them are with .asx, some .asf
whatever - point is that if you can find link to the stream, you don't need browser to play that.

---

### Post by mc4man on 2009-09-09
> point is that if you can find link to the stream, you don't need browser to play that. 
Thanks, finally got how to find the url that works in the cli mplayer

> Yes, I can hear a regular 'tapping' noise in the background of that particular stream

Can actually hear that too, though only from the 32 bit stream.
Saw this on other site though it's referring to windows and describes as 'clicking'
> Often when you  hear clicking from our website, it is because you have the sounds in your “start navigation” system enabled.  The clicking comes from our page reloading the “now playing” option on our website. ...?

---

### Post by andrew.46 on 2009-09-09
Hi mc4man,

> **mc4man said:**
> Can actually hear that too, though only from the 32 bit stream. Saw this on other site though it's referring to windows and describes as 'clicking'

Very odd and as you mentioned confined to the 32bit stream. I notice as well that the 'clicking' is intermittent and varies depending on what is being broadcast. Anyway I am happy that this seems to a problem at the broadcast end rather than the receiver end, although this did not stop me wasting a lot of time looking at the MPlayer audio filters in an effort to screen out the noise :).

Andrew

---

