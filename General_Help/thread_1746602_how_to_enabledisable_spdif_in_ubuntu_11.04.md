---
title: "how to enable/disable spdif in ubuntu 11.04"
date: 2011-05-02
forum: General Help
---

### Post by creatxr on 2011-05-02
how to enable/disable spdif in ubuntu 11.04 ?
after install ubuntu 11.04 it turn on spdif automatic.
but i dont need it.
how can i disable spdif?
thanks.

---

### Post by papibe on 2011-05-02
You can try going to System -> Preferences -> Sound, or the volume icon on then Sound Preferences.

Another way would be muting that output on alsamixer:
```
$ alsamixer
```

I hope it helps.

---

### Post by creatxr on 2011-05-02
thanks.
i can trun off in alsamixer now.
but when i switch user or restart, it trun on again.
how can i trun off it permanant?

---

### Post by papibe on 2011-05-02
Right after executing alsamixer, run this:
```
$ alsactl store
```
If that doesn't work, try running it as root next time:
```
$ sudo alsactl store
```
Good Luck!

---

