---
title: "copy/delete files from an ext2 binary img (win32)"
date: 2010-05-17
forum: General Help
---

### Post by rbhkamal on 2010-05-17
HI!

I've been trying for a while now to find a bug-free utility that let's me copy files to an ext2 binary image from windows.. so far no luck.

For security reason, the tool cannot depend on a driver.. :(

I've tried so far the following:
explore2fs (pascal): Doesn't support writing to image files (like most of the utils out there)

ltools: Does everything except that its buggy. After doing a few write operations (mkdir, cp ) the image will become corrupted. However, if I limit the write to a single file ltools seem to be OK with it


I would really appreciated it if someone can help me to accomplish my goal. I could use anything (C/C++ libraries, utilities , dlls ... etc )


Also, if I were to write my own C/C++ library. Where should I start? Which documentations can point me to the way ext2 was implemented?


Thanks!

---

### Post by viralmeme on 2010-05-17
Some solutions are mentioned here ..

[http://www.linux.com/community/forums?func=view&catid=17&id=5800](http://www.linux.com/community/forums?func=view&catid=17&id=5800)

---

### Post by rbhkamal on 2010-05-17
lol... that is actually my post too. linux.com didn't give me any new tools to try. The only suggestion that were worth it are the Linux VM + Samba share.

I need just a single/simple exe file that does the job (if there is any)

---

### Post by rbhkamal on 2010-05-19
bumpy

---

### Post by rbhkamal on 2010-05-27
another bump,

please help

---

