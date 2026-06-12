---
title: "Has anyone found a way to get song info from Clementine into conky?"
date: 2010-10-22
forum: General Help
---

### Post by GrdLock02 on 2010-10-22
I've been messing with it and haven't found a good way to script it in Conky.

Has anyone else found anything?

---

### Post by gslug79 on 2010-11-17
Hello,

I too was wondering how to do this and came across this bash script:

```
#!/bin/bash



TRACK=`qdbus org.mpris.clementine /TrackList \

org.freedesktop.MediaPlayer.GetCurrentTrack`



qdbus org.mpris.clementine /TrackList \

org.freedesktop.MediaPlayer.GetMetadata $TRACK \

| sort -r | egrep "^(title:|artist:)" | sed -e "s/^.*: //g" \

| sed -e ':a;N;$!ba;s/\n/ - /g' | head -c 45
```

Let's call this conky-clementine. Save it wherever you like (I have a folder /home/username/scripts) and make it executable:

```
chmod +x conky- clementine
```

You can test that it works by calling it from the command line:

```
./conky- clementine
```

Finally to get conky to display the output, add this line to your .conkyrc

```
${execi 10 /path to script/conky-clementine}
```

The number 10 is the update interval in seconds.

---

### Post by VastOne on 2010-12-14
You can find the way from Conky-PitStop [_[COLOR="Blue"]here under the tab The Code[/COLOR]_]("http://conky-pitstop.wikidot.com/g10ii:g-2010-ii")

---

