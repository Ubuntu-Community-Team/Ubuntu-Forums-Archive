---
title: "OMG! This cant be good"
date: 2006-02-17
forum: General Help
---

### Post by andy5667 on 2006-02-17
I have just been told that i cant install drivers because ubuntu dosen't have GCC. is there any way around this?

---

### Post by firetux on 2006-02-17
install gcc:mrgreen: 
















```

sudo apt-get install build-essential
```

---

### Post by Protex on 2006-02-17
You can actually download the GCC from the repos if I'm not mistaken.

'sudo apt-get install build-essential gcc gcc-3.3 gcc-4.0'

There might be some dependency issues, or different GCC's you may need to download, I'm not sure, but try this at least.

---

