---
title: "FFmpeg and ipodvidenc issues"
date: 2010-02-24
forum: General Help
---

### Post by al1x on 2010-02-24
I have an ipod 4th generation and I downloaded the ipodvidenc script to convert videos but when I am trying to convert a video I am getting the message "unknown encoder aac" .Even when I change it to  -acode libfaac its the same thing.I have installed the ffmpeg 4:0.5 svn 20090706 but I don't know what else to do.Can anyone help me?:confused:

---

### Post by FakeOutdoorsman on 2010-02-24
Forget *ipodvidenc*.  FFmpeg now has iPod specific presets that will give you better quality than that script.  I assume you're using Karmic.  Ubuntu Karmic does not enable *libfaac* in FFmpeg due to the current status of the *libfaac* license.  This can be fixed by installing a package from Medibuntu.  See *Option C* (or *Option A*) in:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

Once you get that completed you can try this command:
```
ffmpeg -i input.avi -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod320 -crf 24 -f ipod -threads 0 output.mp4
```

---

### Post by al1x on 2010-02-24
Thanks a lot!! May I copy-paste the code you have sent me to ipodvidenc script?Is there any way to avoid typing all this code every time or I 'll just do it manually?

---

### Post by FakeOutdoorsman on 2010-02-24
> **al1x said:**
> Thanks a lot!! May I copy-paste the code you have sent me to ipodvidenc script?
Of course you can.  Did my example work?  I don't have an iPod.
> **al1x said:**
> Is there any way to avoid typing all this code every time or I 'll just do it manually?
You can make a simple script much like *ipodvidenc*:
```
#!/bin/bash
# usage: ipoodvid.sh input.foo output.mp4

ffmpeg -i $1 -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod320 -crf 24 -f ipod -threads 0 $2

exit
```
Now make the script executable.  I named it *ipoodvid.sh*, but you can give it any name you want:
```
chmod +x ipoodvid.sh
```
Now run it (*input.foo* being the name of your input file):
```
./ipoodvid.sh input.foo output.mp4
```
You may want to adjust the *-vpre* or *-crf* value.  See the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for a good introduction.

---

### Post by al1x on 2010-02-26
Yup it worked just perfect and the encoding is very good.Thanks again , your explanations was very good :D

---

