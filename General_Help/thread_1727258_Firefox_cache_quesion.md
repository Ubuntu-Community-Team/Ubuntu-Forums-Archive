---
title: "Firefox cache quesion"
date: 2011-04-12
forum: General Help
---

### Post by LiamG on 2011-04-12
When streaming audio, firefox stores files in the cache folder (home/.mozilla/firefox/xxx.default/OfflineCache

However, one the file has finished downloading, it disappears from this folder. Does anyone know where it goes?

---

### Post by sanguinoso on 2011-04-12
I don't have that folder personally but my guess is that when its streaming audio it treats that directory as a temp folder and deletes. When the audio is actually playing the audio file will be in memory.

---

### Post by seawolf167 on 2011-04-12
Aye, I don't have an OfflineCache folder either, all mine go to 

```
ls ~.mozilla/firefox/xxxxxxxx.default/Cache
```

---

### Post by Frogs Hair on 2011-04-12
When you play a video  after buffering  the files  are in File system /temp and it is possible to save them at that point while the browser is still open . If  adobe flash is being used , cookies are stored in home /hidden /.adobe. 

I cannot  find a good description of how the Ubuntu or  Firefox  temporary file functions and removes those files . If all those files were saved automatically you could  run out space pretty quickly .

---

### Post by LiamG on 2011-04-12
You're right, it's "Cache" not "OfflineCache".

Frogs Hair, I have a "tmp" folder, not "temp", but I can't find it in there either. Any suggestions?

---

### Post by lovinglinux on 2011-04-12
Try to clear your Cache before viewing the videos. I think this problem happens when the cache reaches it's limit. So, the video stays in memory. But I am not sure.

I also recommend using [Video Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/") extension for general video download and my [FlashVideoRelacer]("http://www.webgapps.org/addons/flashvideoreplacer"), for replacing flash with gecko-mediaplayer in some supported sites.

---

