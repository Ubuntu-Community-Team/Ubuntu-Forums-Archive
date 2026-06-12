---
title: "mp3 playback problems"
date: 2006-06-22
forum: General Help
---

### Post by bob_the_d on 2006-06-22
Hey, I'm new to the whole Ubuntu thing.  I finally overcame the video driver difficulties that Dapper gave me and I'm running fine.  More or less.

The thing is that my audio collection is all MP3 based.  However, for some reason, MP3's won't read in the audio players.  Totem says that I don't have a decoder isntalled to handle MP3 files and I may need to install the necessary plugins.

RhythmBox just flat out says there's no "compatible files" existing in the file tree.

However, I don't think it's a hardware problem because OGG files play fine in Totem and RhythmBox.

I also don't know where to find/install the decoders in Ubuntu.  Couldn't find anything in the forum archives either.

Any help?

---

### Post by jvl on 2006-06-22
Look better next time, please :)   [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bob_the_d on 2006-06-22
I'm not sure where the discrepancy lies, but a lot of the packages that were listed that I had to find were not listed on Synaptic.  Neither was I able to get them through the command line.

> 
Ubuntu 6.06 LTS (Dapper Drake)
Most of the proprietary formats can be played using the two default Ubuntu media players, totem-gstreamer and rhythmbox plus gxine, a media player that uses the xine back-end.
Install the following packages and all should be well:

gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly,
gstreamer0.10-plugins-ugly-multiverse, gstreamer0.10-ffmpeg, gstreamer0.10-pitfdll, 
gstreamer0.10-gl, w32codecs, libxine-main1, libxine-extracodecs, gxine


Not a single "bad" or "ugly" package of gstreamer was listed.  Similar ones that I have found and are installed are:

gstreamer-0.10-alsa
gstreamer-0.10-esd
gstreamer-0.10-gnomevfs
gstreamer-0.10-plugins-base
gstreamer-0.10-plugins-base
gstreamer-0.10-plugins-apps
gstreamer-0.10-plugins-base-dbg
gstreamer-0.10-plugins-good
gstreamer-0.10-plugins-good-dbg
gstreamer0.10-tools
gstreamer0.10-x

I'm not sure if it will be relevant, but I also have 

libgstreamer0.10-0, 
libgstreamer0.10.0-dbg
libgstreamer-plugins-base0.10-0

installed and running.

I have libxine-main1 installed and I also have some other package called libxinerama1 installed, but libxine-extracodecs doesn't seem to exist and neither does gxine.

And in the mp3 section, a lot of packages there don't seem to exist either.  Not sure what's going on.

---

### Post by bob_the_d on 2006-06-22
Okay, so I installed XMMS and it seems to be able to playback my MP3 files.  I thought that it installed some codec or decoder along with it, but other players still can't seem to be able to recognize MP3 files.  My best guess is that XMMS has the codecs built into them, but that still doesn't help me since I need to get my iPod synced up to the library.

---

### Post by bob_the_d on 2006-06-22
Actually, the package manager here is kind of frustrating in general.  It seems that I can't install VLC or Banshee through there either.  Despite multiple updates, VLC, VLC's codecs and Banshee, along with the other codecs I listed in the earlier post, just don't seem to exist.  I'm not sure why it's doing that though.

My DiVX/Xvid files don't play either in Totem.  Which is what I was hoping VLC would fix, but I can't seem ti find it.  And VLC's page just tells me to do sudo apt-get which isn't very helpful.

Actually, I wonder if all these problems stem from me using the AMD64 version instead of the x86 version...

](*,) ](*,)

---

### Post by scxtt on 2006-06-22
what does your sources.list look like?

---

### Post by nix4me on 2006-06-22
You must add universe and multiverse to your sources.  This is well documented on the forums and the wiki.

nix4me

---

### Post by bob_the_d on 2006-06-23
Yeah, that did.  Thanks for the help!

---

