---
title: "Linux video format?"
date: 2006-02-08
forum: General Help
---

### Post by DavidGX on 2006-02-08
Hey guys. I, until not too long ago used windows and recently switched to ubuntu. Doing great so far but I'm wonder what the "linux video format(s)" is? What video format is native to linux? I know windows has mpg/avi. I'd like to convert my video files into a more linux-friendly format. Also any suggestions on the tools to do this would be fine.

I'm playing the windows formats ok via w32codecs and such but I'd like the videos to be in linuxs usual format.

---

### Post by dickohead on 2006-02-08
To correct you on that, the windows format would be WMV, MPG and AVI are just standard video formats. Linux supports anything you can find support for (powers of logic are amazing!).. .which does sound stupid yes, but it's true, if you want to play AVI files find a player that plays them. If you want to play WMV's then you need the w32 codecs.

OGG which is a popular video/audio format within the Linux community might be considered the Linux video format, although since Linux/Ubuntu is not built by one company, officiality is not something that's prevelant (no standard format).

That's why Linux is so great! You have lots of freedom's beyond that of price and software.

---

### Post by kingsidy on 2006-02-09
you can basically use whatever you like. I would say use whatever gives the best quality. you can basically play anything with the right codec.

---

### Post by niviche on 2006-02-09
The original poster's question is interesting for people who want to release audio or video in patent-free formats. 

[QUOTE=dickohead]OGG which is a popular video/audio format within the Linux community might be considered the Linux video format[/QUOTE]

Ogg (lossy) and FLAC (lossless) would be the formats of choice for audio, but are you sure that ogg is also a video format? I have never seen any .ogg video file.

---

### Post by kingsidy on 2006-02-09
when used as video i think that it is a container just like avi or mkv. it is a contained that encodes audio to ogg i think. I personnaly prefer xvid.

---

### Post by el3ktro on 2006-02-09
[QUOTE=niviche]Ogg (lossy) and FLAC (lossless) would be the formats of choice for audio, but are you sure that ogg is also a video format? I have never seen any .ogg video file.[/QUOTE]

To be precisely, the audio format is not called OGG, it's called Vorbis (OGG Vorbis) and the corresponding video format is called OGG Theora. Theora is not finished yet afaik. But if you'd like to produce completely free (patent- & license-free) video/audio then you should choose OGG Vorbis+Theora. For all other purposes I'd recommend any MPEG flavor. I prefer FFMPEG.

To clear all this up for the original poster:
A video file consists of two streams, a VIDEO stream and an AUDIO stream. Both can be in different formats, for video there's MPEG, DIVX, Quicktime etc., for audio there's WAV, MP3, OGG (Vorbis), AAC etc. The video & the audio stream are put together into a CONTAINER, such a container is AVI for example. So AVI is not a video format or a codec, it's a container - so having an AVI file doesn't tell you anything which codec is actually used. An AVI container can not hold an Theora or Vorbis stream, but it can hold an MPEG stream & an WAV stream for example. The MPG container can hold an MPEG video stream & an MP3 audio stream, whilst only the OGM container can hold an MPEG/DIVX/Theora video stream together with an MP3/Vorbis audio stream. Complex, that is ...


Tom

---

### Post by dickohead on 2006-02-09
Thanks Tom! Good info guys, as for the OGG videos, check slashdot for the current XGL stuff from Novell, they have videos on their site in OGG format.

---

