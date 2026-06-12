---
title: "skype 2.1 beta webcam problems"
date: 2010-06-10
forum: General Help
---

### Post by Tinya_Fair on 2010-06-10
I just installed Skype for linux, but when i try to use video call the tiny screen that represents my webcam fails to load properly.

The type of webcam that i have is a logtic 1200. I used cross over to install the drivers. Can someone please help me, it would mean a lot if you could.

---

### Post by no2498 on 2010-06-10
? does the cam work at all
in/on 910 and up cheese webcam booth is/should be loaded
look for it in sound & video

try the cam in cheese

hope it come on for you

for skype 
open a terminal put this in it

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

now im only thinking you need to leave the terminal open so skype can use that

hope this helps

---

### Post by Tinya_Fair on 2010-06-10
Thanks it worked, i`m really happy now.

---

