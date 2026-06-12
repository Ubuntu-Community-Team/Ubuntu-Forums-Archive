---
title: "Flash 10.2 Causes problems"
date: 2011-02-09
forum: General Help
---

### Post by Owen.C93 on 2011-02-09
So I've been having this problem with flash 10.2 on ubuntu, basically if  I have a youtube video open it is still  shown even when It's been closed or if I scroll off the page.

However weirdly it only shows on the black parts of my screen, for example a black  picture will show a perfect picture of the youtube player with the last  video I watched, even if I close the video (and firefox)

Annoyingly taking screenshots does not show the problem unfortunately.

I know it's hard to imagine but I was hoping someone might know a way I can fix this problem. (I understand it may be a flash bug, so I will seek help from them as well).

Thanks for any replies.

---

### Post by newrikk on 2011-02-11
Hello, same problem and a way to get flash working is to install chrome : flash version is 10.2.154 while it's 10.2.152 on ubuntu, and it works. Waiting for an update in ubuntu version.

---

### Post by newrikk on 2011-02-11
I copied flashplugin from chrome to firefox and chromium plugins directory and it worked :

Dowwload chrome and install it from : [http://www.google.com/chrome/eula.html?hl=fr]("http://www.google.com/chrome/eula.html?hl=fr")

then :

```
sudo cp /opt/google/chrome/libgcflashplayer.so /usr/lib/chromium-browser/plugins
```

```
sudo chmod ugo+x /usr/lib/chromium-browser/plugins/libgcflashplayer.so
```

and for firefox :
```
sudo cp /opt/google/chrome/libgcflashplayer.so /usr/lib/firefox-addons/plugins
``` 

```
sudo chmod ugo+x /usr/lib/firefox-addons/plugins/libgcflashplayer.so
```

Then I uninstalled chrome. :D

---

### Post by mr_niceguy on 2011-02-14
Thank you!

---

### Post by newrikk on 2011-02-18
:d

---

