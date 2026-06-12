---
title: "Problems With MP3 Tags"
date: 2011-11-28
forum: General Help
---

### Post by jlacroix on 2011-11-28
I'm having difficulty with the ID3 tags of my MP3 files. Basically, I spent several days last week going through my MP3's with Easytag, looking for missing information, and making sure they're perfect. And I thought I succeeded.

However, about 20 or 30 songs out of my 3095 MP3's show up as "Unknown Artist" when I copy them to my Android Phone, and show up that way in any music player. When I look at the songs again in Easytag, all the relevant data is there. I would like to fix these but according to Easytag, there's nothing to fix. Amarok and Juk both pick up all the data in the files fine.

Is there a hidden area that Easytag isn't copying data to that my phone is looking at?

---

### Post by McNils on 2011-11-28
Maybe this is a id3 tag version problem. There is a lot of versions of mp3 tags. Check the version of the tags. 
eyeD3 can show the version.

---

### Post by jlacroix on 2011-11-28
> **McNils said:**
> Maybe this is a id3 tag version problem. There is a lot of versions of mp3 tags. Check the version of the tags. 
eyeD3 can show the version.
Thanks. I checked out eyeD3, and I posted the output of two of the songs giving me issues below.

```

-------------------------------------------------------------------------------
Time: 03:26     MPEG1, Layer III        [ 320 kb/s @ 44100 Hz - Stereo ]
-------------------------------------------------------------------------------
ID3 v2.4:
title: Wake Up World            artist: Nonpoint
album: Vengeance                year: 2007
track: 1                genre: Metal (id 9)

FRONT_COVER Image: [Size: 14004 bytes] [Type: image/jpeg]
Description: 

```

```

-------------------------------------------------------------------------------
Time: 10:42     MPEG1, Layer I  [ 96 kb/s @ 44100 Hz - Stereo ]
-------------------------------------------------------------------------------
ID3 v2.4:
title: Don't Stop               artist: Fleetwood Mac
album: Rumours          year: 1977
track: 4                genre: Rock (id 17)

```

---

### Post by McNils on 2011-11-28
compare it to one that works.

---

### Post by jlacroix on 2011-11-28
> **McNils said:**
> compare it to one that works.
Looks the same to me.
```

-------------------------------------------------------------------------------
Time: 03:26     MPEG1, Layer III        [ 320 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
ID3 v2.4:
title: Bullet With A Name               artist: Nonpoint
album: To The Pain              year: 2005
track: 1                genre: Metal (id 9)
Publisher/label: Bieler Bros. Records

FRONT_COVER Image: [Size: 9920 bytes] [Type: image/jpeg]
Description: thumbnail


```

---

### Post by jlacroix on 2011-11-29
Apparently this is a problem with Android. I'm still open to solutions, but I'm being told in the Android forums that this is a problem with something called the "System Scanner."

---

