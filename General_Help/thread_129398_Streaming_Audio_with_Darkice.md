---
title: "Streaming Audio with Darkice"
date: 2006-02-13
forum: General Help
---

### Post by Stormx on 2006-02-13
Hey all... I'm using a program called darkice to stream media to a shoutcast server, hosted by my friend. Darkice takes input from the soundcard, or jack, or whatever... I get this:

```
barney@ubuntu:~/Desktop$ sudo darkice -c config.cfg
DarkIce 0.15 live audio streamer, http://darkice.sourceforge.net
Copyright (c) 2000-2005, Tyrell Hungary, http://tyrell.hu

Using config file: config.cfg
Using OSS DSP input device: /dev/dsp
Using POSIX real-time scheduling, priority 98
DarkIce: TcpSocket.cpp:283: recv error [104]

```

My config file looks like this:

```
# sample DarkIce configuration file, edit for your needs before using
# see the darkice.cfg man page for details

# this section describes general aspects of the live streaming session
[general]
duration        = 60        # duration of encoding, in seconds. 0 means forever
bufferSecs      = 5         # size of internal slip buffer, in seconds

# this section describes the audio input that will be streamed
[input]
device          = /dev/dsp  # OSS DSP soundcard device for the audio input
sampleRate      = 22050     # sample rate in Hz. try 11025, 22050 or 44100
bitsPerSample   = 16        # bits per sample. try 16
channel         = 2         # channels. 1 = mono, 2 = stereo

# this section describes a streaming connection to a ShoutCast server
# there may be up to 8 of these sections, named [shoutcast-0] ... [shoutcast-7]
# these can be mixed with [icecast-x] and [icecast2-x] sections
[shoutcast-0]
bitrateMode     = vbr       # variable bit rate mode
quality         = 0.5       # encoding quality
server          = 80.195.218.217
                            # host name of the server
port            = 8001      # source port of the ShoutCast server, usually 8001
password        = *****    # source password to the ShoutCast server
name            = Stormy's Test Server!
                            # name of the stream
url             = http://www.google.com
                            # URL related to the stream
genre           = dance indie # genre of the stream
public          = yes       # advertise this stream?
irc             = meeeeh
                            # IRC info related to the stream
aim             = meeh  # AIM info related to the stream
icq             = meh
                            # ICQ info related to the stream

```

Any ideas? I really don't understand what the problem could be!

---

### Post by Stormx on 2006-02-13
Update: I just tried streaming to the server at localhost. Same problem

---

