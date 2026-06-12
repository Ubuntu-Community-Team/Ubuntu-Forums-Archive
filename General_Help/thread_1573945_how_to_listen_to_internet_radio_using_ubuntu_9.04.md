---
title: "how to listen to internet radio using ubuntu 9.04"
date: 2010-09-13
forum: General Help
---

### Post by xetero on 2010-09-13
Hi guys, Im just a newbie here and I'm just starting to learn ubuntu, so be easy to me.. so my question is how do I play this radio on my Ubuntu..

here's the links:

> [http://90.7loveradio.com/](http://90.7loveradio.com/)
[http://pinoylivetv.blogspot.com/2009/09/907-love-radio-manila.html](http://pinoylivetv.blogspot.com/2009/09/907-love-radio-manila.html)
any help would be much appreciated!:o

---

### Post by ron999 on 2010-09-13
Hi
For the loveradio page you can listen in the browser if you have the plugin
**gecko-mediaplayer** from the Ubuntu repository.

It's also possible to listen to it using VLC media player.
This is the link:-
> mms://mirrors.martin.bitstop.ph/loveradio_manila?MSWMExt=.asf

From the command line:-
```
vlc mms://mirrors.martin.bitstop.ph/loveradio_manila?MSWMExt=.asf
```

---

### Post by xetero on 2010-09-14
> **ron999 said:**
> Hi
For the loveradio page you can listen in the browser if you have the plugin
**gecko-mediaplayer** from the Ubuntu repository.

It's also possible to listen to it using VLC media player.
This is the link:-

From the command line:-
```
vlc mms://mirrors.martin.bitstop.ph/loveradio_manila?MSWMExt=.asf
```

thanks! it worked! haha! by the way, what if I want to play other radio stations online?

---

### Post by perspectoff on 2010-09-14
> **xetero said:**
> thanks! it worked! haha! by the way, what if I want to play other radio stations online?

I personally like Audacious instead of Amarok, Rhythmbox, or VLC to listen to online radio. It is faster, and plays radio streams well.

For example, I listen to Shoutcast radio quite a bit ([http://classic.shoutcast.com](http://classic.shoutcast.com)) which has hundreds if not thousands of online radio stations. The streams come across as .pls, so the first time i play one, I merely associate the .pls filename with Audacious.

However, you could instead associate the .pls filename with VLC (a good choice) or Amarok, or whatever, and then they will always play with that player.

Same thing for .asf streams or .wmv files, or whatever.

---

### Post by xetero on 2010-09-14
> **perspectoff said:**
> I personally like Audacious instead of Amarok, Rhythmbox, or VLC to listen to online radio. It is faster, and plays radio streams well.

For example, I listen to Shoutcast radio quite a bit ([http://classic.shoutcast.com](http://classic.shoutcast.com)) which has hundreds if not thousands of online radio stations. The streams come across as .pls, so the first time i play one, I merely associate the .pls filename with Audacious.

However, you could instead associate the .pls filename with VLC (a good choice) or Amarok, or whatever, and then they will always play with that player.

Same thing for .asf streams or .wmv files, or whatever.

thanks [perspectoff]("http://ubuntuforums.org/member.php?u=257693") for the suggestion, I Think I will go with VLC coz it's much easier and faster. [perspectoff]("http://ubuntuforums.org/member.php?u=257693") can you tell me how do I get the link of the radio station that stream? whenever I click the flash player that is embedded in the site, i cant figure out how I can get that link... I wonder where did ron999 get his ".asf" link..

---

