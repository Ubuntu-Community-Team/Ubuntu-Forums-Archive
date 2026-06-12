---
title: "Missing video codec?"
date: 2012-04-22
forum: General Help
---

### Post by Ertai87 on 2012-04-22
I'm not sure if this forum is the best place to post this, but I'm having a problem with VLC, and I figured I'd start my search for a fix here.  Basically, I have a video in .mkv format, and upon playing it in VLC, I get audio but the video is just a blank green screen.  Does anyone know of any problems like this with VLC?  As far as I know, I have the latest version of the player.  A friend of mine has tried playing the same video in Media Player Classic (for Windows) and he said it works fine in that, which is why I think it might be a codec issue.

---

### Post by papibe on 2012-04-23
Hi Ertai87.

I would be valuable to know what video codec was your video encoded with.

While playing the video, could post what is says in:
```
VLC -> Tools -> Codec Information
```
Regards.

---

### Post by Ertai87 on 2012-04-23
Alright, there's a lot of info here and I can't seem to copy-paste it, so I'll post the video codec info:

Type: Video
Codec: H264-MPEG-4 AVC (part 10)(avc1)
Language: &#26085;&#26412;&#35486;
Resolution: 1280x720
Frame rate: 23.976215

---

### Post by Gremlinzzz on 2012-04-23
[http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Restricted_Extras](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Restricted_Extras)

The Ubuntu Restricted Extras will install Adobe Flash Player, Java Runtime Environment (JRE) (sun-java-jre) with Firefox plug-ins (icedtea), a set of Microsoft Fonts (msttcorefonts), multimedia codecs (w32codecs or w64codecs), mp3-compatible encoding (lame), FFMpeg, extra Gstreamer codecs, the package for DVD decoding (libdvdread4, but see here for info on libdvdcss2), the unrar archiver, odbc, and cabextract. It also installs multiple "stripped" codecs and avutils (libavcodec-unstripped-52 and libavutil-unstripped-49). This is a single command approach. 
:popcorn:

---

### Post by Ertai87 on 2012-04-23
> **Gremlinzzz said:**
> [http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Restricted_Extras](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Restricted_Extras)

The Ubuntu Restricted Extras will install Adobe Flash Player, Java Runtime Environment (JRE) (sun-java-jre) with Firefox plug-ins (icedtea), a set of Microsoft Fonts (msttcorefonts), multimedia codecs (w32codecs or w64codecs), mp3-compatible encoding (lame), FFMpeg, extra Gstreamer codecs, the package for DVD decoding (libdvdread4, but see here for info on libdvdcss2), the unrar archiver, odbc, and cabextract. It also installs multiple "stripped" codecs and avutils (libavcodec-unstripped-52 and libavutil-unstripped-49). This is a single command approach. 
:popcorn:

Installed it.  Didn't work.  Any other ideas?  I could have just gotten a corrupt video file.

---

### Post by papibe on 2012-04-23
Try following the steps described [here]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg") to add the h264 codec to ffmpeg (I would use the medubuntu repository).

Tell us how it goes.
Regards

---

### Post by Gremlinzzz on 2012-04-23
> **Ertai87 said:**
> Installed it.  Didn't work.  Any other ideas?  I could have just gotten a corrupt video file.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Audio_Video_Conversion#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Audio_Video_Conversion#DVD_Playback_Capability)

DVD Playback Capability



Ubuntu 11.10 (Oneiric Ocelot) Guide
[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

---

### Post by techsupport on 2012-04-23
> **Ertai87 said:**
> I'm not sure if this forum is the best place to post this, but I'm having a problem with VLC, and I figured I'd start my search for a fix here.  Basically, I have a video in .mkv format, and upon playing it in VLC, I get audio but the video is just a blank green screen.  Does anyone know of any problems like this with VLC?  As far as I know, I have the latest version of the player.  A friend of mine has tried playing the same video in Media Player Classic (for Windows) and he said it works fine in that, which is why I think it might be a codec issue.

Try using a to-do list after you install Ubuntu...  That will help you to be sure you have everything you need for media codecs installed..

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

Cheers! 

):P

---

### Post by Ertai87 on 2012-04-23
> **papibe said:**
> Try following the steps described [here]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg") to add the h264 codec to ffmpeg (I would use the medubuntu repository).

Tell us how it goes.
Regards

Nope, didn't work.  I'm going to double-check with my friend to make sure we actually have exactly the same video, and that he doesn't have a different version.  There are multiple versions of the video, so it's possible.  Is there any other debugging information that might be relevant?

As a side note, do I need to reboot after doing the codec update in order to make it work?  AFAIK most installations work out-of-the-box, with no reboots required, but not sure on this one.

EDIT: Checked with my friend.  Turns out his versions of the video are different than mine.  I'm going to get his versions and see if that works.  Thanks, guys!

---

### Post by Cheesemill on 2012-04-23
VLC does not use any of the system installed codecs.

VLC uses internal codecs that are part of the VLC application so installing any other codecs wont make any difference.

It sounds like a problem with the version of the file that you have, you can get more info by doing:
```
ffmpeg -i <filename>
```
or
```
mediainfo <filename>
```

---

