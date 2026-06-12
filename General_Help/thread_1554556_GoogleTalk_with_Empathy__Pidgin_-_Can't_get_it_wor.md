---
title: "GoogleTalk with Empathy / Pidgin - Can't get it working"
date: 2010-08-16
forum: General Help
---

### Post by voltaic on 2010-08-16
Ok, I've searched through every thread I could find in relation to using Google Talk voice / video chat through Empathy or Pidgin, I've done everything that I can think of to get this working, but I still can't seem to get it working.

I know the hardware works, so this isn't the issue.

Here's what I've done so far:

removed existing x264 and FFmpeg isntallations
compiled new x264 and FFmpeg from git / svn repositories
installed telepathy

This doesn't seem to fix the issue; when I try to make a call from empathy or pidgin, it attempts to connect and then instantly disconnects (the program doesn't crash). If I try to receive a call, the program crashes.

I *think* this is an issue with H.264 encoding, but I'm not sure how to fix this.

```
voltaic@tesla-lap:~$ gst-inspect-0.10 | grep 264
h264parse:  h264parse: H264Parse
ffmpeg:  ffdec_h264: FFmpeg H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 decoder
ffmpeg:  ffmux_ipod: FFmpeg iPod H.264 MP4 format muxer
typefindfunctions: video/x-h264: h264, x264, 264
rtp:  rtph264depay: RTP H264 depayloader
rtp:  rtph264pay: RTP H264 payloader

```

I don't know much about codecs and that type of thing in general, but it seems to me like there's no encoder present? I see decoder.. but no encoder, is this my problem? and if so, what do I need to do?

Any help is greatly appreciated, I'm really banging my head on the wall with this one.

---

### Post by voltaic on 2010-08-16
update: I had forgotten to install gstreamer0.10-plugins-ugly-multiverse.

x264enc is now present, but this hasn't resolved the issue; I'm looking back through some bug threads to see if I can resolve it. (I have a bad habit of posting questions on this forum and then figuring it out myself, I think maybe I just need to think out loud...)

EDIT: I was referring to this bug; 

[https://bugs.edge.launchpad.net/ubuntu/+source/gst-plugins-ugly-multiverse0.10/+bug/591172](https://bugs.edge.launchpad.net/ubuntu/+source/gst-plugins-ugly-multiverse0.10/+bug/591172)

but this has been fixed, and the fix is part of the current gstreamer-ugly release, so it shouldn't be a problem. That's me stuck now.

---

### Post by voltaic on 2010-08-17
fixed: needed to add 'Telepathy' to the resource box under account options in empathy.

Recap:
> 
1. Install g-streamer0.10-plugins-ugly-multiverse
2. Install FFmpeg
3. Install Telepathy
4. Add GMail account to empathy with 'Telepathy' in 'Resource' box


Can confirm this is working to have voice/video chat with Google Talk contacts running windows.

---

