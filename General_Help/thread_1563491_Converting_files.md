---
title: "Converting files"
date: 2010-08-29
forum: General Help
---

### Post by Kajmak on 2010-08-29
Hello, is it possible to convert multiple flv files into mp3 files?

---

### Post by Vaphell on 2010-08-29
[http://ubuntuforums.org/showthread.php?t=1101022](http://ubuntuforums.org/showthread.php?t=1101022)

---

### Post by Kajmak on 2010-08-29
Well I've already downloaded videos from youtube and saved them, so downloading them again and saving as audio files would be a pain in the a..

Also I'm familiar with the way of converting, i was just thinking if i could convert multiple files at once so i could save some time.

---

### Post by Vaphell on 2010-08-29
quote from #10

To extract mp3 audio from each flv:
```
for j in *.flv; do ffmpeg -i "$j" -acodec copy "$j".mp3; done; rename 's/flv.mp3$/mp3/' *
```

as you can see it extracts audio to mp3 for every .flv file found in current dir

---

### Post by Kajmak on 2010-08-29
Ahhh ok , thanks !

---

### Post by andrew.46 on 2010-08-30
Be aware though that not all .flv files contain mp3 sound and in fact sites such as youtube are using h264 video and aac sound in a flv container these days for the so called 'High Quality' videos. By using -acodec copy in the manner suggested you run the risk of placing aac sound in an mp3 container, definitely an uncertain undertaking :).

If you are certain that your files contain mp3 sound perhaps the following might be slightly improved variation of the syntax suggested:

```

for j in *.flv
do 
ffmpeg -i "$j" -vn -acodec copy -map_meta_data 0:0 "${j%.flv}.mp3"
done

```

The -map_meta_data option might not exist for your version of FFmpeg, if it fails simply omit the option. If your sound is actually aac, as I suspect might be the case, you can transcode to mp3 with something like the following:

```

for j in *.flv
do 
ffmpeg -i "$j" -vn -acodec libmp3lame -ab 128k -map_meta_data 0:0 "${j%.flv}.mp3"
done

```

You might run into a little trouble with sound quality if the bitrate of your input files is a little low though...

Andrew

---

### Post by Kajmak on 2010-08-31
@ Vaphell

When I type in,
```
for j in *.flv; do ffmpeg -i "$j" -acodec copy "$j".mp3; done; rename 's/flv.mp3$/mp3/' *
```

They encode for a second or so then this shows up,

```
size=    5153kB time=342.08 bitrate= 123.4kbits/s    
video:0kB audio:5153kB global headers:0kB muxing overhead 0.000606%

```

And I get my files converted to mp3, but they're all marked with a padlock (Tried doing chmod 777 to unlock it, doesnt work) and are unable to listen to.
What's weird is that, they're all about 3-4 mb (As a regular mp3 file), but they only encode for a second. In practic, they should be like 10kb or so.

@ Andrew.46

I typed in,

```
for j in *.flv
do 
ffmpeg -i "$j" -vn -acodec libmp3lame -ab 128k -map_meta_data 0:0 "${j%.flv}.mp3"
done
```

But it says,

```
Unknown encoder 'libmp3lame'
```

Eventhough I've installed that package through the Ubuntu Software Center.

---

### Post by nothingspecial on 2010-08-31
You need to follow this

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Just copy and paste, make sure you read and understand what you are doing though, blindly copy and pasting is not a good idea.

---

### Post by andrew.46 on 2010-08-31
Hi Kajmak,

Nothingspecial's advice will get you running with libmp3lame, there is a slightly easier way if you are interested which is published by the same man:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

This will not get you such a modern copy as compiling your own but it will certainly enable mp3 transcoding. But can I ask if you could identify the codecs in a couple of your flvs? The easiest way is to run:

```
ffmpeg -i my_file.flv
```

where you will need to substitute the actual name of your file for 'my_file.flv'. This will show definitively whether you need to transcode to mp3 or simply copy the audio to an mp3 container. If you could paste the command and *full* terminal output into a post here?

Andrew

---

### Post by nothingspecial on 2010-08-31
> **Kajmak said:**
> @ Vaphell
(Tried doing chmod 777 to unlock it, doesnt work) 

I can see how you might do this out of frustration.

If you have any other users on your computer ({wife,husband}, kids, girlfriend etc), 777 is not a good idea.

I would suggest 644

If you are the only user then do what you like.

---

### Post by Kajmak on 2010-08-31
Well I did what Andrews said, i updated, downloaded WinFF, added all my video files and just pressed Convert, and it started converting all files :D

Thanks guys!

---

