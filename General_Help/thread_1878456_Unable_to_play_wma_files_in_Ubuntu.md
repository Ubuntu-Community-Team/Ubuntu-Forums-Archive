---
title: "Unable to play wma files in Ubuntu"
date: 2011-11-09
forum: General Help
---

### Post by TheNixObserver on 2011-11-09
I have Lucid Lynx installed.   I have also installed Exaile and vlc media player.  When I try to play wma files, I get only a jerky and stuttering output in both Exaile and vlc media player as also the default media player.  I looked around in the forums and it was suggested that I run the following command to update gstreamer:

```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse 
gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg 
```However, even after running this command, I got the message saying that all the packages are already updated.  I am still unable to play the wma files properly and have to switch to Windows to get them to play in Winamp or WMP.

Any ideas?

---

### Post by duke.tim on 2011-11-09
Gstreamer should have covered it :/ you can try installing 

ubuntu restricted extras

from the software center and see if that fixes it...

---

### Post by JayKay3OOO on 2011-11-09
Run format factory in windows and convert them to mp3.

Well, that's what I did because I could never get them to play.

---

### Post by claracc on 2011-11-10
Perhaps you don't have w32codecs (32 bits system) and non-free-codecs installed?

---

### Post by linuxwin2 on 2011-11-10
You can use mplayer
```
$ sudo apt-get install mplayer*

```

---

### Post by notgary on 2011-11-10
There's a page on the Ubuntu Documentation site that covers playing restricted media formats which you can find [here]("https://help.ubuntu.com/community/RestrictedFormats"). There's a [section]("http://https://help.ubuntu.com/community/RestrictedFormats#Audio") that specifically deals with various issues you can encounter with restricted audio formats, and if you still can't get your WMA files to play (which I was never able to do, so I just rebought them from the Ubuntu One store), you can try converting them to a format that does work using [this]("http://https://help.ubuntu.com/community/RestrictedFormats/ConvertingToOpen") guide.

---

### Post by andrew.46 on 2011-11-10
Windows Media Audio can be one of 4 variations, details [here]("http://en.wikipedia.org/wiki/Windows_Media_Audio#Codecs"). If you are running a 32bit system with MPlayer and the 'win32' codecs from Medibuntu you can play all of these :).

---

### Post by TheNixObserver on 2011-11-10
Installing mplayer solved the problem, thanks.

---

### Post by killermist on 2011-11-10
I don't know if this is the case in your case or not, but some WMA files have that annoying DRM protection in them too.

I do have to agree with some of the other recommendations to re-rip or reacquire (if possible) as something without DRM or windows file formats.
I definitely think that reencoding from WMA to an open format is a bad idea (not horrible, just bad) because of a generation of quality loss.

---

