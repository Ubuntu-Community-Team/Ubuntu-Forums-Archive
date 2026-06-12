---
title: "audio plugin problems"
date: 2009-11-30
forum: General Help
---

### Post by ravidev17 on 2009-11-30
i have installed ubuntu 9.10 but i am unable to play any sort of video/audio file...i can hear sound on startup...plz help:confused:

---

### Post by Elktro on 2009-12-01
If you are trying to play restricted formats like mp3 or wmv, you need to install the codecs by running this command in terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Due to legal reasons ubuntu doesn't support those natively.

See more information at
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

