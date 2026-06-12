---
title: "CPU usage 100% but process manager only shows 3%"
date: 2006-06-15
forum: General Help
---

### Post by djsamsel on 2006-06-15
i'm running the k-7 kernel and this evening my cpu usage shows 100% on the system monitor, but when i look at the processes it's ony 3to 10%. the system feels as responsive as ever, so i'm guessing the system monitor is wrong. any ideas?

---

### Post by djsamsel on 2006-06-15
bump

---

### Post by graigsmith on 2006-06-15
make sure to click view, all processes.

if that doesn't work, type top in the command prompt.  it will show you the programs that are using the most cpu usage.

---

### Post by djsamsel on 2006-06-16
thanks, that was it. there was a nano session running. killed it and all is back to normal.

---

