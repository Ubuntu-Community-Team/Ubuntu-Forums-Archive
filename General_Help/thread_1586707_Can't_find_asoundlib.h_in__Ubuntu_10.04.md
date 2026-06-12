---
title: "Can't find asoundlib.h in  Ubuntu 10.04"
date: 2010-10-02
forum: General Help
---

### Post by SaberCat on 2010-10-02
Hi,
I recently installed Ubuntu 10.04 on a new machine. I am now trying to compile a program that uses the -lasound library that I wrote on an Ubuntu 8.04 machine. When I try to compile it I find that the compiler (gcc) can't find include file asoundlib.h. On the 8.04 machine I had installed alsa-base, alsa-utils and alsa-source. The asoundlib.h file was then in /usr/include/alsa. I have the same modules installed on the new 10.04 machine but that directory is not present. Can you tell me what modules I need to install and where my program should look for asoundlib.h?

Thanks...!

---

### Post by SaberCat on 2010-10-02
Found solution to this...
I needed to install package libasound2-dev. Then the /usr/include/alsa directory was installed and it contained file asoundlib.h.My program then compiled correctly.

Problem solved...thanks anyway...

---

### Post by nikkizeng on 2011-12-12
I met the same problem. solved with the same solution. Thanks for sharing!

---

