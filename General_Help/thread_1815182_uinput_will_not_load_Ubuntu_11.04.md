---
title: "uinput will not load Ubuntu 11.04"
date: 2011-07-30
forum: General Help
---

### Post by TrenTech on 2011-07-30
I modprobe uinput but doesn't show up when I run lsmod. Tried adding to /etc/modules file and reboot but this did not help. I need this to get my PS3 remote fully working. I thought it might be loaded but not listed as it supposedly being built into the kernel now but many failed attempts to get my remote working all point towards the uinput not loaded. A little help?:confused:

---

### Post by danielandross on 2011-08-25
I'm having the exact same problem. Please help!
I can't find a repository supporting 11.04.

---

### Post by mpw on 2011-11-03
Same Problem over here, any solution?

---

### Post by ahhughes on 2011-11-30
Same here (11.04) :(

Something I can add, try this and check you have similar output.

~$ locate uinput
/usr/include/linux/uinput.h
/usr/src/linux-headers-2.6.38-11/include/linux/uinput.h
/usr/src/linux-headers-2.6.38-11-generic/include/config/input/uinput.h
/usr/src/linux-headers-2.6.38-11-generic/include/linux/uinput.h
/usr/src/linux-headers-2.6.38-8/include/linux/uinput.h
/usr/src/linux-headers-2.6.38-8-generic/include/config/input/uinput.h
/usr/src/linux-headers-2.6.38-8-generic/include/linux/uinput.h

The following occurs for me:

`lsmod | grep uinput`
yields no output
 
`sudo modprobe uinput`
yields no output, and neither does `sudo modprobe -v uinput`

after running modprobe...

`lsmod | grep uinput`
yields no output

From everything I can see (which is nothing), my guess is modprobe either fails to add the uinput module or the uinput module fails to run/load. Both in total silence.

---

### Post by ahhughes on 2011-12-04
I've been told (and would be great if someone can back this up) but if uinput has been compiled into the kernel then it won't show up when running `lsmod | grep uinput`. Also, you will not need to have it added to /etc/modules (because its compiled in it will auto run).

In addition, if `ls -ld /dev/uinput` produces valid output then it confirms that uinput is running.

Unfortunately, this doesn't solve my bluetooth remote problems because uinput is running. I'm wondering if others are in the same boat as me as you all appear to have the same symptoms - can other people on this thread check this on their machines and write back? Cheers :)

---

### Post by ahhughes on 2012-01-04
Finally I have mine working!!!!

Based on the following:
[http://www.mythtv.org/wiki/Sony_PS3_BD_Remote#uinput_kernel_module_method](http://www.mythtv.org/wiki/Sony_PS3_BD_Remote#uinput_kernel_module_method)

and 

[http://wiki.xbmc.org/?title=HOW-TO_Setup_PS3_BD_Remote](http://wiki.xbmc.org/?title=HOW-TO_Setup_PS3_BD_Remote)

(Note: if you are running mythtv use a different input.conf found here [http://www.mythtv.org/wiki/Sony_PS3_BD_Remote#uinput_kernel_module_method](http://www.mythtv.org/wiki/Sony_PS3_BD_Remote#uinput_kernel_module_method) )

IMPORTANT: The guide's uinput check `lsmod | grep uinput` won't check if uinput has been compiled into the kernel. In 11.04 this appears to be the case. So, you can check `ls -ld /dev/uinput` to test for this. In short, online doco appears to be out of date.

IMPORTANT #2: The python pairing scripts do pair the remote to the machine. However, (for me anyway) it did not set the remote as an input device (and thus never went to uinput). This is the real source of the problem (as far as I can tell). The only way I found I could set the remote as an input device was via the 'blueman' ui (there is an apt aka synaptec package for it). From there, select the remote on the ui, and there are options to set and an input device.

Aside from those two notes, the doco on those pages was enough to get my remote working.

Good Luck!

---

