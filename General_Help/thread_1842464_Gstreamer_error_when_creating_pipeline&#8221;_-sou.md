---
title: "Gstreamer error when creating pipeline&#8221; -soundconverter"
date: 2011-09-11
forum: General Help
---

### Post by aninona on 2011-09-11
1104 ubuntu


i'm tryin to convert music using soundconverter[worked perfectly few days ago] 
It happens when I try converting mp3 to itself[just changing the Hz].
the output through terminal:
Cannot set permission on '/home/a/Desktop/mus.mp3'

when firing convert key it outputs: "Gstreamer error when creating pipeline could not link audioconvert1 to lame0"

have tried to reinstall libpipe and gstreamer with no success What should I do? Thanks

---

### Post by aninona on 2011-09-11
bump

---

### Post by nothingspecial on 2011-09-11
Try to bump posts ever 24 hours please.

Do you have all the relevant gstreamer packages installed?

---

### Post by aninona on 2011-09-12
It happens when I try converting mp3 to itself[just changing the Hz].
 the output: 
Cannot set permission on '/home/a/Desktop/mus.mp3'

---

### Post by sisco311 on 2011-09-12
Are you logged in as user **a**? Also please post the exact command you use and the exact error message.

Oh, and fixed the thread title. ;)

---

### Post by aninona on 2011-09-12
hi sisco thanks for the fixing.:-)
I am logged as a.
here is the terminal output
```

a@a:~$ sudo soundconverter
[sudo] password for a: 
SoundConverter 1.5.4
  using Gstreamer version: 0.10.32
  using gio
  using 2 thread(s)

(soundconverter:4491): libglade-WARNING **: could not convert string to type `GValueArray' for property `authors'

(soundconverter:4491): libglade-WARNING **: could not convert string to type `GValueArray' for property `documenters'
/usr/local/bin/soundconverter:2859: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  glade = gtk.glade.XML(GLADE)
giosrc location="file:///home/a/Music/Adele%20-%20Rolling%20in%20the%20Deep.mp3" ! typefind name=typefinder ! fakesink

Queue done in 0.018s (1 tasks)
giosrc location="file:///home/a/Music/Adele%20-%20Rolling%20in%20the%20Deep.mp3" name=src ! decodebin name=decoder ! fakesink

Queue done in 0.359s (1 tasks)
giosrc location="file:///home/a/Music/Adele%20-%20Rolling%20in%20the%20Deep.mp3" name=src ! decodebin name=decoder ! audioconvert ! audioresample ! audio/x-raw-float,rate=43200 ! audioconvert ! lame quality=2 vbr=4 vbr-max-bitrate=128 vbr-quality=9 ! xingmux ! id3v2mux  ! giosink location="file:///home/a/Desktop/Adele/Unknown%20Album/Rolling%20in%20the%20Deep.mp3"
Cannot set permission on '/home/a/Desktop/Adele/Unknown Album/Rolling in the Deep.mp3'

Queue done in 1.626s (1 tasks)


```

---

