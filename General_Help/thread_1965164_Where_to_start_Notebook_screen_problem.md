---
title: "Where to start? Notebook screen problem"
date: 2012-04-25
forum: General Help
---

### Post by AD0tech on 2012-04-25
Hi all, thanks for reading.  I've looked through the threads and can't find a solution, any help appreciated.

I'm running Ubuntu 10.04 on my Elonex Notebook, just upgraded and having a problem I think with my screen refresh rate, after the ubuntu logo the screen flickers and is completely unreadable.  When I go into the boot menu and hit F8 to start in safe mode, the startup stops at an (initramfs) prompt, giving the error

ALERT! /dev/disk/by-uuid/3e131947-3ab5-49df-b6e2-e886df913ec9 does not exist. Dropping to a shell!

Ctrl+D or exit just result in the same error again.  I can get to the grub command line but from here I'm out of ideas as to where to start.  Not asking for a full fix, just any idea where to go from here?

Thanks,

---

### Post by cortman on 2012-04-25
Sounds like a problem with your graphics driver. Just from looking on the site it appears that Elonex is only making tablets now, so if you can provide us a model number of your laptop that would be helpful.
Also run the following commands in a terminal and post the full output:

```
lspci | grep -i vga
lshw -C video
```

---

### Post by AD0tech on 2012-04-25
Thanks for your help,

lspci | grep -ivga
01:00 VGTA compatible controller: VIA Technologies, Inc. CX700/VX700 [s3 Unichrome Pro] (rev 03)

lshw -C video
*-display UNCLAIMED
description: VGA Compatible controller
product: CX700/VX700 [s3 Unichrome Pro]
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 03
width: 32 bits
clock: 55MHz
capabilites: bus_master cap_list
configuration: latency=64 mingnt=2
resources: memory:c0000000- dfffffff(prefetchable) memory:fd000000- fdffffff memory:feaf0000- feafffff(prefetchable)

Any ideas what I need to change and where to solve this?

Cheers,

---

### Post by cortman on 2012-04-25
> **AD0tech said:**
> Thanks for your help,

lspci | grep -ivga
01:00 VGTA compatible controller: VIA Technologies, Inc. CX700/VX700 [s3 Unichrome Pro] (rev 03)

lshw -C video
*-display UNCLAIMED
description: VGA Compatible controller
product: CX700/VX700 [s3 Unichrome Pro]
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@0000:01:00.0
version: 03
width: 32 bits
clock: 55MHz
capabilites: bus_master cap_list
configuration: latency=64 mingnt=2
resources: memory:c0000000- dfffffff(prefetchable) memory:fd000000- fdffffff memory:feaf0000- feafffff(prefetchable)

Any ideas what I need to change and where to solve this?

Cheers,

Hi, try running

```
sudo apt-get install xserver-xorg-video-openchrome
```

If it installs, great. If it's already bundled, you may need to get the proprietary driver. There's a really good wiki page on it [here.]("https://help.ubuntu.com/community/OpenChrome")

---

