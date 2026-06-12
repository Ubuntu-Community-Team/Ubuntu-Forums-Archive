---
title: "Problem starting Audacity"
date: 2006-04-13
forum: General Help
---

### Post by pmilin@ptt.yu on 2006-04-13
Hi!
When I start Audacity, I receive an error message:

==========================================

There wan an error initiallizing the audio i/o layer.
You will not be able to play or record audio.

Error: Host error.

==========================================

Does anybody know what can I do to fix that problem?

Sincerely,
P. Milin

---

### Post by barbarossa on 2006-04-13
You could try:

```
killall esd
```

first. Alternatively run the program from the command line. Works for me.

---

