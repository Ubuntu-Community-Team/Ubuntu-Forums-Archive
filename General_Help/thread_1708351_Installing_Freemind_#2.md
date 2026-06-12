---
title: "Installing Freemind #2"
date: 2011-03-16
forum: General Help
---

### Post by cpgos on 2011-03-16
I have recently installed Freemind 0.9.0 RC 6 via Synaptic but find on running Freemind that it cannot get past the point where it says "Load Maps".

Could anybody suggest what the problem may be?

Best regards,
cpgos

---

### Post by knattlhuber on 2011-04-17
It's probably not working with your current Java installation. (If you start freemind from a terminal you'll see the error messages.) 

```
sudo apt-get install openjdk-6-jdk
``` worked for me (YMMV)

---

