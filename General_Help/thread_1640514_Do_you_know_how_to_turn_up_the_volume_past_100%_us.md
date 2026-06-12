---
title: "Do you know how to turn up the volume past 100% using keyboard hot keys?"
date: 2010-12-07
forum: General Help
---

### Post by Aitaix on 2010-12-07
So my volume doesn't go load enough when it is at 100%, I have to  manually turn it up in sound preferences.  I'm lazy and just want to  push the volume button on my keyboard and have it go up too....the  maximum. HOW HOW HOW!

---

### Post by hackerseraph on 2010-12-11
Bump

---

### Post by Aitaix on 2011-02-14
and another

---

### Post by vladverzeni on 2011-09-23
also interested!

---

### Post by stinkeye on 2011-09-23
On my machine this command will set my volume up full.
```
pacmd set-sink-volume 1 100000
```

If the volume is below the 100% mark in sound preferences,
the first time the command is run it takes the sound to the 100% mark.
A subsequent running of the command takes the volume to full.

You could add to keyboard shortcuts using as the command
```
bash -c "pacmd set-sink-volume 1 100000 && pacmd set-sink-volume 1 100000"
```


Could also use this command in startup applications to set volume to full at boot.
```
bash -c "sleep 5 && pacmd set-sink-volume 1 100000 && pacmd set-sink-volume 1 100000"
```

---

