---
title: "Standalone Openbox soundproblems."
date: 2006-06-26
forum: General Help
---

### Post by Rezon Mero on 2006-06-26
I know the answer to this probably evades me because of my total lack of skill. But I can't figure it out myself at the moment, nor can I find the answer at the internet.

After having installed openbox, and configured it for running stand-alone. I am discovering that the playback of sound somehow is disabled (it works fine in the standard Gnome config). This is probably just some background process I have to enable in the .xsession, but which or in every other case, what?

I would be extremely gratified if you could tell me. 

Sincerly Yours.
S.V.Welling 3.

---

### Post by johannes on 2006-06-28
I'm not sure it helps, but try running:

```
amixer set Master 75 unmute
amixer set PCM 75 unmute
```

---

