---
title: "File properties from terminal"
date: 2009-10-17
forum: General Help
---

### Post by AndrewSimoes on 2009-10-17
I specifically want to be able to see audio-video file properties from the terminal.
Not ls -l or ls-lh
The file command only prints the type of file.

---

### Post by OpenGuard on 2009-10-17
For audio/video files - ffmpeg ( available from repos ).

```
ffmpeg -i sound.mp3

```

---

