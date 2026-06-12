---
title: "Firefox crashes immediately after starting in Lucid Lynx"
date: 2010-05-01
forum: General Help
---

### Post by bruntie2 on 2010-05-01
After upgrading to Lucid Lynx firefox doesn't seem to want to work - immediately after starting it simply closes. This is the first time this has happened so I think it must be something to do with upgrading. I have tried rebooting a few times but it makes no difference, and I had to install Arora to get on the internet. Does anyone have any idea how to stop this? I'm using a Vaio laptop if that helps.

---

### Post by wojox on 2010-05-01
Start firefox from the terminal and see what errors it gives.

---

### Post by bruntie2 on 2010-05-01
It says "Attempting to load the system libmoon 
Segmentation fault"

---

### Post by wojox on 2010-05-01
Try in a terminal:

```
sudo apt-get purge moonlight-plugin-core moonlight-plugin-mozilla
```

---

### Post by bruntie2 on 2010-05-01
Thanks, problem solved!

---

### Post by wojox on 2010-05-01
Cool, your welcome.

---

### Post by jgkellt001 on 2010-05-16
Excellent fix. Thanks very much, I have spent 3 weeks trying to solve this problem, ever since upgrading to 10.04. Other browsers are OK, but Firefox has got a bit of meat in it! Typical, Moonlight has a Microsoft connection!

---

