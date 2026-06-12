---
title: "Error: no such partition"
date: 2010-11-05
forum: General Help
---

### Post by baraka607 on 2010-11-05
hi friends, please help me i was using a laptop with dual boot of windows 7 and ubuntu 10.04 and it was working fine but today i tried to switch on my machine and am getting this ERROR. Please help me to solve it my friends. thank you

---

### Post by Verbeck on 2010-11-05
umm... what does the error say?

---

### Post by baraka607 on 2010-11-05
> **Verbeck said:**
> umm... what does the error say?
 
Just black screen with the following words;
 
**ERROR: NO SUCH PARTITION**
**GRUB**

---

### Post by oldefoxx on 2010-11-05
Grub goes by the UUID when searching for a partition.  If you reformat a drive or partition that Grub pointed to. the UUID would be changed and Grub can get hung on that.  During the install process. I see where the installer does two things, one is install grub, and the other is grub update.   You can also call Grub by name and exercise some commands there to fix things. but like most Linux taskings, the details are not all that clear.  Wish I could be more clear, but it is a weak area in my understanding of what is going on under the covers.

---

### Post by ajgreeny on 2010-11-05
Using the link in my signature from a live CD run the boot-info-script and attach the RESULTS.txt file back here.  It could help diagnose what is going wrong.

---

### Post by wilee-nilee on 2010-11-05
> **ajgreeny said:**
> Using the link in my signature from a live CD run the boot-info-script and attach the RESULTS.txt file back here.  It could help diagnose what is going wrong.

+1 sounds like a wubi install the script will tell us what we need to know.

---

