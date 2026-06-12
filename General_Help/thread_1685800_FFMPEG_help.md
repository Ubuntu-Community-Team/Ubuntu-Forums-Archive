---
title: "FFMPEG help"
date: 2011-02-11
forum: General Help
---

### Post by doperative on 2011-02-11
I have a nine minute wav file of about 48MB, how can I reduce the file size using ffmpeg, II have read various solutions but none work and I am a little confused right now ... :)

---

### Post by DanneStrat on 2011-02-11
Hi! Try this:

Place your .wav file on your desktop or another easy to find 

location.

Given that you placed the file on the desktop do this:

Open a terminal and do the following:

```


cd Desktop

ffmpeg -i thefilename.wav -fs newsizeinMB newfilename.wav
```

This will output a new file on your desktop with a new name that you specified in "newfilename".

Good luck!

---

