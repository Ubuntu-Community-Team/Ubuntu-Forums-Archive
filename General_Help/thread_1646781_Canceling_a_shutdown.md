---
title: "Canceling a shutdown"
date: 2010-12-16
forum: General Help
---

### Post by wikwanderlust on 2010-12-16
Hi. Not a big problem here, more curious than anything else. I usually use my computer to play internet radio while I fall asleep, then have it shut down with the shutdown command after 120 minutes. 99 percent of the time, that works out just fine, but I'd like to be able to cancel the impending shutdown in case I need to. Again not really a big problem, but I would think there would be a way to do it. Thanks in advance.

---

### Post by TeoBigusGeekus on 2010-12-16
What about
```
sudo killall shutdown
```
?

---

### Post by stinkeye on 2010-12-16
```
sudo shutdown -c
```

---

### Post by wikwanderlust on 2010-12-16
That did it. Thank you very much TeoBigusGeekus. Usually I do try to find answers without posting, but I couldn't for this one. I've used Linux off and on for two years now, you'd figure I'd be a little better at this by now...Thanks again.

---

### Post by wikwanderlust on 2010-12-16
stinkeye's method works as well. Am I really this bad at this?:frown: Thank you stinkeye.

---

### Post by stinkeye on 2010-12-16
> **wikwanderlust said:**
> stinkeye's method works as well. Am I really this bad at this?:frown: Thank you stinkeye.

You can usually find what your looking for in the man pages.
```
man shutdown
```

---

### Post by wikwanderlust on 2010-12-16
I will keep that in mind for future reference. Thanks again.

---

