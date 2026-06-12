---
title: "Having issues with dvd ripping and codecs - cant tell whats installed or not"
date: 2011-09-14
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-14
So here I am, on my last leg..

I've been trying for a day or so on how to rip dvds and each time ive ran into issues.

I've downloaded Medibuntu and then downloaded and installed libdvdcss as well as other codecs, and installed Dvd::rip and i'm having issues with it telling me that


"It seems that transcode ripping stopped short.
The movie has 161936 frames, but only 135073
were ripped. This is most likely a problem with your
transcode/libdvdread installation, resp. a problem with
this specific DVD." 

so I went and installed libdvdread and it still didnt fix the issue.

so I uninstalled Dvd::rip and basically I can't tell what's installed and what's not installed anymore. and im close to wiping the drive and re-installing ubuntu fresh, because I don't understand how to find out what Ive got installed or not..

I need help.  Major.  I've tried looking up tutorials on how to encode with Mencoder and Mplayer, but I cant figure out how to install Divx or if I even have Divx installed....

Please respond with some sort of help that I can use...

---

### Post by LowSky on 2011-09-15
Handbrake is the best thing since sliced bread
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk
```

---

### Post by AlexOnVinyl on 2011-09-15
> **LowSky said:**
> Handbrake is the best thing since sliced bread
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk
```

Thanks mate. but Handbrake tends to overheat my computer.

---

