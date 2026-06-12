---
title: "ffmeg enabling shared library"
date: 2006-02-13
forum: General Help
---

### Post by gmclachl on 2006-02-13
Is it possible to use apt-get to install ffmpeg with the --enable-shared option. I have tried installing from source but i get 

  common.h:67: error: array type has incomplete element type
  common.h:71: error: array type has incomplete element type

 if anyone could point me in the right direction it would be great
 Thanks
 G

---

### Post by gmclachl on 2006-02-13
Sorted my problem, I grabbed the latest from CVS and it built fine.

 George

---

