---
title: "mplayer problem"
date: 2010-08-15
forum: General Help
---

### Post by vaskark on 2010-08-15
Mplayer has recently stopped working for me. At the command line I get this error:

```
mplayer: relocation error: mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference
```

Any help would be appreciated. Thanks.

---

### Post by mc4man on 2010-08-15
That error is fairly typical if mplayer is using shared ffmpeg libs which are incompatible.
The default lucid mplayer does use the system installed ffmpeg libs - are you using any ppa's?

---

### Post by vaskark on 2010-08-15
Good thinking!

---

