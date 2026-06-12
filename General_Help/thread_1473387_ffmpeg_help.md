---
title: "ffmpeg help"
date: 2010-05-05
forum: General Help
---

### Post by satish_j on 2010-05-05
i cannot convert wav files to mp3..after searching,i came to know this is because ffmpeg is not having mp3 support and the solution is to compile it with mp3 support.My questions are:
1. How can i know whether,for a particular codec,ffmpeg support is there or not??I mean from ffmpeg -help or any other command..
2. Do i need to remove ffmpeg completely before compiling it again with mp3 support??

---

### Post by jennil on 2010-05-05
I think ```
ffmpeg -formats
``` provides a list of available formats. My list has MP3 in it and it also works when I convert wav to mp3. The reason could be that I have installed "kubuntu-restricted-extras" that includes some codecs (if you use ubuntu there is "ubuntu-restricted-extras"). Or it could be some other package I have installed that provedes mp3 support.

regards
jennil

---

### Post by satish_j on 2010-05-05
ffmpeg -formats also shows me mp3 option,but i cannot convert to mp3...iam getting the error as:
_*Unsupported codec for output stream #0.0*_
iam going to try 'ubuntu-restricted-extras' later today to see if my prob gets resolved..
thanxx..

---

### Post by 3rdalbum on 2010-05-05
> **satish_j said:**
> ffmpeg -formats also shows me mp3 option,but i cannot convert to mp3...iam getting the error as:
_*Unsupported codec for output stream #0.0*_
iam going to try 'ubuntu-restricted-extras' later today to see if my prob gets resolved..
thanxx..

There's a couple of things you have to check. First is that you've used the right codec name - currently in FFMPEG, when you're encoding to MP3 you use the codec 'libmp3lame'. Not just 'mp3'.

Unfortunately all codec names are likely to change, the FFMPEG developers LOVE to change the codec names just when we were getting familiar with them!

Secondly, you need the "libav*extra-*" packages. Just search through Synaptic for "libav" and install all packages that have the words "libav" and "extra" in their name. This gives you restricted format support.

Thirdly, you might as well use Lame directly if you're going from WAV to MP3. FFMPEG is more for video files, you'll probably find some better audio options in Lame than you'll find in FFMPEG.

---

### Post by satish_j on 2010-05-05
if iam not wrong,lame is not mp3 encoder,whereas i need to encode an wav file to mp3...
pls correct me if iam wrong...

---

### Post by 3rdalbum on 2010-05-05
> **satish_j said:**
> if iam not wrong,lame is not mp3 encoder,whereas i need to encode an wav file to mp3...
pls correct me if iam wrong...

I know where you got that idea from, but Lame **is** an MP3 encoder. That's all it does!

If you want to use FFMPEG instead, go ahead. It still uses Lame as the backend. If you're a real audio enthusiast, though, you might be more satisfied with using Lame directly.

---

### Post by robert shearer on 2010-05-05
```
apt-get install ubuntu-restricted-extras soundconverter
```

Then open soundconverter from the applications/sound&video menu.

Edit the preferences for output format =mp3 and the bitrate and quality you want.

 Choose the folder for the converted files to be put in and how they are named.

Then just use the add file or add folder button to import your wav files and convert.

---

### Post by satish_j on 2010-05-05
> **3rdalbum said:**
> I know where you got that idea from, but Lame **is** an MP3 encoder. That's all it does!

If you want to use FFMPEG instead, go ahead. It still uses Lame as the backend. If you're a real audio enthusiast, though, you might be more satisfied with using Lame directly.

can you help me with the command??

---

### Post by MooPi on 2010-05-05
lame has a multitude of commands depending on your wants or needs, It would be best to consult the man pages.
```
man lame
```Or if you just want an 128 bit mp3
```
lame -b 128 your.wav
```

---

### Post by FakeOutdoorsman on 2010-05-05
> **satish_j said:**
> i cannot convert wav files to mp3..after searching,i came to know this is because ffmpeg is not having mp3 support and the solution is to compile it with mp3 support.My questions are:
1. How can i know whether,for a particular codec,ffmpeg support is there or not??I mean from ffmpeg -help or any other command..
2. Do i need to remove ffmpeg completely before compiling it again with mp3 support??

You need to manually enable some encoders in FFmpeg from the repository.  There are several methods to do this (several already mentioned) and is explained here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

More recent versions of FFmpeg now use the following command to list the available encoders and decoders:
```
ffmpeg -codecs
```
I'm not sure if the repository FFmpeg for Lucid is new enough for this command, otherwise you can use *ffmpeg -formats* as mentioned earlier.

Lame can encode from wav to mp3 as shown by MooPi. See posts #9 and #10 in the [ffmpeg convert ogg](http://ubuntuforums.org/showthread.php?p=9127752) thread for some FFmpeg and lame examples for encoding to .mp3 from any format.

---

### Post by satish_j on 2010-05-05
Thanks everyone...i finally used lame to convert wav to mp3.lame --help exlpained the basic syntax...very easy to use...
iam learning new things everyday....;);)
Friends,i have a new question about ffmpeg now..Dont know whether i should start a new thread for it or not...
i extracted the video and audio files from an mkv file(I got h264 and mp3 files)..
I ran ffmpeg command on the h264 file to convert it into avi format.THough,I got the file in avi format,but the duration of this avi is about 20min longer than the original mkv file..
How can i use ffmpeg command to get an avi file of same length??
I ran foll ffmpeg command:
```

ffmpeg -i /home/satish/RawVidFile.h264 -vcodec mpeg4 -vtag xvid -b 2500k /home/satish/AVIfile_NoAudio.avi

```

_*I think i found out the reason..the original file is using a framerate of 30 frames/second,whereas i did not specify anything about it in ffmpeg command and i got 25fps(which is the deafult value)*_

---

### Post by satish_j on 2010-05-08
Nopes,framerate is not the issue..I re-encoded with 30 fps,but still the video is longer in duration than original vid..
How can i encode an h264(raw video file) file to an avi file using ffmpeg _keeping same video duration??_
Any ideas???

---

### Post by satish_j on 2010-05-12
prob solved...
had to switch to avidemux...:popcorn:

---

