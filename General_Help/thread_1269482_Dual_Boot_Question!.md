---
title: "Dual Boot Question!"
date: 2009-09-18
forum: General Help
---

### Post by TheStroj on 2009-09-18
Hi everyone!
I have Windows 7 and Ubuntu 9.04 installed on my PC. And when i turn on my computer, I have 10 seconds to choose which operating system i want to use, or Ubuntu will boot automatically. Can I turn that "time-to-choose" option off? 

I'm testing Windows 7 and sometimes I want to boot it and don't want to wait next to my computer just to press Down and Enter. I just want too boot the PC and choose the OS I want later, even if I'm not there at the moment. 

Simply said: I want dual boot to wait forever for me to choose the OS I want to use. How do I do that?

---

### Post by TheStroj on 2009-09-18
*please help me, I know you know the answer!*

---

### Post by prem1er on 2009-09-18
Edit the file /boot/grub/menu.lst. It is a configuration file. You need to set the 'timeout' option to 0.  Make sure you backup this file before you make any changes.  Also, search before posting, there are many posts about this topic.

---

### Post by rocket16 on 2009-09-18
Sure. You need to edit Grub fot this. But an easy way is to download KGrubEditor from Add/Remove. Go to Applications -> Add/Remove Applications and in the search box, type KGrubEditor. Now, download it just checking the box to the lft of it, and click "Apply". Now, use Applications -> System Tools -> KGrubEditor. And, go to Options and uncheck the "Boot Default Entry after" and you're done.

---

### Post by TheStroj on 2009-09-18
> **prem1er said:**
> Edit the file /boot/grub/menu.lst. It is a configuration file. You need to set the 'timeout' option to 0.  Make sure you backup this file before you make any changes.  Also, search before posting, there are many posts about this topic.
Thank you!

---

### Post by Shujah on 2009-09-18
The easy way is to download the package Startup-Manager from Synaptic. It will be available in Menu > System > Administration > Startup Manager. Open it and change the Value of time out or if you want to disable the function uncheck 'use timeout in bootloader'. You can also change the default boot OS to the one you want.

---

