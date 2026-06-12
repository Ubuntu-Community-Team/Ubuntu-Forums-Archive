---
title: "mp3/wav files will not play in Chromium"
date: 2010-12-15
forum: General Help
---

### Post by alem189 on 2010-12-15
When I open a direct link to a mp3 or wav audio file in Chromium, it will not play. I see a player in the middle of the screen, but nothing happens. Ogg vorbis works fine. I have all of the codecs installed, and all of them play in Rhythmbox. Do I have an issue with plugins? If so, which ones do I need?

---

### Post by Habeouscorpus on 2010-12-15
It's not just on linux. I believe that Windows Google Chrome has this issue to. Try sifting through the plugin directory to find a quick patch.

---

### Post by alem189 on 2010-12-16
Could you be more specific?  Where would I find the plugin directory?  It's not in .config/chromium.  Also, what do you mean by "try sifting through the plugin directory to apply a quick patch"?

---

### Post by rtb on 2010-12-29
I believe I encountered the same problem on Lucid Lynx: Google Chromium, an MP3 off the web, player in the middle of the screen, play button grayed out and no sound.

The solution appears to be this simple: install the package chromium-codecs-ffmpeg-extra.  (I stumbled across this on another forum somewhere.)

Synaptic is one way to install the package.  Select System | Administration | Synaptic Package Manager.  Click "Search" and enter the package name.  Click on the package and select "Mark for Installation".  The click "Apply".

It can also be done with a single command in a terminal:

```
sudo apt-get install chromium-codecs-ffmpeg-extra
```

Enter your password when prompted.

Note that the package is "non-free".  Apparently there are restrictions on the source, and that's why it's not installed by default.

---

### Post by alem189 on 2010-12-31
Aha! Thank you. I really think you should be *notified* of this when you install Chrome, though...:mad:

---

