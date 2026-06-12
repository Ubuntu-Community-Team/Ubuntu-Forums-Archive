---
title: "Container Convertor"
date: 2010-08-11
forum: General Help
---

### Post by TomAbada on 2010-08-11
hi all
i need a way to convert the containers of PHOTO`s and AUDIO`s files to minimum space as possible

for example .wav to .mp3
and photo to convert to .jpg

prefer to use the command line in order to write a script

i realy need help here
thanks in advance

---

### Post by TomAbada on 2010-08-11
anyone ? 
i realy need help here please

---

### Post by john newbuntu on 2010-08-11
"convert" and "ffmpeg" are two commands I know off the top of my head to do these kind of things.  You can do a 'man' on this for more details.  ffmpeg may not be available by default.

---

### Post by FakeOutdoorsman on 2010-08-11
> **TomAbada said:**
> hi all
i need a way to convert the containers of PHOTO`s and AUDIO`s files to minimum space as possible

for example .wav to .mp3
LAME can handle .wav:
```
lame -V4 input.wav output.mp3
```
or use FFmpeg with any audio input and attempt to copy metadata. You may need to enable additional encoders: [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)
```
ffmpeg -i input.foo -acodec libmp3lame -aq 4 -map_meta_data 0:0 output.mp3
```
or pipe from FFmpeg to LAME:
```
ffmpeg -i input.foo -f wav - | lame -V4 - output.mp3
```

> **TomAbada said:**
> and photo to convert to .jpg
```
sudo apt-get install imagemagick
convert input.foo output.jpg
```
or use *mogrify*, which is also from *imagemagick*. It is similar to *convert*, but will overwrite the original file.

---

