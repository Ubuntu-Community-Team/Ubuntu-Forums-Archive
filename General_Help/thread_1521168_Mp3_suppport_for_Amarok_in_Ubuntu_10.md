---
title: "Mp3 suppport for Amarok in Ubuntu 10"
date: 2010-06-30
forum: General Help
---

### Post by kantu on 2010-06-30
I am not able to play mp3 files in Amaraok in Ubuntu 10.04.
It can play m4a files .
Other players can play mp3 files without any problem,
I tried installing libxine1-ffmpeg and kubuntu-restricted extras and ubuntu restricted extras ,all are installed but theres no mp3 support
This is the error message i get ,
```
Phonon claims it cannot play mp3 files
```

---

### Post by x C0MMAND0 x on 2010-06-30
Try installing the following:

phonon-backend-xine
libxine1-ffmpeg

If that doesn't work see [this thread]("http://ubuntuforums.org/showthread.php?t=1439468")

---

### Post by kantu on 2010-06-30
> **x C0MMAND0 x said:**
> Try installing the following:

phonon-backend-xine
libxine1-ffmpeg

If that doesn't work see [this thread]("http://ubuntuforums.org/showthread.php?t=1439468")

thanks that worked out perfectly

---

### Post by x C0MMAND0 x on 2010-06-30
No problem, was it the first part that worked or was it the second thread?  That way people who search for this problem might stumble upon this thread and no what to do. Don't forget to mark the thread as solved.

---

### Post by Jeffa on 2010-07-12
kantu, 

please oh please do what x Commando x suggested in the last post. That kind of thread maintenance helps the community so much. I'm currently having the same problem as you were, and I'm sure others will be searching for threads like this.

Please give back to the community that helped you!

Thanks!

---

### Post by merlin_ie on 2010-10-31
> **Jeffa said:**
> kantu, 

please oh please do what x Commando x suggested in the last post. That kind of thread maintenance helps the community so much. I'm currently having the same problem as you were, and I'm sure others will be searching for threads like this.

Please give back to the community that helped you!

Thanks!

well, I'd like to say that it was ```
libxine1-ffmpeg
``` that did it for me so thanks

---

### Post by hobie on 2011-01-18
It worked for me too.  Funny thing is, when I installed Maverick, it worked, but after subsequent updates, it stopped working.  All is well now, though. 

Thanks!

---

