---
title: "/dev/rtc doesnt exist"
date: 2009-07-13
forum: General Help
---

### Post by mas123 on 2009-07-13
Hello, 
I want to generate a periodic interrupt through Real time clock RTC. However, /dev/rtc file doesnt exist. How can i configure the kernel to enable the RTC. Thanks.

---

### Post by miklcct on 2009-07-13
Make sure you have the suitable RTC driver and device enable in the kernel. (For PCs, PC-style CMOS is OK, and make sure to enable /dev/rtcN in your kernel)

---

### Post by mas123 on 2009-07-14
thanks for the reply. 

How can I actually enable the kernel? (I am new to linux.)

---

### Post by mas123 on 2009-07-16
One of the sites was suggesting the following:
"modprobe: Can't locate module char-major-10-135

char-major-10-135 refers to the character device, major 10, minor 135, which is /dev/rtc. It provides access to the BIOS clock, or RTC, the Real Time Clock. See /usr/src/linux/Documentation/rtc.txt for more information.

The error is because something, most likely hwclock, is trying to use /dev/rtc but you haven't configured kernel support for it in your kernel. Either delete /dev/rtc so hwclock won't try to use it or enable RTC support in your kernel. It's located in make menuconfig under "Character devices" -> "Enhanced Real Time Clock Support"."

how can i get to menuconfig. Is there a way to enable RTC through terminal line because my TS-linux platform has no GUI (its a platform for a PC104 computer).

---

### Post by mas123 on 2009-07-23
Can anyone attend this thread please?

---

