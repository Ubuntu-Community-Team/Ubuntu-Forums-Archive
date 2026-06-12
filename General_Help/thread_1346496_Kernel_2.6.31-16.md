---
title: "Kernel 2.6.31-16"
date: 2009-12-05
forum: General Help
---

### Post by Miguel on 2009-12-05
Dear ubunteros,

I'm a bit puzzled about where to put this topic, but since the -16 kernel is a security update, maybe this is the right place. 

The thing is, I'm one of the fellows that saw a very clear degradation of boot time with Karmic on my laptop with a magnetic HD. This was brilliantly fixed with ureadahead and the required -15 kernel, available in karmic-proposed.

Today I had the -16 kernel available as a security update. According to the changelog, it had one SCSI subsystem fix, three launchpad bug fixes and several security bug fixes pertaining at least two advisories. However, I saw no mention of the required patches for ureadahead. Trying to read the changelog of 2.6.31-15, instead of providing the useful info, shows a succinct "ABI bumped for proposed kernel".

I have my doubts that the required bits for an optional performance update are included in a "mandatory" security update. Does anybody know for sure whether the ureadahead bits are included in the -16 kernel?

Thanks for your comments,

Miguel

---

### Post by ibuclaw on 2009-12-05
This isn't really a security question - so moved to general help.

ureadahead (meaning uber-readahead) is a userspace application ran at boot-time. It is not something that is integrated into the kernel.

If you are worried, you can force generate a new pack file by removing (or renaming):
```
/var/lib/ureadahead/pack
```
and a new pack file will be generated when you reboot.

Rebooting a second time will test the new speed of bootup.

Regards
Iain

---

### Post by Miguel on 2009-12-05
Thanks for your answer, and thanks for moving the thread to a more appropriate place. I actually thought that ureadahed did depend on some specific kernel bits, based on ureadahead's description. From ureadahead's changelog:
```

ureadahead (0.90.3-2) karmic-proposed; urgency=low

  * über-readahead is a replacement for sreadahead that should
    significantly improve boot performance on rotational hard drives,
    especially those that had regressed in performance from jaunty to
    karmic.

    It does this by pre-loading such things as ext2/3/4 inodes and opening
    files in as logical order as possible before loading all blocks in one
    pass across the disk.

    On SSD, this behaves much as sreadahead used to, replacing that package
    with slightly improved tracing code.

    This requires the kernel package also found in karmic-proposed.

    LP: #432089.

 -- Scott James Remnant <scott@ubuntu.com>  Mon, 09 Nov 2009 18:38:51 +0000

```

I'll perform the tests anyway, and maybe also ask in the ureadahead bug if I still have some doubts. Have a nice weekend,

Miguel

---

### Post by ibuclaw on 2009-12-05
[QUOTE=Iain's terminal]
iain@netbook:~/src/ureadahead-0.90.3$ grep "#include <linux" src/ -nR
[COLOR="Indigo"]src/trace.c[/COLOR][COLOR="Cyan"]:[/COLOR][COLOR="Lime"]47[/COLOR][COLOR="Cyan"]:[/COLOR][COLOR="Red"]#include <linux[/COLOR]/fs.h>
[COLOR="Indigo"]src/trace.c[/COLOR][COLOR="Cyan"]:[/COLOR][COLOR="Lime"]48[/COLOR][COLOR="Cyan"]:[/COLOR][COLOR="Red"]#include <linux[/COLOR]/fiemap.h>
iain@netbook:~/src/ureadahead-0.90.3$ 
[/QUOTE]

It's only dependencies are **high level** filesystem headers/hooks.

Even then - for something to break, the hooks that it depends on with need to be removed/changed. Which is not very likely - especially in a minor revision update. ;)

If you have doubts - look in your dmesg.
If ureadahead was broken, it would likely segfault on you...

---

### Post by Miguel on 2009-12-05
I've rebooted with -16 and the time was in line with previous boots. Some difference exists in the bootcharts, but heck, nothing weird. Funnily, though, /var/lib/ureadahead/ only has an empty directory inside. It could have detected a new kernel and is forcing a reprofile next boot, couldn't it?

Anyway, the only mention with an "error" I've seen regarding ureadahead in the boot logs is
```

Dec  5 15:02:21 lcpybm init: ureadahead-other main process (1179) terminated with status 4

```
I've seen that message appear in every boot, so I guess it's normal and all. It also appears in both my Ubuntu and Kubuntu logs, so I'll just shut up and go back to work.

Thanks again for all your comments, Iain

---

