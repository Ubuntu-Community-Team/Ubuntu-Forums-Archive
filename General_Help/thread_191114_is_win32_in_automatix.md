---
title: "is win32 in automatix ???"
date: 2006-06-07
forum: General Help
---

### Post by kelmer on 2006-06-07
Hi everyone,
first of all I would like to thank the fantastic work of **Automatix** developers. It really made things easier for newbies like me. However I am not succeding in stalling **win32 codecs**, and therefore my mozilla plugins are failing to play some wmv9 videos(only sound playing). I tried changing the repositories myself and installing via command line but no success there neither. If it is in automatix, which of the options contains this codec ? because "audio & DVD codecs", for some reason, are not installing via Automatix, but I'm not sure this codecs are there.
Any help would be very appreciated. Thanks.

---

### Post by tseliot on 2006-06-07
[QUOTE=kelmer]Hi everyone,
first of all I would like to thank the fantastic work of **Automatix** developers. It really made things easier for newbies like me. However I am not succeding in stalling **win32 codecs**, and therefore my mozilla plugins are failing to play some wmv9 videos(only sound playing). I tried changing the repositories myself and installing via command line but no success there neither. If it is in automatix, which of the options contains this codec ? because "audio & DVD codecs", for some reason, are not installing via Automatix, but I'm not sure this codecs are there.
Any help would be very appreciated. Thanks.[/QUOTE]
Which version of Ubuntu do you use? Ubuntu 32bit or Ubuntu 64 bit?

---

### Post by kelmer on 2006-06-07
hi tseliot,
  32 bits

---

### Post by Thomaseov on 2006-06-11
I'm having the same problem with 32 bit dapper...codecs are failing to install via automatix (only wmv not functioning) as is real player.  Everything else works beautifully.  

Is this widespread?

---

### Post by taurus on 2006-06-11
[QUOTE=Thomaseov]I'm having the same problem with 32 bit dapper...codecs are failing to install via automatix (only wmv not functioning) as is real player.  Everything else works beautifully.  

Is this widespread?[/QUOTE]
I have to install RealPlayer by hand which takes like 2 seconds...  You can download the latest version from [http://www.real.com/](http://www.real.com/).  After saving it, RealPlayer10GOLD.bin, change the permission and install it to /opt/RealPlayer.  When it asks if you want it to link to /usr/bin, answer yes so everybody can run realplay from anywhere...
```

chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```

---

