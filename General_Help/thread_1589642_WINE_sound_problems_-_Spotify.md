---
title: "WINE sound problems - Spotify"
date: 2010-10-06
forum: General Help
---

### Post by kolo-01 on 2010-10-06
first of all i think spotify is great and if you are into music then i recommend it, it works ok on wine, but i have found that there are quite a few sound issues with it, i think the majority of these come from running two or more applications through wine at the same time. when i start another program in wine often spotify stops playing, usually it is ok after a restart but i have found that this is not nececssarily the case and a lot of things on wine to be extremely temperamental in terms of sound and stability. if anyone knows what the problem with sound and ideas of how to improve sound/stability in wine then please let me know. i am unsure about whether pulseaudio is/part of the problem here, i tried uninstalling it for a bit and things worked ok, im not sure if they were any better as i didnt try without it for very long, as it is integral to ubuntu in other ways.

---

### Post by andy_spoo on 2010-10-09
Any particular reason why you're running Spotify through wine?

There appears to be a Linux version available (I've installed it on Lucid with no problems, but have yet to try it).

[http://www.spotify.com/uk/download/previews/](http://www.spotify.com/uk/download/previews/)

Andy



> **kolo-01 said:**
> first of all i think spotify is great and if you are into music then i recommend it, it works ok on wine, but i have found that there are quite a few sound issues with it, i think the majority of these come from running two or more applications through wine at the same time. when i start another program in wine often spotify stops playing, usually it is ok after a restart but i have found that this is not nececssarily the case and a lot of things on wine to be extremely temperamental in terms of sound and stability. if anyone knows what the problem with sound and ideas of how to improve sound/stability in wine then please let me know. i am unsure about whether pulseaudio is/part of the problem here, i tried uninstalling it for a bit and things worked ok, im not sure if they were any better as i didnt try without it for very long, as it is integral to ubuntu in other ways.

---

### Post by Quarkrad on 2010-10-09
To eliminate things I have Spotify working 100% with wine.  I'm using wine 1.1.42 and a recent version of Spotify from the web version  0.4.8.213.g936012fc

---

### Post by kolo-01 on 2010-10-09
> **andy_spoo said:**
> Any particular reason why you're running Spotify through wine?

There appears to be a Linux version available (I've installed it on Lucid with no problems, but have yet to try it).

[http://www.spotify.com/uk/download/previews/](http://www.spotify.com/uk/download/previews/)

Andy


i have downloaded that version but ive heard that it doesnt work unless you have a premium account as they have not found a way to get the ads working on free accounts, and the native version doesnt work on mine yet for that reason it seems, are you using premium? if not did you read/experience any problems with getting free compatible with native spotify?

---

### Post by garethpn on 2010-11-23
Type winecfg at the terminal or bring up the configuration dialog for Wine from the application shortcut.

Under the audio tab un-tick the ALSA driver and tick the EsounD driver.

Hope this helps.

---

