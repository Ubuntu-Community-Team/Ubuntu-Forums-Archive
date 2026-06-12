---
title: "trouble compiling ieee80211"
date: 2006-01-26
forum: General Help
---

### Post by gidkill on 2006-01-26
Clearly, I have failed to download something. Can anyone tell me what that is?

sh-3.00# make install
make -C /lib/modules/2.6.12-10-386/build M=/var/tmp/ipw2200/ieee80211-1.1.8 MODVERDIR=/var/tmp/ipw2200/ieee80211-1.1.8 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
sh-3.00#

---

### Post by Iandefor on 2006-01-26
Just out of perverse curiosity, why are you running sh and not bash?

Try installing the kernel source and the kernel headers. Those are necessary for compiling and installing kernel modules.

Type into a terminal 
```
uname -r

sudo apt-get install linux-source-2.6.12 linux-headers-[output from uname -r]
```

---

### Post by gidkill on 2006-01-26
sh? Oh, I was just trying to see if it made a difference - thought perhaps it might have slightly different env variables set. Didn't make any difference.

So, what' s crazy is that I have used both synaptic and apt-get to download all the kernel source and header files.

---

### Post by gidkill on 2006-01-26
Started from scratch. Reinstalled Breezy. Downloaded updates. Then downloaded the build-essentials and the headers. Now when I look, the /lib/modules/'kernel-version'/build directory exists and is populated. Not sure what I did wrong the first time, but it looks like I'm in a much better place to begin the process.:cool:

---

### Post by Iandefor on 2006-01-26
[quote=gidkill]Started from scratch. Reinstalled Breezy. Downloaded updates. Then downloaded the build-essentials and the headers. Now when I look, the /lib/modules/'kernel-version'/build directory exists and is populated. Not sure what I did wrong the first time, but it looks like I'm in a much better place to begin the process.:cool:[/quote] It does rather sound like it, doesn't it? Do report back and tell us how it goes!

> 
So, what' s crazy is that I have used both synaptic and apt-get to download all the kernel source and header files. It doesn't matter which way you get the source and header files- either way works, but it's easier to describe it using the terminal.

---

