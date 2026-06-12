---
title: "Listening to streaming audio."
date: 2010-10-17
forum: General Help
---

### Post by Owen Thomas on 2010-10-17
Hi there.

I want to use Ubuntu, but I'd like to listen to my favourite audio stream like I do for Windows. I have installed Audacious from the Synaptic Package Manager when I found out that my new Ubuntu installation didn't install an audio device as part of its installation, and then I installed something called 'Xine' as prompted when, after I went to the home-page of my audio source, I discovered that I needed to install some extra 'codecs'.

However, I still cannot get the familiar noise that surrounds me when I'm working within Windows to play on Ubuntu. No noise is produced. What's going on?

Help appreciated,

  Owen.

---

### Post by claracc on 2010-10-17
Ubuntu has default software rhythmbox to listen to music and totem to watch videos.

Surely you haven't got installed the ubuntu restricted extras repositories and w32codecs in order to play restricted formats.

Read this link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) in order to play music and video in ubuntu.

---

### Post by Owen Thomas on 2010-10-17
> Ubuntu has default software rhythmbox to listen to music and totem to  watch videos.Hmmm... what do you mean by 'default'? How does this differ from the software I found in the software manager, and if it is installed by 'default', what could have been wrong when I tried to listen to my streaming audio source? I can listen to it fine when I boot my laptop in Windows. Could something have gone wrong with the install I did through WUBI?

> Surely you haven't got installed the ubuntu restricted extras  repositories and w32codecs in order to play restricted formats.I'd previously assumed sound was a pretty simple medium that didn't require different formats or particular 'w32codecs'... little did I know. :)

> Read this link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)  in order to play music and video in ubuntu.     I can be fairly sure that the audio source ([an Australian public broadcaster]("http://www.abc.net.au/newsradio/audio/streaming.htm")) wouldn't use a proprietary format. I wouldn't know how to check this to be sure, so I've supplied the link in the hope that you may be able to find out and get back to me with what I need to do to be able to listen to it.

In the chance that I might be wrong, I'll reboot my laptop in Ubuntu because the page that appears when I follow the link you have supplied presents another link that installs the 'ubuntu-restricted-extras' package.

Thanks,

  Owen.

---

### Post by claracc on 2010-10-17
> Hmmm... what do you mean by 'default'? How does this differ from the software I found in the software manager, and if it is installed by 'default', what could have been wrong when I tried to listen to my streaming audio source? I can listen to it fine when I boot my laptop in Windows. Could something have gone wrong with the install I did through WUBI?

I mean you go to applications --> sound and video --> and then you will have some apps, between them music player rhythmbox and movies player. You can use rhythmbox to listen to audio streaming, providing the radio's link, if there is any codec problem it will say.

In order to install the restricted extra repositories, you can follow instructions in this link: [http://www.unixmen.com/linux-tutorials/501-enchance-your-ubuntu904-and-910-karmic-koala-repositories-with-midibuntu](http://www.unixmen.com/linux-tutorials/501-enchance-your-ubuntu904-and-910-karmic-koala-repositories-with-midibuntu)

---

### Post by Owen Thomas on 2010-10-17
Okay... I have installed these 'rectricted formats' (the link you supplied in your first message), but still no sound. I notice that the player is coming up with the same 'Xine' logo as it did after I installed Audacious. Should I remove Audacious? Should I remove Audacious and these restricted formats, and reinstall the restricted formats only?

---

### Post by HermanAB on 2010-10-17
Howdy,

Do yourself a favour and try out Streamtuner.

---

### Post by claracc on 2010-10-17
Perhaps it will be something in the configuration of sound.

You go to system --> preferences --> sound and be sure you haven't got silenced the volume, try to listen to the sound effects.

Here, there is a link to troubleshooting sound problems: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

You don't need to uninstall audacious, you can choose either rhythmbox or audacious to listen to audio.

It is always advisable to have the ubuntu restricted extras installed in order to listen to or watching any audio/video

---

### Post by Owen Thomas on 2010-10-17
> **HermanAB said:**
> Howdy,

Do yourself a favour and try out Streamtuner.
Third time lucky perhaps. :D

---

### Post by Owen Thomas on 2010-10-17
> **claracc said:**
> Perhaps it will be something in the configuration of sound.

You go to system --> preferences --> sound and be sure you haven't got silenced the volume, try to listen to the sound effects.
Done. My volume settings appear to be fine.
> Here, there is a link to troubleshooting sound problems: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)Done, to a point. I discovered that I'm in the audio group. I am, however, the only user that uses this laptop, so it would appear that this doesn't really matter(?). Edited /etc/group and removed my login.

