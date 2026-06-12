---
title: "Warsow: mouse not detected on game launch"
date: 2011-11-26
forum: General Help
---

### Post by promet on 2011-11-26
Hello,

I'd been having problems getting my mouse to be detected by Warsow on launch. I discovered the following setting in my "~/.warsow-0.5/config.cfg file: 

```
seta in_dgamouse "1"
```

This appeared to be the setting that was tying up my mouse. I set it to zero, as such:

```
seta in_dgamouse "0"
```

And now it appears to be working. I hope this is of some help to someone.

Cheers!

---

