---
title: "i can`t resize partition with gparted"
date: 2011-12-29
forum: General Help
---

### Post by bestbg on 2011-12-29
Hi everyone. i`ve install ubuntu to my aspire one d257 , but i have some problems. First wireless driver doesn`t work. Just have wired network , but now wireless network. I`ve try windows driver but anything happend. My bigger problem is that i can`t resize my HDD. Gparted show me that is boot partition and can`t resize. I want 2 partition , and the second i want to be NTFS . How can i do this? 


P.S. Gparted stop working ;( . When i start it , type my password , and anything happend ? what`s the problem ?

Thank you for your attention .

---

### Post by dabl on 2011-12-29
Which version of windows?  If Win 7, you have to use the Windows disk management tool to shrink the Win 7 partition, before you use GParted.

GParted must be run in "gksu" mode -- super user mode.

---

### Post by mike555 on 2011-12-29
You need to use gparted from the live cd, it can't be used from an installed system on the same system (while it's running) even from the live cd you might need to unmount the swap partition .

---

### Post by AARON_73 on 2011-12-30
You also might want to check if you have enough memory, sometimes gparted won't
work if you don't have enough memory.

---

### Post by bestbg on 2011-12-30
it`s work from live cd :) Thank you

now i have problem with windows 7 but i`ll continue trying to see what will happend , because i want touse ubuntu and win 7

---

