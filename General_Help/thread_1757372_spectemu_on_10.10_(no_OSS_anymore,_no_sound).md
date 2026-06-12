---
title: "spectemu on 10.10 (no OSS anymore, no sound)"
date: 2011-05-13
forum: General Help
---

### Post by akos.maroy on 2011-05-13
I wonder if anyone has a solution to this issue: spectemu and xspectemu expect an OSS sound interface, with is not available anymore on recent ubuntu distros (say 10.10 or later). thus there is no sound....

is anyone aware of an ALSA or Pulse Audio capable spectemu?

---

### Post by nicktime on 2011-08-14
Just to fill knowledge base.
There's alsa wrapper, which can handle this:
```
sudo apt-get install alsa-oss
aoss xspect
```and you get sound.

---

