---
title: "How to uninstall and re install ubuntu 10.04?"
date: 2010-05-21
forum: General Help
---

### Post by Dallas.Dude on 2010-05-21
Hello friends,
                   I installed ubuntu 10.04 to my new laptop recently but i installed from outside windows. It is creating problems. I cant open windows after using linux, its not booting up, displaying message like OS not found. I read some threads and i fixed it by inserting live CD. Again i am using only Ubuntu and i have fear if i open windows again i will face similar problem. I asked my friend he said to install ubuntu inside windows. But i dont know how to do it ? Please help.. Is it possible to uninstall ubuntu without touching windows and reinstall from inside windows. Thanks

---

### Post by TheGnomeOfMetal on 2010-05-21
how did you install it the first time?

---

### Post by elliotn on 2010-05-21
if u installed via wubi uninstall it as normal bt if its a full install then format

---

### Post by Dallas.Dude on 2010-05-21
> **elliotn said:**
> if u installed via wubi uninstall it as normal bt if its a full install then format
Dear elliton?
Is there any thread which give details of how to format? I didnt install using wubi..

---

### Post by bodhi.zazen on 2010-05-21
You do not need to uninstall Ubuntu then, simply re-install it. When you re-install your partitions will be formatted, well swap and / at least.

To answer your most recent question, use gparted if you wish to format a partition with a graphical application. gparted in not installed by default, install it via the software center, synaptic, or command line.

```
sudo apt-get -y install gparted
```

---

