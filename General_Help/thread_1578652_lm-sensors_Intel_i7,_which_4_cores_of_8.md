---
title: "lm-sensors Intel i7, which 4 cores of 8?"
date: 2010-09-20
forum: General Help
---

### Post by TheShader on 2010-09-20
Hello I'm trying to monitor the temperatures of my i7 CPU on Ubuntu 10.04 with the gnome applet. However the "sensors" detect 8 temperatures. I only have 4 cores, why does it show the temperatures of non-physical cores? It's impossible for one physical core to have 2 different temperatures isn't it? So I want to hide 4 of the temperatures but I don't know which please help, which of the 8 cores are pairs? 0-1, 2-3, 4-5, 6-7 or 0-4, 1-5, 2-6, 3-7 or something like that? :(

I think I solved this, I enabled only the first 4 cores. This means the 8 cores are paired as 0-4, 1-5, 2-6, 3-7.

---

