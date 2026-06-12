---
title: "Cannot remove fglrx, no matter what."
date: 2010-11-20
forum: General Help
---

### Post by Elcarc on 2010-11-20
I traveled across the lands, searching far and wide

I found nothing that would fix my problem. Tried all the guides, copy/pasted so much script, but nothing works. This thing is like a damn virus, seriously. 

This is what I get when I do the basic solution
> [PHP]edward@edward-desktop:~$ sudo apt-get remove fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 209 not upgraded.
1 not fully installed or removed.
After this operation, 65.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 165533 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
edward@edward-desktop:~$ [/PHP]


I get something similar when I try to purge it. 
Synaptic can't remove it either. 
Can someone get me through this?

---

### Post by dcstar on 2010-11-20
> **Elcarc said:**
> I traveled across the lands, searching far and wide

I found nothing that would fix my problem. Tried all the guides, copy/pasted so much script, but nothing works. This thing is like a damn virus, seriously. 

This is what I get when I do the basic solution


I get something similar when I try to purge it. 
Synaptic can't remove it either. 
Can someone get me through this?

[LIST=1]
[*]Do NOT quote code.
[*]Try reinstalling xorg-driver-fglrx
[/LIST]

---

### Post by Elcarc on 2010-11-20
> **dcstar said:**
> 
[LIST=1]
[*]Do NOT quote code.
[*]Try reinstalling xorg-driver-fglrx
[/LIST]

1. Erm, okay, noted. 
2. Okay. I tried that, it gave me some stuff, so I just reinstalled fglrx (instead of xorg-driver-fglrx). Note, I've done this before. It didn't work this time either

Thanks though ;-;

---

