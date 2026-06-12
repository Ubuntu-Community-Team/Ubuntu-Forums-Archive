---
title: "usb to serial driver"
date: 2012-03-22
forum: General Help
---

### Post by lilipop on 2012-03-22
hi, 
i also want do develop USB driver for a common USB to serial adapter.
i have no clue from where to begin.
so can somebody give me some advices about from where to start?
are there some places in the internet that have some source code related to it?


i thank you in advance for the help

---

### Post by Favux on 2012-03-22
Hi lilipop,

I would think you would want to model it on one already in the kernel.  This thread discusses 2 or 3 of them:  [http://ubuntuforums.org/showthread.php?t=1780154](http://ubuntuforums.org/showthread.php?t=1780154)  They needed a patch to work with the Wacom X driver.  The Keyspan is linked in Sources on the first post.  Otherwise you'll have to search the thread for the posts.

---

