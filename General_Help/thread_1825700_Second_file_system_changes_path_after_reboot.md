---
title: "Second file system changes path after reboot"
date: 2011-08-15
forum: General Help
---

### Post by blow69 on 2011-08-15
Hey in there. A few days I used the wubi installer to install Ubuntu over Windows. This I did on my C:\ drive. I also have another partition, the X:\ which now is my D:\ drive after I used the gparted live cd to give the system partition more free space.

No problems so far. 

But now, when I use Clementine Player, I see that it cannot find any of my songs in my library and Deluge has to 'check' my downloads every time I open it after a reboot. My theory is that the folder inside /media/, which contains the file system gets a new name (a 16 digit capital letter/number name) every time I reboot my computer - or maybe every time I use Windows and then Ubuntu again? It's pretty annoying, and I hope some of you can help me.

Peace!

---

### Post by blow69 on 2011-08-15
Okay, I found out the path probably doesn't change, but both Clementine and Deluge have problems locating their files and I can't seem to understand why since the file system is mounted instantly at startup.

---

