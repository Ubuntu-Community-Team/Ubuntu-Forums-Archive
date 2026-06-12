---
title: "MP3 to M4A = Impossible????"
date: 2011-02-09
forum: General Help
---

### Post by xeare on 2011-02-09
I have been at this for a couple weeks, and yet no matter where i look, i cannot find a way to convert an mp3 file to m4a. and i DO mean mp3 to m4a. i need it for my dsi. so, i was just wondering if anyone can help me at all. please, thank you, etc.:p

---

### Post by Primefalcon on 2011-02-09
easiest way is to open the command and type in

ffmpeg -i "input file.mp3" "output file.m4a"

---

### Post by andrew.46 on 2011-02-09
> **Primefalcon said:**
> ```
ffmpeg -i "input file.mp3" "output file.m4a"
```

By default this will use aac as the audio codec, which has been stripped from the Ubuntu FFmpeg. A quick read of the following page will get around this issue:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by timgood on 2011-02-09
```
sudo apt-get install soundconverter
```

Then in the preferences, choose M4A as the output.


Hope this helps.

---

### Post by xeare on 2011-02-09
> **timgood said:**
> ```
sudo apt-get install soundconverter
```Then in the preferences, choose M4A as the output.


Hope this helps.    Unfortunatly no, there isnt an m4a file type in this program's preferences, just .wav  .ogg  and .flac , whatever that is.     and the ffmpeg tells me that theres "no such file or directory" when i try and do the conversion

---

### Post by timgood on 2011-02-09
Sorry, you need the new version of Sound Converter which is available at GetDeb [here]("http://www.getdeb.net/software/SoundConverter")

Then Robert should be your father's brother.

---

### Post by Primefalcon on 2011-02-09
a graphical frontend for ffmpeg is winff, try that if your not too familiar with the command line

---

### Post by timgood on 2011-02-09
Also, make sure you have installed ubuntu-restricted-extras which provided the relevant codecs.

---

### Post by andrew.46 on 2011-02-10
> **xeare said:**
> [...] the ffmpeg tells me that theres "no such file or directory" when i try and do the conversion

You will have to give the correct path to your input file, or perhaps easier is to change to the location of your file first.

---

### Post by xeare on 2011-02-10
> **timgood said:**
> Sorry, you need the new version of Sound Converter which is available at GetDeb [here]("http://www.getdeb.net/software/SoundConverter")

Then Robert should be your father's brother.
and again, this looks, and acts just the same as the last program. its not giving me an m4a output option.

---

### Post by xeare on 2011-02-10
> **Primefalcon said:**
> a graphical frontend for ffmpeg is winff, try that if your not too familiar with the command line
winff has no m4a output as well, from what ive seen.... huh, this is looking more and more difficult.... (incase you were wondering, ive been through this several other times in several other places.)

---

### Post by andrew.46 on 2011-02-10
> **xeare said:**
>  huh, this is looking more and more difficult....

But FFmpeg will do this quite easily, your only mistake previously was with the path of the input file. To make it easier perhaps first place your media file on the Desktop, then navigate to the file as follows:

```
cd $HOME/Desktop
```

Then you can run the following command, as long as you have updated your version of FFmpeg according to [FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=1117283"):

```
ffmpeg -i my_file.mp3 -ab 126k test.m4a
```

For 'my_file.mp3' you will of course have to give the actual name of *your *file.

---

### Post by timgood on 2011-02-11
> **xeare said:**
> and again, this looks, and acts just the same as the last program. its not giving me an m4a output option.

In that case you do not have the correct codecs installed. [[IMG]http://img253.imageshack.us/img253/5969/preferences002.th.png[/IMG]](http://img253.imageshack.us/i/preferences002.png/)

Uploaded with [ImageShack.us](http://imageshack.us) is a screenshot of my SoundConverter running on Ubuntu 64 bit.

So you are lacking the codec for m4a.

The Sound Converter site says: 

"SoundConverter is the leading audio file converter for the GNOME Desktop. It reads anything GStreamer can read (Ogg Vorbis, AAC, MP3, FLAC, WAV, AVI, MPEG, MOV, M4A, AC3, DTS, ALAC, MPC, Shorten, APE, SID, MOD, XM, S3M, etc...), and writes to WAV, FLAC, MP3, AAC, and Ogg Vorbis files."

Have you got the gstreamer plugins installed? 

Hope this helps.

---

### Post by xeare on 2011-02-18
> **timgood said:**
> In that case you do not have the correct codecs installed. [[IMG]http://img253.imageshack.us/img253/5969/preferences002.th.png[/IMG]]("http://img253.imageshack.us/i/preferences002.png/")

Uploaded with [ImageShack.us]("http://imageshack.us") is a screenshot of my SoundConverter running on Ubuntu 64 bit.

So you are lacking the codec for m4a.

The Sound Converter site says: 

"SoundConverter is the leading audio file converter for the GNOME Desktop. It reads anything GStreamer can read (Ogg Vorbis, AAC, MP3, FLAC, WAV, AVI, MPEG, MOV, M4A, AC3, DTS, ALAC, MPC, Shorten, APE, SID, MOD, XM, S3M, etc...), and writes to WAV, FLAC, MP3, AAC, and Ogg Vorbis files."

Have you got the gstreamer plugins installed? 

Hope this helps. sorry, havnt been able to get on my computer much. anyway. how do i get the m4a codec? ive been on the site but i cannot find a navigation to the download. mind posting a link to it or something?

---

### Post by shantiq on 2011-02-19
---ok xeare   nearly there   ----    soundconverter is your best bet


you need the gstreamers extras mentioned above


go applications/ubuntu software centre


then enter gstreamer    see image attached    the red cross is the one     the two ticks could be useful too for others things



then run your mp3s through soundconverter    it is excellent



good luck

---

