---
title: "VLC will not open at all please help me understand why"
date: 2011-03-28
forum: General Help
---

### Post by metalf8801 on 2011-03-28
I'm trying to understand why VLC will not open. 

If I try to open it by 
Applications > Sound & Video > VLC 
Nothing happens 
If I right click on a FLAC or OGG files and try to open it with VLC nothing happens 

So next I tried to open it a terminal using the command vlc %U I then get the following output  
```

username@nameofdevice:~$ vlc %U
VLC media player 1.1.4 The Luggage (revision exported)
Segmentation fault

```
What does that mean? 

I've found post with similar problems that claimed to have been solved by simply reinstalling VLC which did not work for me. So then I tried purging VLC and reinstalling which still did not work. I've tried turning off Compiz which didn't help. I've done a lot of searching for solutions none of which has helped. If anyone has any suggestion that would be great or if anyone could tell me what the error message means that would be even better.

Thank you 
Dan

---

### Post by Soul-Sing on 2011-03-28
```
sudo apt-get remove --purge vlc-data
```

```
sudo apt-get install vlc
```

---

### Post by metalf8801 on 2011-03-28
> **leoquant said:**
> ```
sudo apt-get remove --purge vlc-data
```

```
sudo apt-get install vlc
```

I already tried that and it didn't work

---

### Post by metalf8801 on 2011-03-28
I was running ESET NOD32 Antivirus RC1 for Linux (I use it to keep from infecting any of my Windows boxes) and after I uninstalled it I was able to use VLC without any problems. 

Thank you leoquant for trying to help 
Dan

---

