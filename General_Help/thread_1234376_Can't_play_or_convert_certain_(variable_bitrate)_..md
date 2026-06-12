---
title: "Can't play or convert certain (variable bitrate?) .wma files"
date: 2009-08-07
forum: General Help
---

### Post by adempewolff on 2009-08-07
I just discovered that I have certain .wma files that neither Rhythmbox or Totem will play despite being able to play other .wma files.

Some investigation revealed that these are all files I ripped off of CDs 7-8 years ago using whatever Windows Media Player was the newest one then (WMP 9 I think) and used either the lossless settings or the variable bitrate settings.  Unfortunately most of these CDS are worse for the wear 8 years later so I can't just re-rip them.

As they appear to not be very lossy formats I would be willing to convert them to ogg vorbis or flac but SoundConverter is also unable to decode the files as well.

Here are the errors from trying to open a file running each program from the terminal.

Rhythmbox:
```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|Windows Media Audio decoder|decoder-audio/x-wma, wmaversion=(int)4, bitrate=(int)900032
```

Totem:
```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: don't know how to handle audio/x-wma, wmaversion=(int)4, bitrate=(int)831816, depth=(int)16, rate=(int)44100, channels=(int)2, block_align=(int)13375, codec_data=(buffer)100003000000000000000000000021000000
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2307): prepare_output (): /GstPlayBin:play

** Message: Missing plugin: gstreamer|0.10|totem|Windows Media Audio decoder|decoder-audio/x-wma, wmaversion=(int)4, bitrate=(int)831816 (Windows Media Audio decoder)
```

SoundConverter (doesn't seem to print the error to the terminal but the same search for codecs windows pops up as for the other programs):
```
SoundConverter 1.4.1
  using Gstreamer version: 0.10.22, Python binding version: 0.10.14
  using gio
  using 2 thread(s)
uri not found: 'file:///usr/bin/%25U'
Queue done in 0s
Queue done in 7s

```

Anyone know either how to make these files play or (preferably) a program capable of converting this type of file to a better format?

I multi-boot with XP and Vista 64 so if anyone knows of a solution that requires booting into windows I can deal with it (but who wants to boot into Windows if they don't have to? :D).

---

### Post by Chronon on 2009-08-07
[http://forums.linuxmint.com/viewtopic.php?f=47&t=25318&start=0&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=47&t=25318&start=0&st=0&sk=t&sd=a)

That claims to do the job for lossless wma.  I'm not sure if it will work for the variable bitrate ones too.

---

### Post by adempewolff on 2009-08-07
I tried that nautilus script method (which you need to install mplayer for to convert .wma files) and went through the dialogues untill it says "conversion completed. goodbye!" but it does not appear to create a new file.  How would I run this script from the terminal so I can see where it is going wrong?

---

### Post by mc4man on 2009-08-08
cd to the dir (folder) with wma's and go 
```
audio-convert filename.wma
```

or to batch
```
 audio-convert *.wma
```

It doesn't autotag .wma's so you'd need to enter the info for each file individually

Edit 
just happened to try the repo .deb "nautilus-script-audio-convert"

For that I copied AudioFileConvert to a bin folder in my path (in my case home/bin, normally /usr/bin
Then as above but using this instead of "audio-convert" from terminal prompt
EX.
```
ConvertAudioFile *.wma
```

If flac's are wanted and tags are not important then this would suffice (does file names with spaces, remove the 2 rename lines if none present
you can add creating a dir. and or  moving files ect.ect.

```
#!/bin/bash
for f in *.wma; do mplayer "$f" -ao pcm:fast:waveheader:file="${f%.wma}.wav"; done
rename 's/ /_/g' *.wav
  flac *.wav
rename 's/_/ /g' *.flac
rm *.wav

```

---

### Post by Mike_IronFist on 2009-08-08
> **adempewolff said:**
> I just discovered that I have certain .wma files that neither Rhythmbox or Totem will play despite being able to play other .wma files.

Some investigation revealed that these are all files I ripped off of CDs 7-8 years ago using whatever Windows Media Player was the newest one then (WMP 9 I think) and used either the lossless settings or the variable bitrate settings.  Unfortunately most of these CDS are worse for the wear 8 years later so I can't just re-rip them.

As they appear to not be very lossy formats I would be willing to convert them to ogg vorbis or flac but SoundConverter is also unable to decode the files as well.

Here are the errors from trying to open a file running each program from the terminal.

Rhythmbox:
```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|Windows Media Audio decoder|decoder-audio/x-wma, wmaversion=(int)4, bitrate=(int)900032
```

Totem:
```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: don't know how to handle audio/x-wma, wmaversion=(int)4, bitrate=(int)831816, depth=(int)16, rate=(int)44100, channels=(int)2, block_align=(int)13375, codec_data=(buffer)100003000000000000000000000021000000
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2307): prepare_output (): /GstPlayBin:play

** Message: Missing plugin: gstreamer|0.10|totem|Windows Media Audio decoder|decoder-audio/x-wma, wmaversion=(int)4, bitrate=(int)831816 (Windows Media Audio decoder)
```

SoundConverter (doesn't seem to print the error to the terminal but the same search for codecs windows pops up as for the other programs):
```
SoundConverter 1.4.1
  using Gstreamer version: 0.10.22, Python binding version: 0.10.14
  using gio
  using 2 thread(s)
uri not found: 'file:///usr/bin/%25U'
Queue done in 0s
Queue done in 7s

```

Anyone know either how to make these files play or (preferably) a program capable of converting this type of file to a better format?

I multi-boot with XP and Vista 64 so if anyone knows of a solution that requires booting into windows I can deal with it (but who wants to boot into Windows if they don't have to? :D).

You could always install Wine and use a media player from Windows to play the files. It's not the best solution but it's the quickest by far. I use Winamp with Wine and I get mixed results, but at least all WMA files play uniformly.

---

