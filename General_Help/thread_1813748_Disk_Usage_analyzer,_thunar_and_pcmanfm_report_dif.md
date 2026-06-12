---
title: "Disk Usage analyzer, thunar and pcmanfm report different amounts of free space"
date: 2011-07-28
forum: General Help
---

### Post by jan-banan on 2011-07-28
I'm trying to figure out why thunar, pcmanfm and disk usage analyzer report different amounts of free hard disk space, do any of you have any hints to give? Thunar says 285 gb free, pcmanfm says 306 gb free and disk usage analyzer says 357gb free. 
Pcmanfm reports that my hard drive is 947.1 gb while disk usage analyzer says 909.6 gb and thunar doesnt say how much the total is. 

EDIT: Now disk usage analyzer changed and says that my harddrive is 1TB in total?

---

### Post by Wim Sturkenboom on 2011-07-28
One thing is the difference between GB and GiB. I never know what is what but computers use multiples of 2 (so 1024 bytes in a kilo byte); HD manufacturers specify the space in multiples of 10 (so 1000 bytes is a kilo byte). That should bring you from 1 TB to 909GB.

Further there's space allocated for root's usage; some programs don't have to care about that and will therefore report more space (disk utility is more than likely one of them). If the HD is full and a normal user can't login because of that, root can still login and fix it. This should be about 5%.

---

### Post by jan-banan on 2011-07-28
They all have the suffix GB so i guess it comes down to if they report that extra hidden root space or not.

---

### Post by Wim Sturkenboom on 2011-07-28
One thing I forgot.

If you delete a file while it's still in use, it's no longer visible in the browser (e.g. nautilus) and will therefore be counted as free. However as the space is not actually free yet, disk usage will still see it as used.

And the last one :D
If you have mounted an external disk, it might hide the content of a directory. disk usage will count it and a browser will not see it and not count it.

PS: In both cases I might have it swapped around; too lazy to check but you can read up on the command *df* and *du*

---

