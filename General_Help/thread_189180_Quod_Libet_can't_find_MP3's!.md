---
title: "Quod Libet can't find MP3's!"
date: 2006-06-04
forum: General Help
---

### Post by heinlein on 2006-06-04
Hello!

After what seems to be a relative easy upgrade to 6.06 (compared to updating to 5.10), I decided to install the new version of Quodlibet (0.20.1). The new vesion will not load any of my MP3's and, according to the start-up text, only supports flac, oggvorbis, wav. I have installed all gst-plugins (I think) and then re-installed them, without any help. I can play MP3's in any other program that I have tested.

I found an old thread (locked, so I couldn't post there):
[http://ubuntuforums.org/showthread.php?t=167723&highlight=quodlibet](http://ubuntuforums.org/showthread.php?t=167723&highlight=quodlibet)

When I open up Quod Libet it only shows my (few) ogg-files and it completely ignores all MP3-files. The same for Ex Falso.

```
gst-launch-0.10 filesrc location=/path/to/mp3file ! mad ! audioconvert ! gconfaudiosink
```
Does work without problem, but:
```
gst-launch-0.10 filesrc location=/path/to/mp3file ! mad ! audioconvert
```
or
```
gst-launch-0.10 filesrc location=/path/to/mp3file
```
gives an error-message:
```
Ställer in rörledningen till PAUSED...
Rörledningen har utfört PREROLL...
Ställer in rörledningen till PLAYING...
FEL: från element /pipeline0/filesrc0: Internt dataflödesfel.
Ytterligare felsökningsinformation:
gstbasesrc.c(1510): gst_base_src_loop (): /pipeline0/filesrc0:
streaming task paused, reason not-linked
Execution ended after 527000 ns.
Ställer in rörledningen till PAUSED...
Ställer in rörledningen till READY...
Ställer in rörledningen till NULL...
FRIGÖR rörledning...
```
and just removing MAD:
```
gst-launch-0.10 filesrc location=/path/to/mp3file ! audioconvert ! gconfaudiosink
```
gives:
```
Ställer in rörledningen till PAUSED...
Rörledningen utför PREROLL...
FEL: från element /pipeline0/audioconvert0: not negotiated
Ytterligare felsökningsinformation:
gstbasetransform.c(1395): gst_base_transform_handle_buffer (): /pipeline0/audioconvert0:
not negotiated
FEL: rörledningen vill inte utföra preroll.
Ställer in rörledningen till NULL...
FRIGÖR rörledning...
```

Anyone that have any good idea???

THX in advance (and I hope this is the right sub-forum)!
/heinlein

---

### Post by Evoreth on 2006-06-05
Did you install Mutagen?
[http://www.sacredchao.net/quodlibet/wiki/Download](http://www.sacredchao.net/quodlibet/wiki/Download)

---

### Post by heinlein on 2006-06-05
[QUOTE=Evoreth]Did you install Mutagen?
[http://www.sacredchao.net/quodlibet/wiki/Download](http://www.sacredchao.net/quodlibet/wiki/Download)[/QUOTE]

Yes, but I don't remember if it was before or after the first try to get Quod Libet to work (I tried to re-install it and remove configure-files to see if it helped, but nothing).

---

### Post by hugmenot on 2006-06-05
This has to work ```
gst-launch-0.10 playbin uri=file:///home/xxx/xxx.mp3
``` to rule a playback issue with Gstreamer out.

But Gstreamer is not related to file loading and indexing per se in QL.
There must be an installation issue (Mutagen or codecs). If QL doesn&#8217;t list MP3 support, it thinks the particular Gstreamer codecs are missing.

---

### Post by heinlein on 2006-06-05
[QUOTE=hugmenot]This has to work ```
gst-launch-0.10 playbin uri=file:///home/xxx/xxx.mp3
``` to rule a playback issue with Gstreamer out.

But Gstreamer is not related to file loading and indexing per se in QL.
There must be an installation issue (Mutagen or codecs). If QL doesn&#8217;t list MP3 support, it thinks the particular Gstreamer codecs are missing.[/QUOTE]

```
gst-launch-0.10 playbin uri=file:///home/xxx/xxx.mp3
```

works when I use /home/xxx/xxx.mp3 but not with ~/xxx.mp3.

How do I tell if a Gstreamer codec is missing? I have installed all gstreamer0.10-plugins.* and basically anything related to Gstreamer or Python that looked the least relevant.

---

### Post by Evoreth on 2006-06-05
Did you completely uninstall quodlibet before installing the new version? I once had this problem, too. Just remove the whole /usr/local/share/quodlibet directory and install it again. There might be a better way to do this, though. :p

---

### Post by heinlein on 2006-06-05
Evoreth:

Thx that worked. I just feel that I should have figured it out myself...

---

