---
title: "Nach DivX konvertieren"
date: 2011-09-17
forum: General Help
---

### Post by zensor on 2011-09-17
Hallo, ich habe einen Festplattenrekorder, der kann angeblich DivX abspielen, sowohl von CD als auch von USB... aber ich habe es bisher nicht hinbekommen, dass er die Dateien auch abspielen kann.

In der Anleitung ist folgendes definiert

DivX
Wiedergabefähige Medien [-R] [-R]DL] [CD] [USB]
  
Dateiformat DivX
           &#8805;Die Dateien müssen die
             Erweiterung “.DIVX”, “.divx”,
                    “.AVI” oder “.avi” aufweisen.
Ordneranzahl Maximal erkennbare Anzahl von Ordnern: 300
            (einschließlich Hauptordner)
Dateienanzahl Maximal erkennbare Anzahl von Dateien§1: 200
Unterstützte Zertifiziert für das DivX Home Theater Profile.
Versionen Video
  – Anzahl von Streams: Maximal 1
  – Codec: DIV3, DIV4, DIVX, DV50
  – Bildgröße: 32 x 32 bis 720 x 576
  – Bilder pro Sekunde (FPS): Maximal 30
                Audio
  – Anzahl von Streams: Maximal 8
  – Format: MP3, MPEG, AC3
  – Surround Sound: AC3 ist möglich. MPEG-
                   Mehrkanalton wird auf zwei Kanäle reduziert.


Meine Idee war jetzt, die vorhandenen Dateien per ffmpeg umzuwandeln.
Nach der Literatur einiger Internetquellen kam ich zu:
ffmpeg -i DVD_2008.flv -vtag DIVX -f avi -vcodec mpeg4  DVD_2008.divx

es funktioniert aber NICHT (die Datei wird dann zwar erkannt vom Player, kann aber nicht abgespielt werden - auf dem Rechner allerdings schon) & so ganz hat es mir eh nicht gefallen, insbesondere da der Codec (MPEG4) nicht oben in der Liste ist. Aber unter "-formats" konnte ich nichts besseres finden.

Irgendeine Idee, was ich gerade übersehe. Also insbesondere, wie kann ich eine Datei mit oben genannten Codecs konvertieren?

---

### Post by Rubi1200 on 2011-09-17
zensor,
this is an English language forums. I suggest you either find a support forum in German or try and translate your post as best as possible.

---

### Post by TeoBigusGeekus on 2011-09-17
You're lucky that I can speak german...

I think your problem is that you haven't specified an audio codec.
Try with this
```
ffmpeg -i DVD_2008.flv -vtag divx -vcodec mpeg4 -acodec libmp3lame DVD_2008.avi
```

EDIT: Alright Rubi...
EDIT2: @zensor - avi is a container for mpeg4, it doesn't have to be listed in the dvd's formats.

---

### Post by Rubi1200 on 2011-09-17
@TeoBigusGeekus; I was just relating a general policy regarding posting in other languages in the main forums. If you can help the OP that is great and much appreciated.

@zensor; try the suggestion by TeoBigusGeekus

---

### Post by TeoBigusGeekus on 2011-09-17
Since the thread stays, I'll try to describe the problem:
Zensor has a device that can play divx (either from CD or USB). 
The device's manual defines that it can play files with a .divx/.DIVX or .AVI/.avi extension, with the specs described by Zensor (fps, resolution, codecs, etc.)
Zensor tried to convert an flv file with the ffmpeg command he found in the internet, but the device, although listing the file, does not play it.
He then proceeds to explain that it is natural, because the manual doesn't specify mpeg4 as a legitimate codec, but he couldn't find anything more appropriate searching in the --formats option of ffmpeg.
He ends his post asking for advice.

PS: I hope my explanation was more understandable than the original post :P

---

### Post by zensor on 2011-09-28
Thank you, a lot, I'm going to try the suggestion....
Shortform in English: I want some flv-movie converted to DivX, which should be accepted by my Player. How do I need to include the codecs into the ffmpeg-command?

Video
&#8211; Codec: DIV3, DIV4, DIVX, DV50
Audio
&#8211; Format: MP3, MPEG, AC3

But I think the suggestion that was already given should help.

---

### Post by TeoBigusGeekus on 2011-09-28
Out of curiosity: did I get the translation right?

---

