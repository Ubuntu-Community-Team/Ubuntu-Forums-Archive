---
title: "Pulse Audio Volume Control GUI flashes on then off"
date: 2010-06-26
forum: General Help
---

### Post by Bucky Ball on 2010-06-26
Hi all,

When I hit the Pulse Audio Device Chooser icon and then click on 'Volume Control' the volume control GUI flashes on for long enough for me to realise it has flashed on and then is gone again! If I run the chooser as root from a terminal (sudo padevchooser) I get this response when I hit the error:

```

**
** ERROR:(pavucontrol.cc:339):void StreamWidget::setVolume(const pa_cvolume&, bool): assertion failed: (v.channels == channelMap.channels)
```Strange thing is, I have spent a lot of time working on my wife's laptop and Pulse Audio was working great (after many brain twisting, hair ripping hours of working on it) and indeed is still working despite the lack of GUI. This is all good except I want to change the output device for ringing in Skype and this is where I need to 'Move Stream ...' and can't get to it. Any help or ideas appreciated.

---

### Post by Bucky Ball on 2010-06-27
Bump. When I sudo now I get the 'Connection Refused' message.

For some weird reason it is not giving me 'Audio Capture Problem' when I'm trying to make a Skype test call with the USB headset now also. After talking with it all afternoon and everything's been fine! The machine hasn't even been switched off or changed in any way since the last call. Mystery. Pulse Audio has been a really long nightmare ...

---

