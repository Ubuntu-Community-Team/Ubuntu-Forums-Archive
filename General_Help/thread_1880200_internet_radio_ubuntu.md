---
title: "internet radio ubuntu"
date: 2011-11-13
forum: General Help
---

### Post by sssuizaaa on 2011-11-13
Good morning everyone,

I'm using radiotray and clementine to listen to internet radio stations (vlc as well). I use the shoutcast links to configure each radio station in radiotray and clementine and they work. I look for the radio station I want and I get the specific shoutcast url for that station. The problem is that I cannot find most of the stations I want in the shoutcast webpage. I find them in tunein for exemple but somehow the tunein links don't work in radio tray nor  in clementine or vlc. Radio tray and clementine tell me that my GStreamer installation is missing a plug-in. I got no message from vlc. I think I have all the possible plugins installed.
Any ideas on how to solve this either by making radiotray or clementine to accept tunein links or by using a different source for radio stations urls?

Thank you

sssuizaaa

---

### Post by ron999 on 2011-11-13
> **sssuizaaa said:**
> ... I look for the radio station I want and I get the specific shoutcast url for that station. The problem is that I cannot find most of the stations I want in the shoutcast webpage. I find them in tunein for exemple but somehow the tunein links don't work in radio tray nor  in clementine or vlc.

Hi
Please give an example.

---

### Post by sssuizaaa on 2011-11-13
Hi ron999

As an exemple the RAC1 radiostation ([http://rac1.org/](http://rac1.org/)) from Spain, where I live. The shoutcast link would be: [http://yp.shoutcast.com/sbin/tunein-station.pls?id=150379](http://yp.shoutcast.com/sbin/tunein-station.pls?id=150379). That works in radiotray and in clementine. The tunein link for the same station is (I guess) [http://tunein.com/radio/RAC-1-877-s18296/](http://tunein.com/radio/RAC-1-877-s18296/). This one does not work. I have chosen an exemple for a radiostation that is both in shoutcast and in tunein. Why bother with tunein? because I can only find a limited amount of radio stations in shoutcast.

Hope this helps.

sssuizaaa

---

### Post by ron999 on 2011-11-13
OK, I understand.
The tunein links will not play with VLC.:(
Will have to use a better way to find a station's feed, without using tunein.

---

### Post by sssuizaaa on 2011-11-13
yes, that's the thing. So you believe it is not a plugin problem then, don't you?
Does anyone knows a good source for radio feeds that work for ubuntu?
thank you

---

### Post by kensum on 2011-11-13
you can use streamtuner2, as the shoutcast plugin works. It can then be set to use whatever audio program you want to play the station, or you can pull the urls off of it and add them to radiotray. ps; I use version 2 as the one in repo i could not get to work.:)

---

### Post by sssuizaaa on 2011-11-13
yes, I've tried streamtuner2 but I do not think I can play a station that is not in their listings, can't I? If I want to play a local radio station I cannot find it there, I only can find it (as far as I know, there's probably other station's feed sites) in places like tunein but then I cannot use these feed url's into any ubuntu media player. As I said I can use the url's I find in the shoutcast webpage but they have a limited amount of them.

---

### Post by Frogs Hair on 2011-11-13
The first link I was able to open in Rythmbox and the last link I can  listen via Firefox  . Below are my plug-ins .

---

### Post by sssuizaaa on 2011-11-13
Yes, sorry I probably did not explain that enough. I can play these stations from the [www.shoutcast.com](www.shoutcast.com) or from [http://tunein.com/](http://tunein.com/) in any web browser (mozilla, chromium...). What I wanted to do is to have my favorite ones in a media player (like clementine or in radio tray) so this would be easier to handle. And I actually can do this with the shoutcast urls that I find in the shoutcast webpage. I put them in clementine or radiotray and works well. But the range of stations they have is limited. tunein has the ones I want but I cannot make the tunein urls work in any ubuntu media player.

---

### Post by sssuizaaa on 2011-11-14
OK, I finally found what I needed.
The url's here work with radiotray, vlc, streamtuner, etc.
[http://www.mikesradioworld.com/](http://www.mikesradioworld.com/)
Regards,
sssuizaaa

---

