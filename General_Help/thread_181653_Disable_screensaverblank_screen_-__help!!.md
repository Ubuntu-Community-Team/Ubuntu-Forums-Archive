---
title: "Disable screensaver/blank screen -  help!!"
date: 2006-05-24
forum: General Help
---

### Post by IndigoMontoya on 2006-05-24
Hi,

I am having a problem with my screensaver/power management.  When I use mplayer to watch streaming video sometimes (not always) the screen goes black after about 20 minutes.  Using system->preferences->Screensaver I have disabled the screensaver and also gone to the advanced mode and disabled display power management.  The command I use to run my stream is:
```

mplayer *stream* -ao alsa -fs -stop-xscreensaver 
```

this is actually run in a script (I pass in a list of winampTV files and since alot of them are full, it tries one until it gets in), so would running -stop-xscreensaver multiple times actually turn it off then on then off then.....?

Thanks for your help,
Scott

---

### Post by IndigoMontoya on 2006-05-25
I thought I would add that sometimes (not always) my screen will go blank after some time (I assume this is from the screensaver) of no use.  Also when the laptop is unplugged the monitor gets dimmed, so I see that as the power management not being off.  Is there a non-graphical way I can confirm the settings?  Or even change them?  

Thanks!

---

