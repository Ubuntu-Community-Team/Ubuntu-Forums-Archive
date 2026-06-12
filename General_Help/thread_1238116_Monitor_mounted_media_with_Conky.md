---
title: "Monitor mounted media with Conky"
date: 2009-08-12
forum: General Help
---

### Post by acrocephalus on 2009-08-12
Hello!
I usually mount a Windows device with my Ubuntu 9.04. The mounting point is:
```
/mnt/windows_sylvia/
```.
I would like to monitor this mounted device, thus I write this code into my .conkyrc:
```
${if_mounted /mnt/windows_sylvia/}
Sylvia: ${alignr}${fs_free /mnt/windows_sylvia/} / ${fs_size /mnt/windows_sylvia/}
${fs_bar 4 /mnt/windows_sylvia/}${endif}
```
However, when I run conky it doesn't detect the media even if it is mounted. How can I do this?
Best!

Dani

---

