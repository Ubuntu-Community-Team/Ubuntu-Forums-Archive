---
title: "RAM is getting full !!!"
date: 2011-06-08
forum: General Help
---

### Post by intelligence storm on 2011-06-08
Hi ,
i have a desktop pc with 1G RAM and 3,000 cpu was running XP perfectly.....
yesterday i've installed ubuntu 11.4 in another partition....and it's done but i notice in system monitor that ram capacity goes up and no program is running !! and if i open firefox Ram will continue going up until it get full then no respond :(,,,,,,,,,,why???
please, help ??!

---

### Post by Joe of loath on 2011-06-08
Sounds like there's a memory leak.

If you open the system monitor, can you see which process is filling up?

---

### Post by dozycat on 2011-06-08
do not use system monitor. Try top from the terminal.

---

### Post by philinux on 2011-06-08
> **dozycat said:**
> do not use system monitor. Try top from the terminal.

+1.

When top is running do Shift F then press n and enter. This will sort it by memory usage.

---

### Post by intelligence storm on 2011-06-08
yes ,i did it , i wrote in terminal "top" and saw the processing ,hugest one was firefox about 35 MB
but what i mean that the ram free space  decrease automatically without any touch !!! no program is running ! nothing at all !!       whyyyyyyyyyyyyyyy???
i'll try to install ubuntu 10.10 to see if problem is continuing or not-what do you see ???!-

---

### Post by Joe of loath on 2011-06-08
Which number are you looking at?

```

             total       used       free     shared    buffers     cached
Mem:          1001        784        216*          0         74        422
-/+ buffers/cache:        **287        713**
Swap:         1951          0       1951

```

There's the output of free -m on my machine. Linux likes to cache memory, so the free figure (*) is not what a user of another operating system would consider free. Instead, you want to look at the bolded figures, as they're more 'true' to how much memory you are actually using.

---

### Post by intelligence storm on 2011-06-11
thank you all for helping
and i thought the problem was caused by activation of graphic card cos when it is disable no more Ram eaten !!

anyway, i reinstall ubuntu 10.10 it perfectly works with graphic card

thanks for all

---

