---
title: "MKV playback in totem?"
date: 2006-03-19
forum: General Help
---

### Post by wr0x2 on 2006-03-19
I have a few MKV media files that I'd like to play in totem, but although the sound work the video won't show. Where can I get a codec? mplayer will play the files (I have the full codec pack from mplayerhq) but I don't like mplayer as well as totem, and it crashes too. Can I just grab the mkv codec from wherever it's stored for mplayer and install it for totem?

---

### Post by tuxcantfly on 2006-03-19
try totem-xine

sudo apt-get install totem-xine

it looks the same as totem, only it might be able to play your file

---

### Post by wr0x2 on 2006-03-19
totem-xine is already installed, although running "totem-xine" from the command line returns command not found.

---

### Post by tuxcantfly on 2006-03-19
try totem-gstreamer, and then install the various gstreamer0.8 or gstreamer0.10 (depending on your distro version) plugin packages

---

### Post by wr0x2 on 2006-03-19
I installed totem-gstreamer and now totem crashes with the error that another app is using the video output whenever i try to start it.

---

### Post by varunus on 2006-03-19
Totem-xine should work with the mplayer codecs.  Where did you install the codec pack?  It needs to be in /usr/lib/win32 i think for totem to find them.

Or, you could install the w32codecs package from the PLF (google around in the forums for it).

---

### Post by tuxcantfly on 2006-03-19
try rebooting

are you using dapper drake or breezy? if you're using breezy, you might need to upgrade your totem and gstreamer to the dapper versions (gstreamer0.10, the dapper version, works better than gstreamer0.8, the breezy version)

---

### Post by tdwester on 2006-03-19
You may want to try VLC player it seems to play just about anything.

---

### Post by wr0x2 on 2006-03-19
VLC won't play the file.

---

### Post by tuxcantfly on 2006-03-19
how about mplayer?

---

### Post by tuxcantfly on 2006-03-19
if you don't like the look of mplayer, just use a different skin (install mplayer-skins first)

---

### Post by wr0x2 on 2006-03-19
I don't like the seperate control scheme of mplayer, and my version is messed up. I've uninstalled and reinstalled, but it won't let me seek forward in these files, and whenever I've used mplayer, it's ALWAYS made the audio horribly out of sync with the video. Totem works well for me. Does totem have a codec folder where I can drop in mplayer's codecs?

---

### Post by tdwester on 2006-03-19
Here is the link to the codec for mkv. Funny the lis VLC as being able to play it.:confused: 
[http://www.matroska.org/downloads/linux.html](http://www.matroska.org/downloads/linux.html)

---

### Post by wr0x2 on 2006-03-19
How do I install that codec?

---

### Post by wr0x2 on 2006-03-20
OK, so no one knows?

---

### Post by varunus on 2006-03-20
Mplayer can play the files, right?  Where did you install the codecs?  Totem-xine should use mplayer codecs if they're in the right place.  You may also need to install all xine-codec related packages from synaptic.

---

### Post by wr0x2 on 2006-03-20
All that I'm wondering is where the totem codec folder is. Everything else I can take care of.

---

### Post by wr0x2 on 2006-03-20
Hmm, I just did a remove and then reinstall of vlc, and it still won't play the file. I checked the site and matroska is fully supported. Where are the codec folders for these apps?

---

### Post by tuxcantfly on 2006-04-09
actually, totem-gstreamer supports the file. just install gstreamer0.10-ffmpeg (for dapper) or gstreamer0.8-ffmpeg (older versions), then switch from totem-xine to totem-gstreamer. the commands:

sudo apt-get install gstreamer0.10-ffmpeg
sudo apt-get install totem-gstreamer

---

### Post by tuxcantfly on 2006-04-09
you could also just use the plain ffmpeg package to reencode it into something that more players support, like mpeg. to install it:

sudo apt-get install ffmpeg

---