I'll reboot and observe...

---

### Post by Owen Thomas on 2010-10-17
Alas Clara. No sound.

Might there be a particular issue with my hardware?
[INDENT]00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01bd
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
[/INDENT]I can't find any mention of 'Intel Corporation N10/ICH 7 Family High Definition' in the AlsaProject's list of supported devices under the category 'Intel' so is my hardware in fact unsupported or have I not looked at the list correctly?

Thanks,

  Owen.

---

### Post by Owen Thomas on 2010-10-17
Well, I believe I am defeated.

All I want to do is listen to a streaming audio source on my laptop when I've booted it in Ubuntu, like I can do for Windows. I'm now following some obscure instructions about 'modules' and 'codecs' and other stuff. It is now 11pm.

If you think you can help me any further, I got to the bit in [these instructions]("https://help.ubuntu.com/community/SoundTroubleshooting") where it said the following:
[INDENT]Now you need to figure out what module is loaded by ALSA on your machine.
[/INDENT]I found that my 'module' is 'snd-hda-intel', and my 'codec' is 'SigmaTel STAC9200'. I can't locate information about STAC9200 from the file found on git.alsa.org as per the instructions, and this could apparently be because it refers me to another document.

Listening to streaming audio shouldn't be this hard. It would be a great idea if someone fixed Ubuntu to make it easier. That someone isn't me.

  Owen.

---

### Post by claracc on 2010-10-17
You can try to do this:

Open your browser, firefox I suposse, and write the radio's link you provide: [http://www.abc.net.au/newsradio/audio/streaming.htm](http://www.abc.net.au/newsradio/audio/streaming.htm), there you can select windows media, xine codec loads and I can listen to the streaming (you also can try with the button in the web, real player).

If you cannot listen to any sound, so you have a sound configuration problem in your computer, and you have to wait for more expertise advice.

If you can listen to this radio from your web browser, I think the problem is rhythmbox or audacious cannot play the streming from the url [http://www.abc.net.au/newsradio/audio/streaming.htm](http://www.abc.net.au/newsradio/audio/streaming.htm) and you have to look for a streaming url ( no html) in order the player can play the radio station.

I hope it can help

---

### Post by oldos2er on 2010-10-17
Owen Thomas, which version of Ubuntu are you using? Did your sound work before you tried listening to streaming audio?

Did you install w32codecs? I noticed the website [http://www.abc.net.au/newsradio/audio/streaming.htm](http://www.abc.net.au/newsradio/audio/streaming.htm) offers Windows media and realplayer formats; I tried Windows media and it worked for me, so I think it's just a matter of having the proper codec installed.

---

### Post by andrew.46 on 2010-10-21
Hi Owen,

Good to see a fellow Australian here :). The actual url for the news stream is:

[http://www.abc.net.au/streaming/newsradio.asx](http://www.abc.net.au/streaming/newsradio.asx)

and this plays with vlc or MPlayer well enough. If you were ever keen on the commandline (which is how I personally play streams) MPlayer does a brilliant job as follows:

```

mplayer -playlist 'http://www.abc.net.au/streaming/newsradio.asx' \
        -cache 2048 -cache-min 80


```

But the gui players should have no trouble with this one, I attach a screenshot of vlc playing the stream...

Andrew

---

