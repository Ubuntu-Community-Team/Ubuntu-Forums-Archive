---
title: "How do you convert Video to Audio?"
date: 2011-01-27
forum: General Help
---

### Post by WlaadDyaab on 2011-01-27
Hi

When I had Windows XP I used to convert almost any YouTube video into audio (the whole video into audio) by going to [www.catchyoutube.com](www.catchyoutube.com), downloading VDownloader and just inserting the URL in the box provided; waiting for a couple of minutes and having an mp3 format file at the location that I want it to be in the desktop.

When I searched for something similar for Linux, because VDownloader was an .exe file and obviously wasn't going to work on Ubuntu. I found that I could get a video downloaded from YouTube but not an audio - I wait for the video to finish buffering; click on Places; Computer; File System; tmp; then rename the video folder and copy/relocate it to where ever on the desktop. Ending with this video format "Flash video (video/x-flv)".

My question is: is there a Linux program where I get to convert the entire video format to an audio format, possibly mp3?

Thanks

---

### Post by TeoBigusGeekus on 2011-01-27
```
ffmpeg -i nameofflashvideo.flv -acodec libmp3lame -ab 320k nameofsong.mp3
```

---

### Post by cascade9 on 2011-01-27
> **TeoBigusGeekus said:**
> ```
ffmpeg -i nameofflashvideo.flv -acodec libmp3lame -ab 320k nameofsong.mp3
```

Dont use 320k. The biggest audio bitrate that youtube uses is 232k, so converting to 320k will just waste space. That 232k bitrate is only for HD, normal youtube is 128k or even lower....Thats besides the way that lossy-lossy transcodes will reduce the audio quality. 

*edit- 232, 128, they are both VBR so you get that exact bitrate. 

A better way to do it is to just strip the video from the .flv/.mp4. See here- 

[http://ubuntuforums.org/showpost.php?p=8823611&postcount=14](http://ubuntuforums.org/showpost.php?p=8823611&postcount=14)

---

### Post by francf on 2011-01-27
Easy way, install this [http://www.miksoft.net/mobileMediaConverterDown.htm](http://www.miksoft.net/mobileMediaConverterDown.htm)

---

### Post by TeoBigusGeekus on 2011-01-27
> **cascade9 said:**
> Dont use 320k. The biggest audio bitrate that youtube uses is 232k, so converting to 320k will just waste space. That 232k bitrate is only for HD, normal youtube is 128k or even lower....Thats besides the way that lossy-lossy transcodes will reduce the audio quality. 

*edit- 232, 128, they are both VBR so you get that exact bitrate. 

A better way to do it is to just strip the video from the .flv/.mp4. See here- 

[http://ubuntuforums.org/showpost.php?p=8823611&postcount=14](http://ubuntuforums.org/showpost.php?p=8823611&postcount=14)
You're right, I just wrote 320k to be on the safe side.

---

### Post by 3rdalbum on 2011-04-11
You can open the video file with Audacity, which will immediately turn it into sound-only, and then export it. You might also be able to use Sound Converter; not entirely sure about that; but Audacity definitely works.

---

### Post by papibe on 2011-04-12
WinFF is very easy to use GUI program that uses ffmpeg. If you don't feel comfortable with the command line try WinFF, it is on the Software Center.

Regards.

---

### Post by Harix on 2011-04-24
You can open the video file with Audacity, which will immediately turn  it into sound-only, and then export it. You might also be able to use  Sound Converter; not entirely sure about that; but Audacity definitely  works.

How can I export the file? I cannot find any button...thanks

---

### Post by decrepit on 2011-04-24
It's under "file". You the have "export" or export "selection".
Then you have to choose which format, I think the default is ogg, and it won't do mp3 unless you have the "lame" library.

---

### Post by stinkeye on 2011-04-24
**_[COLOR="#ff0000"]Edit:[/COLOR]_** [I][COLOR="DimGray"]Just noticed francf has already recommended this one.
Oh well, worthy of a second mention.[/COLOR][/I]

I came accross [**_[COLOR="DarkRed"]Mobile Media Converter[/COLOR]_**]("http://miksoft.net/mobileMediaConverter.htm")
which has a deb file for download.
Seems very easy to use and has an integrated Youtube downloader. 
I converted a Youtube vid to mp3 and worked.

You'll need to add **mencoder** from the **medibuntu** repository.
Links for this are on the download page.

It's supposed to be able to convert to other formats as shown in pic.

---

### Post by Ghost_Mazal on 2011-04-24
I see there is only a 32 bit version of Mobile Media Converter

---

### Post by stinkeye on 2011-04-24
> **Ghost_Mazal said:**
> I see there is only a 32 bit version of Mobile Media Converter
From Mobile Media Converter's help page.
> Why don't you make a 64-bit version available?
Unfortunately, there is not way to do this because RealBASIC, in which MMC is written, does not produces 64-bit executables. You can install MMC on your 64-bit Debian-based Linux by using the command "sudo dpkg --force-architecture -i PACKAGE_NAME.deb"

---

### Post by Harix on 2011-04-25
> **decrepit said:**
> It's under "file". You the have "export" or export "selection".
Then you have to choose which format, I think the default is ogg, and it won't do mp3 unless you have the "lame" library.
Thanks, but still can not find ´file´ I rightclick and get: About Audacious, Play File, Play Location etc...where to find ´File´??
What is the ´Lame´lib and how to install?

---

### Post by dr.m0x on 2011-05-06
What the official FAQ fails to mention is that you must also install the meta package ia32-libs in addition to ffmpeg and mencoder in order to get mmc to install in a 64 bit system.

---

### Post by andrew.46 on 2011-05-11
> **TeoBigusGeekus said:**
> You're right, I just wrote 320k to be on the safe side.

My wife gets me to strip audio from video clips for her and I had exactly the same issue, but with multiple videos and different bitrates for the audio. I came up with the following which is more than a little clumsy but it works well for a big bunch of flvs:

```

for f in *.flv
   do 
   ffmpeg -i "$f" -acodec libmp3lame \
   -ab $(mplayer -frames 0 -identify "$f" 2>/dev/null \
   | grep -m 1 'ID_AUDIO_BITRATE' | cut -d '=' -f 2) \
   -vn "${f%.flv}.mp3"
done

```

This is a little off the topic here but I thought it might be useful to somebody and certainly my wife appreciates it :).

---

