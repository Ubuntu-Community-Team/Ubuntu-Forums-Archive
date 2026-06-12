---
title: "How do I batch normalise ogg audio files?"
date: 2010-11-26
forum: General Help
---

### Post by Rytron on 2010-11-26
Hi.

I use this command to normalise all my mp3 files:

```
normalize-audio -m -v  *.mp3
```

What command should I use to normalise all ogg files?

The normalize-audio program also contains normalize-mp3 and **normalize-ogg**

Would I use something like below or do I require more flags?

```
normalize-ogg *.ogg
```

---

### Post by lykeion on 2010-11-26
You can use the same parameters: normalize-ogg -m -v *.ogg

But why don't you use replaygain (mp3gain/vorbisgain) instead of normalize-audio? 
Difference is that normalize-audio will re-encode the audio files and you'll lose quality. 
With replaygain you only add a "tag" with normalize levels to the audio file, and don't need to re-encode it.

This page describes how to use mp3gain: [http://embraceubuntu.com/2006/09/11/normalize-the-gain-playback-volume-of-your-mp3s/](http://embraceubuntu.com/2006/09/11/normalize-the-gain-playback-volume-of-your-mp3s/)

For ogg files you can use vorbisgain.

---

### Post by Rytron on 2010-11-26
Cheers lykeion for helping me out in yet another thread. ;)

I did notice that running [COLOR="Indigo"]normalize-ogg -m -v *.ogg[/COLOR] reduced the bps from *192* to *128*.

Is the reduction in quality significant with normalize-audio?

Would this suffice?

```
vorbisgain *.ogg
```

---

### Post by lykeion on 2010-11-26
Glad to be of help as always
You can add a --bitrate BR parameter (where BR is the value, default 128) to the normalize-ogg command.
A great help is to use the *man* command to view available parameters and some examples: ```
man normalize-ogg
man vorbisgain
```
Note that not all audio players support replaygain and some like rhythmbox requires enabling a plugin. And very few hardware mp3 players does support it. 
Otherwise it's preferrable to use replaygain instead of normalizing (and re-encoding) the audio files.

---

