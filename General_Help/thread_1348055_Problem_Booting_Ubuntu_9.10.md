---
title: "Problem Booting Ubuntu 9.10"
date: 2009-12-06
forum: General Help
---

### Post by Absense on 2009-12-06
I've installed Ubuntu 9.10 a few weeks ago and it ran without any problems.

I've been double booting it with windows with no problem.

Yesterday when i selected to boot Ubuntu it went to GRUB and displayed this message:

"Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename."

I tryed some stuff i found around the forum and i did the following command lines:

root (hd0,1)
chainloader +1
boot

and it went to windows...

so i tryied again

root (hd0,2)
chainloader +1
boot

and it goes back to the boot menu between Windows and Ubuntu...

I'm not an expert on linux/ubuntu so i would apreciate some help on this.. 

Thanks in advance.

---

### Post by namok on 2009-12-07
Use this: [How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

