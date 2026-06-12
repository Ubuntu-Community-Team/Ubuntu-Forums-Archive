---
title: "Firefox Ubuntu 12.04 not playing MP3 links on webpages-Quicktime?"
date: 2012-10-09
forum: General Help
---

### Post by 777funk on 2012-10-09
I notice if I click a hyperlink with an audio clip, it won't automatically play like it will in windows. Seems like it uses Quicktime in Windows to play the clip. I'm guessing there's not Quicktime in Ubuntu. Are there any other options?

---

### Post by zvacet on 2012-10-09
This should do 


```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 777funk on 2012-10-10
> **zvacet said:**
> This should do 


```
sudo apt-get install ubuntu-restricted-extras
```

Thanks for that. I already have that (did that upon 12.04 install) but I ran it again just incase and it confirmed. 

All I get when I click on an MP3 file links is just some media player looking animation that immediately stops and no sound from the get go.

---

### Post by Vaphell on 2012-10-10
maybe try this:
```
sudo apt-get install gecko-mediaplayer
```
it should install multimedia plugin in gecko-based (eg firefox) browser

---

