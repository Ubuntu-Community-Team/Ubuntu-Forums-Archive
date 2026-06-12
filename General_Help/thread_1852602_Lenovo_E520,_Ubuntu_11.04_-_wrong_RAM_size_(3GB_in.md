---
title: "Lenovo E520, Ubuntu 11.04 - wrong RAM size (3GB instead of 4GB)"
date: 2011-09-30
forum: General Help
---

### Post by khurtsiya on 2011-09-30
Fresh install from the last download.

System monitor:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=203212&stc=1&d=1317382254[/IMG]

misha@laptop:~$ free -m
total used free shared buffers cached
Mem: 2937 1101 1836 0 58 610

and only BIOS shows 4GB

any help appreciated

---

### Post by CHEWS on 2011-09-30
how much of your ram is dedicated to video in bios? and are you running 32 or 64bit ubuntu

---

### Post by 2F4U on 2011-09-30
Did you run memtest? It may be the case that something is wrong with the memory. The fact that the BIOS shows 4 GB doesn't say that everything is ok with that RAM.

---

### Post by CHEWS on 2011-09-30
Seriously if ram is dedicated to video in bios it doesn't show up and 64bit supports more ram if you have the cpu than 32bit. Bad ram normaly just freezes my system but could run memtest if neither of those show to be the issue. Well run memtest before trying to reinstall ofc lol

---

### Post by khurtsiya on 2011-09-30
32

how much is dedicated for video I can't find this in BIOS

but I guess the answer is in this

thanks!

---

### Post by CHEWS on 2011-09-30
its one of the setting it it depends on the bious just lokk for video memory listing that can be changed.

---

### Post by khurtsiya on 2011-09-30
misha@laptop:~$ memtest
memtest: command not found

---

### Post by khurtsiya on 2011-09-30
> **CHEWS said:**
> its one of the setting it it depends on the bious just lokk for video memory listing that can be changed.

there are no such settings

---

### Post by CHEWS on 2011-09-30
it may be in an otherwises purely informational section unless you don't have any sort of on board graphics chip. try the memtest then just try a live cd of a 64bit ubuntu and see if it sees all the ram

---

### Post by CHEWS on 2011-09-30
Just noticed ur post on memtest, that is a bios option though ubuntu has one two in boot menu that you have to make come up, its not a program

---

### Post by Blasphemist on 2011-09-30
If you install a 32 bit version of the distro from cd (vs the larger dvd), you may be running the generic kernel instead of the PAE kernel. Could that be your issue? On the grub screen do you see PAE in the kernel name?

If you are not using the PAE kernel, it allows 32 bit to use more that 3GB of memory, the PAE kernel can be installed. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

