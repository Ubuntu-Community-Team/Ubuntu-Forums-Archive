---
title: "Internet Radio without Automatix and RealPlayer"
date: 2006-04-11
forum: General Help
---

### Post by adamkane on 2006-04-11
MediaPlayerConnectivity Firefox Plugin:
[https://addons.mozilla.org/extensions/moreinfo.php?id=446]("https://addons.mozilla.org/extensions/moreinfo.php?id=446")

The mplayer plugin via automatix can't handle many realmedia streams, and also can't be uninstalled easily. 

Also I've been looking for a way to easily play and manage realmedia streams without using RealPlayer, and I don't want to cut and paste streams into another program. 

All you need is firefox with gxine for rtsp and mms streams and your favorite media player for http streams.

This new Firefox extension can even parse .smil and .pl files, so you don't have to rely on RealPlayer anymore!

Be sure to enable these options in the MediaPlayerConnectivity extension to play the most radio streams possible:

firefox -> tools -> mediaplayerconnectivity -> configure

> 
Real Media: /usr/bin/X11/gxine
Activate expert mode.
Activate MPC for application links.
Show a direct URL link icon.
Search media in links ...
  

If you have a stream with no file extension, then press "Play as Playlist" link in the MediaPlayerConnectivity sidebar.

Once in a while MediaPlayerConnectivity may not know what to do with a playlist, and will have to browse to gxine to play a stream:
> 
/usr/bin/X11/gxine
 
I previously recommended using mplayer, but I find gxine is the preferred application for playing streaming radio.

---

### Post by eeried on 2006-04-24
Hello,

I've followed your instructions plus I installed w32codecs (from cypherfunk.org as recommended on this forum) and all kings of gstreamer modules.

BeepMP doesn"t launch. Nothing happens actually.

Only Gxine seems to work although it isn't recognised by MConnectivity and  it takes over (but a lot of buffering interruption on dial-up connection.

What exactly do you mean bu using MPlayer as your engine: as the real play plugin?

I noticed Mplayer installs a RealPlayer9 plugin -- isn't this outdated since RealPlayer10 is out, or is this irrelevant?

In my limited experience only gxine + w2codecs work as a replacement for RealPlayer. 

Oh those blasted proprietray, restricted formats :twisted: 

We'd need a detailed howto on the subject. I can send in my gxine solution if it can help as it is very simple.

cheers

---

### Post by eeried on 2006-04-24
An idea perhaps:

When you install plugins they often lack some permissions, especially the excute for all permission.

I added +x to all plugin directories (win32 and firefox plugins) and I'm going to check if I can listen to RealMedia ram files (streaming).

---

### Post by adamkane on 2006-04-24
Install beep-media-player this way:
```

sudo apt-get install beep-media-player

``` 
Which version of beep-media-player do you have?

There's nothing special about RealMedia v10. v10 refers to the media player, not the media being played. Mplayer is all you need to play most, if not all RealMedia.

MediaPlayerConnectivity works well with the settings I've described. My guess is that there is something wrong with your beep-media-player installation.

Also please describe the stream you were trying to play, and I can try to play it on my computer for comparison.

---

### Post by eeried on 2006-04-24
Many thanks for your reply adamkane.

This is my version of BMP: 
beep-media-player_0.9.7.1+cvs20050803-1ubuntu1_i386.deb

I installed it through APT.

BMP doesn't not play a CD but plays all downloaded files (very good sound BMP has). I can't find any BMP config file.

Looking for left-over realplayer files (after uninstalling the app installed  through a BIN file, I came across this:

```

$ cat /etc/gconf/gconf.xml.defaults/desktop/gnome/thumbnailers/audio\@x-pn-realaudio/%gconf.xml
<?xml version="1.0"?>
<gconf>
        <entry name="command" mtime="1145695781" schema="/schemas/desktop/gnome/thumbnailers/audio@x-pn-realaudio/command"/>
        <entry name="enable" mtime="1145695781" schema="/schemas/desktop/gnome/thumbnailers/audio@x-pn-realaudio/enable"/>
</gconf>

```

Mplayer as an embedded thing works on radio-France which has ram or rm  streaming files. The sound's all right though I don't have access to sound control except from the Gnome top bar, of course. Can't pause either, and such like. So BMP would be an excellent idea.

Can you give more detail about your  MC extension config. What are you settings for players : 
 - Realplayer -> /usr/bin/X11/gmplayer (this is by default)
Did you uncheck the A box (=autoplay)?

---

### Post by dlai on 2006-04-24
I've just recently discovered [Listen]("http://listengnome.free.fr/"), a amaroK equivalent for gnome, it still pretty unstable though, and I think it needs alot of polish, for example taking out that ugly bar in the middle... Anyways this one plays radio from my favourite danish radio station, and it is the first linux music-player I have experienced that does it right!! So I would recommend it for playing netradio outside of mozilla-plugins

---

### Post by eeried on 2006-04-24
Thanks for the suggestion. dlai, I'll have a close look at Listen.

None of the gnome multimedia work for me, apart from Totem (sound at least I don't have a DVD drive).

Does you favorite Danish radio use RealPalyer files like some other radios?

Can you listen to these files?

[http://www.tv-radio.com/ondemand/france_culture/CINGLES/CINGLES20060417.ram](http://www.tv-radio.com/ondemand/france_culture/CINGLES/CINGLES20060417.ram)

or you can go to the page [http://www.tv-radio.com/ondemand/france_culture/CINGLES/](http://www.tv-radio.com/ondemand/france_culture/CINGLES/)

and the click on  the link (or picture) ÉCOUTER

Can you listen to a Live or to a Listen again program on BBC radio 4.

You seem to be saying there's no use of the mozilla plugins when using Listen. No need of w32codecs?

---

### Post by dlai on 2006-04-24
[QUOTE=eeried]Thanks for the suggestion. dlai, I'll have a close look at Listen.

None of the gnome multimedia work for me, apart from Totem (sound at least I don't have a DVD drive).

Does you favorite Danish radio use RealPalyer files like some other radios?

Can you listen to these files?

[http://www.tv-radio.com/ondemand/france_culture/CINGLES/CINGLES20060417.ram](http://www.tv-radio.com/ondemand/france_culture/CINGLES/CINGLES20060417.ram)

or you can go to the page [http://www.tv-radio.com/ondemand/france_culture/CINGLES/](http://www.tv-radio.com/ondemand/france_culture/CINGLES/)

and the click on  the link (or picture) ÉCOUTER

Can you listen to a Live or to a Listen again program on BBC radio 4.

You seem to be saying there's no use of the mozilla plugins when using Listen. No need of w32codecs?[/QUOTE]
I'm not sure about realmedia... have not tried it yet... i will when i get home. But if you install both gstreamer-ugly, gstreamer-ugly-multiverse and gstreamer-bad, gstreamer-bad-multiverse you'll get many of the codecs needed... I think... Anyways it looks like you should have either the realplayer plugin or the helix engine... I know that is possible from amaroK... But i'll definitely try it out when i get home.

---

### Post by adamkane on 2006-04-24
Listen doesn't allow you to click on a link in firefox and have it play automatically.

The whole point of this thread is to avoid listen or amarok.

When I press the link to the french stream, mediaplayerconnecitivity pops up in my firefox sidebar, and I am able to hear it with totem.

I have many streams saved in the amarok radio station manager, but amarok doesn't work for streams, where the stream address changes each day.

Also I use beep-media-player 0.9.7 with breezy. Beep is buggy, if you try to install the latest.

---

### Post by dlai on 2006-04-24
[QUOTE=adamkane]Listen doesn't allow you to click on a link in firefox and have it play automatically.

The whole point of this thread is to avoid listen or amarok.

When I press the link to the french stream, mediaplayerconnecitivity pops up in my firefox sidebar, and I am able to hear it with totem.

I have many streams saved in the amarok radio station manager, but amarok doesn't work for streams, where the stream address changes each day.

Also I use beep-media-player 0.9.7 with breezy. Beep is buggy, if you try to install the latest.[/QUOTE]

I'm sorry must read the thread more carefully next time.

---

### Post by eeried on 2006-04-25
Where can you get the beep-media-player 0.9.7 package for Ubuntu-Breezy? Only the cvs is in the repositories now. :neutral:

---

### Post by adamkane on 2006-04-25
I got a little mixed up, when you mentioned beep-media-player "cvs". I think we both have the same version from the breezy repos. Can you try using mediaplayerconnectivity with xmms? xmms works on my machine.

If xmms doesn't work, then we should see which version of mplayer and ffmpeg, you have installed.

I have a fresh install of breezy on my laptop, so I can try all this along with you, and see if I left out any steps.

Don't bother with bmpx. That's the buggy version of bmp that I was thinking of.

---

### Post by eeried on 2006-04-26
Many thanks for kind offer of help adamkane.

I too made a fresh install of Breezy after installing many gstreamer modules to move to ALSA but on my old computer there was no difference. Nothing worked better or worse.

At the moment no Ubuntu-Gnome apps can read an audio CD but that doesn't matter much. I can install VLC (better sound than MPlayer on my system, actually).

I rather like BMP, the sound is better than XMMS on my system anyway.

Can you use BMP or Xmms on line without the Media Connectivity extension?

---

### Post by adamkane on 2006-04-26
Here are a couple important for getting your music players to play different types of media:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[http://easylinux.info/wiki/Ubuntu#How_to_get_Automatix](http://easylinux.info/wiki/Ubuntu#How_to_get_Automatix)

I'll try to play the french stream on the new breezy install, and see what needs to be done, but not til tomorrow.

---

### Post by eeried on 2006-04-26
Thanks for the couple of links -- I know the first one well, as for the second, I would like not to install such a lot of stuff -- I know  anything can be uninstalled very easily afterwards. I'd rather do without EasyUbuntu either.

A note on the present sate of my Breezy: I haven't changed to ALSA, and have installed no Gstreamer modules.

I have just installed BMP, and am on my way to install w2codecs, and Media Connectivity -- but I'd rather do without yet another extension!

If that doesn"t work I'll install mplayer-586 and  its companion mozplugin.

---

### Post by adamkane on 2006-04-26
Sorry for my previous post. It wasn't very helpful.

So the problem is playing rtsp streams. I don't have any rtsp or mms streams that I listen to, so I had not considered this issue.

You can install gxine or mplayer to play realmedia rtsp or windows mms streams. 

There's no GUI, if you use mplayer, so you have to type:

```

killall mplayer

``` 

to quit mplayer. Also you may need to edit /etc/mplayer/mplayer.conf, if your sound is garbled. You may need to try ao=alsa or ao=oss or ao=esd to fix the sound output.

Add gxine or mplayer as your Real Media player in MediaPlayerConnectivity:

> 
/usr/bin/X11/gxine
 or

> 
/usr/bin/X11/mplayer
 So really all you need to play RealMedia streams is:

mediaplayerconnectivity
gxine

Other than rtsp or mms streams, you can use the mediaplayerconnectivity firefox extension to use your favorite media player to play internet streams:

totem, rhythmbox, amarok, listen, beep-media-player, etc.

---

### Post by eeried on 2006-04-27
Many thanks for your detailed reply adamkane.

> Sorry for my previous post. It wasn't very helpful.

Don't worry! I'm not a total newbie and I installed Mplayer and the w32codecs.

I can now listen to rtsp streams on  BBC 4, and Radio-France without the help of the Firefox extension, Media Connectivity.

Though I installed media Connectivity it confuses me, I must say, and I uninstalled it completely. As far as I know it is useful to launch, say, Mplayer rather than gxine if you have both installed. I'll have a closer look at it later on.

I'm so pleased to be rid of RealPlayer!

Last issue: I played three different rtsp streams: 
- This one is perfect: after the usual buffering, the stream is smooth, it's better than actual radio
[http://www.tv-radio.com/ondemand/france_culture/CINGLES/CINGLES20060424.ram](http://www.tv-radio.com/ondemand/france_culture/CINGLES/CINGLES20060424.ram)

- The following two streams sounded less good:

The BBC stream had frequent tiny interruptions (but not a syllable was lost, only a letter):
[http://www.bbc.co.uk/radio/aod/shows/rpms/radio4/amitoosoft.ram](http://www.bbc.co.uk/radio/aod/shows/rpms/radio4/amitoosoft.ram)

After a good start, the Jazz stream started to hiccup in the same way as the BBC stream:
[http://www.radiofrance.fr/listen.php?pr=rtsp&file=/telenum/jazzprobablement.rm](http://www.radiofrance.fr/listen.php?pr=rtsp&file=/telenum/jazzprobablement.rm) 

I'm on dial-up connexion and when I used RealPlayer to play the same streams, the stream was sometimes interrupted by "congestion" (sic) for a couple of seconds but there were no hiccups.

I was careful not to visit any websites while listening to these streams so as not to slow down the connexion...

Is it just the internet connexion or busy servers or should I try some sound configuration: moving to ALSA ? (At least OSS is quite all right for listening to downloaded files either on BMP or Mplayer).

In the meantime I'll do some config on Mplayer as you suggest; and I'll see how gxine compares.

Note on  BBC4: you don't have to click on the link "Listen with stand-alone player"; the stream takes a little time to come in, and nothing seems to happen at all -- Mplayer doesn't appear in any form. If you click on the "stand-alone player" link and if your Mplayer isn't configured as embed=0 (no embed), the left-hand panel is hidden by the grey embedded Mplayer window. The advantage is you have access to the Mplayer controls (pause can be useful).

---

### Post by adamkane on 2006-04-27
MediaPlayerConnectivity allows you to click on a stream, and just have it play, which is the point of the thread as I mentioned before.

As you mentioned, MPC isn't really necessary, since firefox will send most streams to your favorite player anyway.

There is only one realmedia stream left that I listen to, and that's the only reason I created this thread. I enjoy casting both realmedia and windows media aside whenever possible.

Try publicradiofan.com. It has thousands of streams, so you can probably find your favorite streams in a format that suits you.

---

### Post by eeried on 2006-04-28
> I enjoy casting both realmedia and windows media aside whenever possible.

So do I! But I'd miss some programs dearly! And I don't think MP3 is any good either. Ogg ought to be widespread as there are no obstacles for it to it can be read on any platform and any multimedia software.

Many thanks for the link to Public radio.com. I'm now listening for some jazz on Chicago Public Radio with Beep Media Player. Firefox sent a box asking if I want to open the link with BMP and off we go. The sound's great -- in spite of some interruptions even when there doesn't seem to be any internet activity.

;)

---

