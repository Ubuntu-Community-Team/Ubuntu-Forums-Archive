---
title: "black screen cant boot"
date: 2010-10-10
forum: General Help
---

### Post by vahe0s on 2010-10-10
hello
i have tried installing wubu , when i boot i get an option for more options "esc" key, if i dont press esc and wait for 5 seconds my screen goes black!(as if i turned off my screen).
and aso i went into more options  and tried safe graphics mode!
i have older posts about this using 10.04 but now i tried 10.10 , but still a no go! 
i tried booting from cd as well (i burned image on maxell dvd+rw 4.7gb) but still i get black?
i think its because of my video card (nvidia g210m with cuda?)

my computer is a sony vaio vpcl11m1e. 
Windows 7 ultimate
64-bit
4gb ram
500gb hdd
2.93 ghz
full hd 1080p
nVidia geforce g210m with cuda

PLEASE HELP!!!!!

---

### Post by sradhakrishna on 2010-10-11
I have a laptop with similar config. I have gotten the NVIDIA drivers from their website (pick the latest) on 10.04, but am having the same problem on 10.10.

This is what you'll need to do:

1. Download latest drivers from NVIDIA's website
2. Boot into recovery mode from the boot menu, after setting the boot parameter nomodeset
3. run telinit 3
4. run the installer with sudo privileges.

This should work. Atleast for me, it did, on 10.04. 

If it doesn't, do file a bug with NVIDIA.

Regards,
Radha.

---

