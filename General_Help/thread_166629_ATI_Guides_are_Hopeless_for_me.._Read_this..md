---
title: "ATI Guides are Hopeless for me.. Read this."
date: 2006-04-26
forum: General Help
---

### Post by Dakaru on 2006-04-26
Ok, so I followed this guide to the letter: 

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)

(The Lower half)

And when I get to the part where I need to put it into the kernal with this command 

"sudo module-assistant build,install fglrx-kernel" 

The piece of shit says "Incorrect Kernal Headers" and wont let me do it. How do you fix this? ATI Drivers are important.

---

### Post by towsonu2003 on 2006-04-26
please copy paste the output of the following:
```

ls -l /usr/src
uname -r

```

---

