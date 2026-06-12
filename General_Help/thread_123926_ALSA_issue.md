---
title: "ALSA issue"
date: 2006-01-31
forum: General Help
---

### Post by louis_nichols on 2006-01-31
Hi! I am having this problem with alsa. Various applications throw out this error:

```
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```

For example, when I run aconnect.

Apps like xmms, mplayer, vlc, totem work though, but I am having some difficulties under wine (which also shows that erros) and I'm thinking it's because of this. Also, I can't seem to get surround sound. I set alsa to 4 channnels for example and run

```
speaker-test -c 4
```

but I can only hear the front speaker, while the others are quite. I was able to get it right using qjackctl, though. I must admit sound under Linux still has many enigmas for me, anyway

Does anybody know what this error is and how I can solve it? THX

---

