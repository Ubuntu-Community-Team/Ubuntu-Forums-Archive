---
title: "Weather Channel Livestream in browser"
date: 2011-08-27
forum: General Help
---

### Post by rCXer on 2011-08-27
Kinda urgent...

So I'm in the path of a hurricane on the east coast of the US and I'm trying watch the [Weather Channel Livesteam]("http://www.weather.com/tv/tvshows/Livestream") in my browser.  Movie Player loads but I don't get any video in either Firefox 3.6 or Chromium.  What can I do to fix this?

---

### Post by coffee412 on 2011-08-27
Do you have "gstreamer-plugins-bad" installed?

Since the weather channel is owned by MS they demand you use their protocol I guess. The "Microsoft Media Server" or MMS. That is what I get when I load the page with firefox.

coffee

p.s. - Wishing you luck thru the storm.:(

---

### Post by Habitual on 2011-08-27
alternative tracking site for Irene:
[http://www.stormpulse.com/atlantic](http://www.stormpulse.com/atlantic)

---

### Post by rCXer on 2011-08-27
> **coffee412 said:**
> Do you have "gstreamer-plugins-bad" installed?

Since the weather channel is owned by MS they demand you use their protocol I guess. The "Microsoft Media Server" or MMS. That is what I get when I load the page with firefox.

coffee

p.s. - Wishing you luck thru the storm.:(

Yeah I have gstreamer0.10-plugins-bad

---

### Post by AlphaLexman on 2011-08-27
> **Habitual said:**
> alternative tracking site for Irene:
[http://www.stormpulse.com/atlantic](http://www.stormpulse.com/atlantic)
I am a weather junkie, and didn't know about that site... AWESOME.

Thanks.

---

### Post by Frogs Hair on 2011-08-27
It works for me and have Gstreamer Plug-ins installed . I also run moonlight , but I don't know if it is required . Good luck with the storm .

---

### Post by rCXer on 2011-08-27
I just got it to work in VLC! I clicked on the arrow at the lower right of the Movie Player and selected "Copy" to get the url.  I then opened VLC then clicked "Media"->"Open Network Stream", pasted the url, and pressed play.  Thanks everyone for your help.

---

### Post by coffee412 on 2011-08-27
There is a gstreamer plugin for aac, xvid, ect.. that probably should be installed. 

I have Ubuntu running in VB and had the same problem. Then installed the additional plugin. I dont normally watch the weather channel online so its kinda new to me too. But I ran into a write error when running the link. However, The tool menus did show up. Might be something in the VB hanging it up.

---

### Post by Habitual on 2011-08-27
> **AlphaLexman said:**
> I am a weather junkie, ...Thanks.

You're very welcome.

I just put the whole Irene system on my desktop using xplanet. ;)
This screenie taken a few days ago...
[IMG]http://i771.photobucket.com/albums/xx360/E522260/Screenshot.png[/IMG]

Clouds/Storm data updated every 3 hours. the Big Blue Marble turns every minute.

Night time is very soothing to look at.

---

### Post by rCXer on 2011-08-27
> **Habitual said:**
> You're very welcome.

I just put the whole Irene system on my desktop using xplanet. ;)
This screenie taken a few days ago...

Clouds/Storm data updated every 3 hours. the Big Blue Marble turns every minute.

Night time is very soothing to look at.

That's cool!

---

### Post by Habitual on 2011-08-27
This will get you started with xplanet.

[http://www.freebsddiary.org/xplanet.php](http://www.freebsddiary.org/xplanet.php)

---

