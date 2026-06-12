---
title: "Xorg crash from firefox"
date: 2010-09-30
forum: General Help
---

### Post by aust77 on 2010-09-30
I am running Lubuntu 10.04 on my desktop (check my sig for stats), My desktop has an intel graphics chip, part of the 18xx series, so it has had some incompatibilities with both Ubuntu (I switched only a week ago to Lubuntu) and Lubuntu.
After various forms of Xorg crashes I was able to stabilize Ubuntu, but due to speed issues I switched to Lubuntu. The speed is fine but I am currently unable to boot into the latest kernel, 2.6.32-25, so using StartUp Manager I automatically boot into 2.6.32-21 (the first available kernel). 
The system is stable and works fine for a variable period of time. However, my family members tell me the computer crashes in firefox when simply browsing. Upon checking it out I notice a flashing white line at the top corner of the screen. I can even type and the text appears on the screen. However, I have no choice but to hold down the power button to manually shut down the computer.
I can wait until 10.10, but I am unsure of whether or not Lubuntu will be released on the 10th like Ubuntu or late in the month.
I gracefully appreciate any assistance,

aust77

EDIT: 
I am aware of the wiki page discussing this issue and have tried several of the fixes. They have not worked so far. I will post the results of lspci | grep VGA if needed.

---

### Post by aust77 on 2010-10-01
bump

EDIT: It also happened in Chrome today.

---

### Post by bluefoot on 2010-10-02
big crash here too.
when I close it.

It also corrupted my profile files...

It was after the last update.

---

### Post by SteveDee on 2010-10-08
> **aust77 said:**
> ...However, my family members tell me the computer crashes in firefox when simply browsing.....

You may find a suitable workaround here: [http://ubuntuforums.org/showthread.php?t=1470930&page=2](http://ubuntuforums.org/showthread.php?t=1470930&page=2)

Suggest you start with these two:-
 - go to gstreamer-properties and set the video Default Output Plugin to: X Window System (no Xv)
 - try the rt kernel

---

### Post by aust77 on 2010-10-08
> **SteveDee said:**
> You may find a suitable workaround here: [http://ubuntuforums.org/showthread.php?t=1470930&page=2](http://ubuntuforums.org/showthread.php?t=1470930&page=2)

Suggest you start with these two:-
 - go to gstreamer-properties and set the video Default Output Plugin to: X Window System (no Xv)
 - try the rt kernel

I appreciate the suggested solution. Since then I have switched from 10.04 to the Lubuntu 10.10 Beta 2. The users of the computer say the browser works flawlessly. Your suggestion is appreciated nonetheless.

Cheers,


aust77

---

