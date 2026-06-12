---
title: "K3b MP3 Support"
date: 2011-08-04
forum: General Help
---

### Post by fleamour on 2011-08-04
k3b seems to like my hardware so I am sticking with it.  Can it be tweaked to handle MP3s?

---

### Post by ron999 on 2011-08-04
> **fleamour said:**
>  Can it be tweaked to handle MP3s?
Yes.
Install the extra codecs:-
```
sudo apt-get install libk3b6-extracodecs
```

Then make adjustments in:-
Settings > Configure K3b > Plugins

---

### Post by fleamour on 2011-08-04
Ah, k, thx.

Will try that tomorrow.  Will save converting to FLAC each time.

---

### Post by fleamour on 2011-08-07
Where will I search for MP3 plugin?  Not seeing it presented under Settings > Configure K3b > Plugins...

---

### Post by fleamour on 2011-08-07
Seems to be automatically configured, thanks!!!

:D:biggrin::D

---

### Post by ron999 on 2011-08-07
> **fleamour said:**
> Where will I search for MP3 plugin?  Not seeing it presented under Settings > Configure K3b > Plugins...

Hi
The name of the mp3 plugin is 'K3b MAD Decoder'.

---

### Post by crazypiglady on 2012-10-16
> **ron999 said:**
> Yes.
Install the extra codecs:-
```
sudo apt-get install libk3b6-extracodecs
```

Then make adjustments in:-
Settings > Configure K3b > Plugins

Great Answer. Didn't even need to make the adjustments. Thanks. :)

---

