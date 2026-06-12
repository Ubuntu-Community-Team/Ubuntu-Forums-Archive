---
title: "Wireless And Driver"
date: 2010-05-13
forum: General Help
---

### Post by HACKER1993 on 2010-05-13
I know this isn't the place for this but i am having trouble with my wireless with Linux mint but ubuntu forums feels more friendly and knowledgeable about these problems the wireless adapter in question is a HornetTek HT-H5DN i have been to the company website they do have a driver but i can't compile it due to lack of experience it runs on a Ralink 2720 driver

---

### Post by Woody1987 on 2010-05-13
Try 
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic 
```
This will install some backported drivers which may or may not support your card. Once installed, reboot.

---

### Post by HACKER1993 on 2010-05-13
I'm Running k9.10 karmic koala:)

---

### Post by HACKER1993 on 2010-05-14
could anyone check to see if the compiling instructions work for it the drivers on hornet tek's website
:-P

---

### Post by HACKER1993 on 2010-05-17
can anyone help me compile this driver?:confused:

---

