---
title: "GRUB chainloading to MBR?"
date: 2010-04-17
forum: General Help
---

### Post by Colin@oxford on 2010-04-17
I have created a boot floppy for an old machine.  That machine has GRUB installed on its MBR and I would like to be able to chainload to that in the case where the floopy has been accidentally left in (in much the same way that the install CDs do for Ubuntu).  If I use
```

rootnoverify (hd0)
makactive
chainloader +1

```
GRUB tells me this is an illegal device name.  If I provide a partition number (e.g. hd0,0) then it is happy, but attempts to find the loader in the partition, not the MBR.

Since the descriptions of "root" and "rootnoverify" both specify a device, rather than a partition, I assume that I am missing something.

Can you help?

---

### Post by srs5694 on 2010-04-17
I'm certain I've done this before, but I don't have a reference system booted at the moment, so I can only guess or try to remember how I did it. Some suggestions:


[list]
[*]Omit the "makeactive" line. That command is intended to set the active (aka bootable) flag on a partition, which is of course meaningless when applied to a whole disk device.
[*]Try "root" rather than "rootnoverify". (This is just a shot in the dark suggestion, though.)
[*]Try "rootnoverify (hd0,0)" (or some other partition) along with "chainloader (hd0)+1". This tells GRUB it's going to use a partition but then forces it to chain-load the MBR.
[/list]


If none of these work, post back. I may be able to find a working sample configuration on one of my computers.

---

### Post by oldfred on 2010-04-17
These settings with old grub have worked for me, until Lucid installed grub1.98 into sda. 

title       Ubuntu 9.04 Jaunty 32 bit @ sdb
root        (hd1)
chainloader +1

title       Ubuntu 9.10 Karmic 64 bit @ sdc
root        (hd2)
chainloader +1

title       Ubuntu 10.04 Lucid alpha/beta @ sda
root        (hd0)
chainloader +1

---

### Post by Colin@oxford on 2010-04-18
Thanks.  That worked.

---

