---
title: "Play .mov stream"
date: 2010-07-17
forum: General Help
---

### Post by arnab_das on 2010-07-17
I'm finding it very difficult to play a video stream of .mov format. The Totem Media player gives me an error : **GstDecodeBin2: This appears to be a text file**

Even Real Media Player for linux is giving me an error: **General error: HXR_CORRUPT_FILE		 (0x80040091) **

Even VLC hangs on trying to play it.

(BTW the file isnt corrupt though, its apple's last night's iphone press conference from their official website - [http://events.apple.com.edgesuite.net/100716iab73asc/event/index.html](http://events.apple.com.edgesuite.net/100716iab73asc/event/index.html).)

---

### Post by arnab_das on 2010-07-18
bump

---

### Post by Vaphell on 2010-07-18
i saved to desktop and both vlc and gnome mplayer played it just fine, totem spitted that text file error

PS. what a bunch of apple fanbois :)

---

### Post by arnab_das on 2010-07-19
> **Vaphell said:**
> i saved to desktop and both vlc and gnome mplayer played it just fine, totem spitted that text file error

PS. what a bunch of apple fanbois :)

that did it! thanks.

erm i watch apple vids coz i can criticize them better. know thy enemy :)

---

### Post by mc4man on 2010-07-19
As an aside vlc 1.1.X and totem will play without dl'ing, though depending on your connection may be best to dl
(is actually a rtsp stream, so this would work better in totem

```
rtsp://a2047.v1411b.c1411.g.vq.akamaistream.net/5/2047/1411/2_h264_650/1a1a1ae454c430950065de4cbb2f94c226950c7ae655b61a48a91475e243acda3dac194879adde0f/100716wiuhvbaealjhvb_1_650.mov

```

---

