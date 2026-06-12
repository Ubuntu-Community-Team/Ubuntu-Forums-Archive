---
title: "How to get technical info about movie file."
date: 2011-03-24
forum: General Help
---

### Post by tommmmmm on 2011-03-24
From command line. Preferably without the use of X.

When opening kmplayer and then 'info about media' I get all the data i need.

Exact frame rate, aspect ratio, codecs for audio/video, runtime, resolutio etc. To put simply every technical info about movie file.

So how can I dump it to a file? From console?

---

### Post by SeijiSensei on 2011-03-24
You can use mplayer from the command line like this:

```
mplayer -identify -frames 0 /path/to/file.mkv
```

---

