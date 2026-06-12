---
title: "webcam won't work on skype, pidgin, empathy -- freezes computer"
date: 2010-04-18
forum: General Help
---

### Post by phubaba on 2010-04-18
Hello everyone,

My webcam works fine on my ubuntu 9.10 computer. I've run gstreamer-properties and I can see that my camera + audio is working. 

Whenever I initialize a video call (or receive a call) from a windows user on gmail or skype to me(a ubuntu user) on empathy pidgin or skpye,

The following happens:
I can first see the other person and hear them. 
I may or may not be able to talk to them (depends on skype pidgin or empathy)
Then right when my video comes up my whole computer freezes and they only get one screenshot of me and I stay frozen on their computer until I restart my computer. In pidgin/empathy they can still hear me talk. Also my mouse still moves.

I cannot do ctrl+alt+escape or backspace. 

I've installed the following codecs via empathy faq and pidgin faqs:
gstreamer ffmpeg
" nice
" plugins-bad
" plugins-bad-multiverse
" plugins-base
" plugins-base-apps
" plugins-base-good
" ugly, " ulgy-multiverse

I've installed each skype, empathy, and pidgin vid using apt-get

skpye is version 2.1.0.81
pidgin is version 2.6.6
empathy is version 2.28.1.1

My specs:
ibm g41, ubuntu 9.10, logitech stx communicator webcam

$ gst-inspect-0.10 | grep 264 

(gst-inspect-0.10:1936): GLib-WARNING **: g_set_prgname() called multiple times
ffmpeg:  ffmux_ipod: FFmpeg iPod H.264 MP4 format muxer
ffmpeg:  ffdec_h264: FFmpeg H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 decoder
h264parse:  h264parse: H264Parse
x264:  x264enc: x264enc
rtp:  rtph264depay: RTP H264 depayloader
rtp:  rtph264pay: RTP H264 payloader
typefindfunctions: video/x-h264: h264, x264, 264

one thing I notice is that I don't have an x264dec but I can't seem to find how to download it.

Any help would be greatly appreciated. I am new to ubuntu for personal computing, and I really want to get this working.

Thanks,
Rob

ps. I've tried using a different camera same result.

I've also tried using aMSN for some reason the msn user can see me but I cannot see them. This really makes no sense to me. Doesn't crash my computer.

---

### Post by P4man on 2010-04-20
Pretty weird. Perhaps you can narrow it down a bit more?

If you do a regular skype call, but disable video, it works?
Enable video for the other person, does that work? Then enable your webcam and where does it fail?

Also can you test the webcam with "Cheese"?

Right now Im guessing the problem might be somewhere else than you think, eg displaying video overlay, and nothing to do with the webcam or codecs, but Im just purely guessing.

---

### Post by no2498 on 2010-04-20
see if this helps in anyway
open a terminal type smplayer
it tells you how to install it

it loads a lot of new codes like 264

hope this helps

---

