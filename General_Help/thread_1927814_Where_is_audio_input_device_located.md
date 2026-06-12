---
title: "Where is audio input device located?"
date: 2012-02-18
forum: General Help
---

### Post by rajohns08 on 2012-02-18
is it in the /dev folder? i am trying to run julius speech recognition and it is looking for mic in /dev/dsp but i don't have anything named dsp in my /dev folder. how do i know which one is my microphone built into my laptops mobo?

---

### Post by rajohns08 on 2012-02-19
bump

---

### Post by Ms. Daisy on 2012-02-19
I'm not certain where it's located. But if you run this in a terminal, bash will tell you what the name of it is. Maybe that will help you figure out where it is:
```
sudo lspci -v | grep -A7 -i "audio"
```Or just do 
```
sudo lspci
```and you'll get a list of all your hardware that you can go through to find the microphone.

---

