---
title: "Restart X = No Menu Just Desktop"
date: 2011-06-24
forum: General Help
---

### Post by poptisse on 2011-06-24
Hello All,

I just enabled ctrl alt backspace to restart X - as I had edited the xorg.conf to fix a screen tearing issue. I pressed ctrl alt backspace - everything went black and came back and all i can see is my desktop with two items i had on my desktop previously,
I have no menu absolutely nothing so can't run terminal or any piece of software....

I added

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

to the end of xorg.conf as a way to fix the screen tearing and it just produced the above error - to which has now been fixed by removing those lines. I have read all over by adding those lines it fixes screen tearing as everything else seems to fail for me.

---

