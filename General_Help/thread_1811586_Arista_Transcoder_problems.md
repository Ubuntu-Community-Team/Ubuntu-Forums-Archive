---
title: "Arista Transcoder problems"
date: 2011-07-25
forum: General Help
---

### Post by miasmablk on 2011-07-25
I'm having issues transcoding .mp4 ----> .avi (specifically) in 'Arista' any other format works just fine ex: .mp4 ----> .mkv. I'm using the latest "XBMC Xbox" preset mode to try and achieve this yet when ever I run the program 'Arista' merely creates an empty .avi file then freezes, requiring a force quit to close. I've tried other presets and i get the same result. ALSO yes I have both gstreamer-plugins-ugly-(multiverse) & gstreamer-plugins-bad-(multiverse) installed

---

### Post by miasmablk on 2011-07-25
bump

---

### Post by miasmablk on 2011-07-25
bump

---

### Post by sgtGarcia on 2011-07-25
Start Arista from Terminal, run convert & paste here what appears in console.

---

### Post by miasmablk on 2011-07-25
richard@richard-Inspiron-1545:~$ arista-gtk -v
arista.presets [453]: DEBUG Loaded device Android Phone (6 presets)
arista.presets [453]: DEBUG Loaded device Apple iPad (2 presets)
arista.presets [453]: DEBUG Loaded device Computer (4 presets)
arista.presets [453]: DEBUG Loaded device DVD Player (3 presets)
arista.presets [453]: DEBUG Loaded device Sony PSP (2 presets)
arista.presets [453]: DEBUG Loaded device Sony Playstation 3 (2 presets)
arista.presets [453]: DEBUG Loaded device Nokia N Series (4 presets)
arista.presets [453]: DEBUG Loaded device Apple iPhone / iPod (3 presets)
arista.presets [453]: DEBUG Loaded device Web Browser (3 presets)
arista.presets [453]: DEBUG Loaded device XBMC Xbox (1 presets)
arista.queue [185]: DEBUG Found item in queue! Queue is Transcode queue: [Queue entry /home/richard/Videos/The Simpsons Movie (2007).mp4 -> Normal avimux -> /home/richard/Videos/The Simpsons Movie (2007).avi]
arista.discoverer [230]: DEBUG Discovering /home/richard/Videos/The Simpsons Movie (2007).mp4
arista.transcoder [596]: DEBUG uridecodebin uri="file:///home/richard/Videos/The Simpsons Movie \(2007\).mp4" name=dmux avimux name=mux ! queue ! filesink name=sink location="/home/richard/Videos/The Simpsons Movie \(2007\).avi" dmux. ! queue ! ffmpegcolorspace ! videorate !   videoscale ! video/x-raw-yuv, width=\(int\)1280, height=\(int\)534, framerate=\(fraction\)24000/1001, pixel-aspect-ratio=\(fraction\)1/1\; video/x-raw-rgb, width=\(int\)1280, height=\(int\)534, framerate=\(fraction\)24000/1001, pixel-aspect-ratio=\(fraction\)1/1 ! xvidenc pass=quant quantizer=8 max-bframes=0 trellis=true ! tee name=videotee ! queue ! mux. dmux. ! queue ! audioconvert ! audiorate ! audioresample ! audio/x-raw-int, width=\(int\)[ 8, 32 ], depth=\(int\)[ 8, 24 ], rate=\(int\)[ 8000, 96000 ], channels=\(int\)[ 1, 2 ]\; audio/x-raw-float, width=\(int\)[ 8, 32 ], depth=\(int\)[ 8, 24 ], rate=\(int\)[ 8000, 96000 ], channels=\(int\)[ 1, 2 ] ! lame bitrate=128 ! mux.

---

### Post by miasmablk on 2011-07-25
last bump

---

### Post by GWBouge on 2011-07-25
I can't really make any sense out of that error output, nor do I really know much about codecs/encoding, but trying to use Avidemux to encode to an avi with the codecs given with that preset, I get the message:

The number of channels is greater than what the selected audio codec can do.
Either change codec or use the mixer filter to have less channels.

So, from what I'm understanding, you'll have to use something that allows you to downmix the amount of audio channels into something that's supported by the mp3 format (such as Avidemux), or choose another format that the X-Box will still work with (I assume this is for streaming?).

---

### Post by miasmablk on 2011-07-25
yeah, I was planning on using this for streaming..."I'll give 'Avidemux' a try as you've suggested. Somewhat disappointed with 'Arista' however as it has so many positive reviews maybe I'll give it a try some other time.

---

### Post by miasmablk on 2011-07-25
lol ok i feel like a total noob..but I was able to correct my problem by  creating a custom 'preset' utilizing these settings...( I was unaware  that 'Arista' supported this feature)[IMG]http://ubuntuforums.org/album.php?albumid=2382&pictureid=8042[/IMG]
[http://ubuntuforums.org/album.php?albumid=2382&pictureid=8042](http://ubuntuforums.org/album.php?albumid=2382&pictureid=8042) 
[IMG]http://ubuntuforums.org/album.php?albumid=2382&pictureid=8042[/IMG]

---

