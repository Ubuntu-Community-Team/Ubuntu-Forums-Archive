---
title: "Sound stopped working after atempting driver update"
date: 2010-12-25
forum: General Help
---

### Post by Dr.Leet on 2010-12-25
Hi

I recently installed ubuntu 10.10 64 bit. I experienced a problem trying to use my TV to watch a movie. The TV wouldn't play any sound but showed my desktop nicely. So i tried do update my sound driver using the linux driver from this site: 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false) 

Some kind of fault happened during the installation and after rebooting the pc sound wouldn't work.

Can anyone help?

---

### Post by Dr.Leet on 2010-12-26
is it possible to make Ubuntu reinstall the sound drivers automatically, just like it does when you install the whole system? Because sound worked just fine after i installed ubuntu.

---

### Post by lidex on 2010-12-26
> **Dr.Leet said:**
> is it possible to make Ubuntu reinstall the sound drivers automatically, just like it does when you install the whole system? Because sound worked just fine after i installed ubuntu.
Try this. In a terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

---

### Post by IWantFroyo on 2010-12-26
System-Administration-Additional Drivers. You could remove and re-activate the driver, or maybe you missed something. Also, the system has glitches. One Linux computer I looked at had no volume until I went into Sound (System-Preferences), selected the speaker, amped it, and then clicked test speaker. After that, it worked perfectly.

---

