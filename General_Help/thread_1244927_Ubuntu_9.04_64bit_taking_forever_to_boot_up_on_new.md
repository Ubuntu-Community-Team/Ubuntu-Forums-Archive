---
title: "Ubuntu 9.04 64bit taking forever to boot up on new computer"
date: 2009-08-20
forum: General Help
---

### Post by munkiipoo on 2009-08-20
Hello,

At first I thought Ubuntu didn't work on my computer, but one time my computer restarted by itself because of Windows updates while I was away and came back to see Ubuntu. (It's the default in GRUB). 

I just bought/made this computer, I don't know what to do to fix this problem. Ubuntu 8.04 works fine but I'd like to use 9.04 if possible...

What happens is the splash screen comes up and loads, then my monitor turns black/turns off. Then it takes roughly 30 minutes until the desktop comes. I know it really shouldn't take that long... This is newly installed.

Processor: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz (2 CPUs), ~2.5GHz
Memory: 4094MB RAM
Hard drive: 1 TB
Graphics: ATI Radeon HD 4650
Vista Ultimate SP1 64-bit
Ubuntu 9.04
System Manufacturer: Gigabyte Technology Co., Ltd.
System Model: EP45T-UD3LR

Thank you.

---

### Post by dearingj on 2009-08-20
Have you installed any software updates yet in Ubuntu 9.04?

---

### Post by tgeer43 on 2009-08-20
Edit your /boot/grub/menu.lst file (make a backup copy of it first) and remove the 'quiet' and 'splash' options from the line for the kernel you are trying to boot. Then you will be able to watch everything execute as it boots and should be able to easily see where it is hanging.

tgeer

---

