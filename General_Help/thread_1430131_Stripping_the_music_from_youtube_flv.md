---
title: "Stripping the music from youtube flv"
date: 2010-03-15
forum: General Help
---

### Post by aviedw on 2010-03-15
I know its possible to strip the music or the sound from a youtube flv file and make it into a mp3. I actually did a google search and found a decent source. I went through the steps with no dice. So now im hoping that someone here might also try to do it to see if its just me  or if the steps provided at the link are wrong. thanks.

Here's the link [http://symbolik.wordpress.com/2007/10/10/extracting-an-mp3-from-a-youtube-flash-flv-download/]("http://symbolik.wordpress.com/2007/10/10/extracting-an-mp3-from-a-youtube-flash-flv-download/")

---

### Post by vzomik on 2010-03-15
&#21482;&#26159;&#35797;&#35797;&#33021;&#19981;&#33021;&#21457;&#20013;&#25991;&#65374;

---

### Post by terry f on 2010-03-15
I think you can extract the audio from a flv file using audacity.  You will need ffmpeg installed, I think.  If that don't work you could also do it with vlc.  I would try using audacity though.  Let me know if you need help using audacity to extract the audio.

---

### Post by gmargo on 2010-03-15
> **aviedw said:**
> no dice
Why don't you say what did happen?

I was able to use ffmpeg by following similar instructions on the forum, probably from this post: [http://ubuntuforums.org/showthread.php?t=989620](http://ubuntuforums.org/showthread.php?t=989620)

---

### Post by qyot27 on 2010-03-15
Flash already uses either MP3 or AAC audio.

1) Install & use the youtube-dl Python script to snag the video:
[http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home) (you can always get the latest version here)

chmod +x youtube-dl
sudo cp youtube-dl /usr/bin/youtube-dl
youtube-dl -l -b -w video_url

2) ffmpeg -i input.flv -vn -acodec copy output.mp3

or, if the output is an MP4 file (or an FLV with AAC audio)

MP4Box -raw 2 video.mp4 (this is assuming -raw 2 points at the audio; if -raw 2 doesn't work, use -raw 1)
MP4Box -add video_track2.aac output.mp4

ffmpeg -i input.flv -vn -acodec copy output.aac
MP4Box -add output.aac output.mp4

If you don't have MP4Box, then *sudo apt-get install gpac* first.



Both of those steps extract the audio out without converting it, keeping the quality the same as it is in the file.  If you need to convert AAC streams to MP3, then you can run the ffmpeg command on the MP4 you got out of MP4Box.

---

### Post by aviedw on 2010-03-15
Thanks for all the suggestions. I'm mobile right now so as soon as I get stationary ill try it again. Thansks again for all the help

---

### Post by asmoore82 on 2010-03-15
mplayer ~ the hacker's delight
```
mplayer -vo null -ao pcm:waveheader:fast *some.video.flv*
```

---

### Post by 2hot6ft2 on 2010-03-15
The Firefox DownloadHelper plugin will do that.
Tools > Add-ons > Get Add-ons
search for DownloadHelper
and install it.

---

### Post by aviedw on 2010-03-15
> **qyot27 said:**
> Flash already uses either MP3 or AAC audio.

1) Install & use the youtube-dl Python script to snag the video:
[http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home) (you can always get the latest version here)

chmod +x youtube-dl
sudo cp youtube-dl /usr/bin/youtube-dl
youtube-dl -l -b -w video_url

2) ffmpeg -i input.flv -vn -acodec copy output.mp3

or, if the output is an MP4 file (or an FLV with AAC audio)

MP4Box -raw 2 video.mp4 (this is assuming -raw 2 points at the audio; if -raw 2 doesn't work, use -raw 1)
MP4Box -add video_track2.aac output.mp4

ffmpeg -i input.flv -vn -acodec copy output.aac
MP4Box -add output.aac output.mp4

If you don't have MP4Box, then *sudo apt-get install gpac* first.



Both of those steps extract the audio out without converting it, keeping the quality the same as it is in the file.  If you need to convert AAC streams to MP3, then you can run the ffmpeg command on the MP4 you got out of MP4Box.

Hey thanks for this input it really helped. This download is what did it sudo apt-get install gpac 

Linux is amazing.

---

