---
title: "Buggy rhythmbox"
date: 2006-03-03
forum: General Help
---

### Post by rikard_grankvist on 2006-03-03
Hello.
I've recently fallen in love with the iTunes/rhythmbox model of music management, however rhythmbox doesn't work quite well. I realise it's in beta, but my problem seems to me like one that can be fixed, and not some bug in the program. The main problem is that I can't move around in a song using the slider at the top right section of the main window. When I do, rhythmbox makes some noises and switches to another song. An exclamation sign is added next to the song in the "playing column". Same error appears if I pause a song. It can be properly paused, but when I press play, it gurgles a bit and changes song. To me this seems like an error with the sound server. I think I'm supposed to be using ALSA, but when I have that sink selected I get super-slow-motion playback. With ossink, it plays quite normally (with the occasional click or pop when changing songs), but I have the above mentioned errors.
   Another thing that's been bugging me is the tagging. I read at the rhythmbox website that it was an experimental feature to try at own risk, but I'd like to. I don't understand the configuration instructions however:
"Why will preferences not let me edit my song tag info?

    Some mp3s are not detected properly by GStreamer. Rhythmbox supports id3 tag editing as an experimental feature. This is a feature that will be supported at some point in the future. Use the --enable-tag-writing flag to configure to enable it, at your own risk obviously.
"

What is the "configure" program?
Also, I wondering how experimental it is, has someone tried it? With bad/good results?

Thanks in advance
/Rikard

---

### Post by CompShrink on 2006-03-03
Personally, I would suggest switching to rhythmbox-xine. It is more stable than the default installed rhythmbox-gstreamer, which in breezy is gstreamer 0.8. Gstreamer 0.10 which ships with the next release should be much better.

As for tag editing, configure is a file used in compiling from source. Compiling is a real pain, you`ll have to download the build-essentials package, and a lot of other -dev packages...

---

### Post by megamania on 2006-03-04
[QUOTE=rikard_grankvist]Another thing that's been bugging me is the tagging. I read at the rhythmbox website that it was an experimental feature to try at own risk, but I'd like to.[/QUOTE]
I preferred not to take the risk to corrupt my data, and I recently installed Audio Tag Tool, which works pretty well. It's in Synaptic.

---

### Post by rikard_grankvist on 2006-03-04
Yeah, I feared they meant the "configure" used when compiling. I had hoped it was just a binary tool built into rhythmbox or something. Well, I'll stay away from that then. I've tried easytag, and it's quite ok, but I'll see if audio tag tool is any better. And I'll give xine a try. Thanks for all the help! :)

---

### Post by doclivingston on 2006-03-04
[QUOTE=CompShrink]Personally, I would suggest switching to rhythmbox-xine. It is more stable than the default installed rhythmbox-gstreamer, which in breezy is gstreamer 0.8. Gstreamer 0.10 which ships with the next release should be much better.[/quote]

The xine backend for Rhythmbox hasn't existed since 0.8.8, and hadn't really worked properly since earlier in the 0.8 series.

---

### Post by CompShrink on 2006-03-05
Oh, really? I haven't used rhythmbox since 0.8.6, and very briefly 0.8.8. Worked fine for me in 0.8.8, but anyway sorry that wasn't helpful afterall.

---

### Post by rikard_grankvist on 2006-03-05
Yeah I noticed that. There is no rhythmbox-xine package in Synaptic anymore. Well, I'm just gonna have to wait for the next version then. When can we expect it? What kind of release schedule are the Rhythmbox and Gstreamer teams on?

Thanks for the tip about Audio Tag Tool by the way! It's very good and easy to work. Easier than EasyTag (ironically), but I suspect that EasyTag has more features, however Tag Tool gives me all I need. Also, if someone else is reading this thread and wants to use Audio Tag Tool, I should mention that it is called just "tagtool" in synaptic, if you're having any trouble finding it.

---

