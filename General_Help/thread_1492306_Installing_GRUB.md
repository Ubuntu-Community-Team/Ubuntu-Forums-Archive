---
title: "Installing GRUB"
date: 2010-05-24
forum: General Help
---

### Post by l HaVoC l on 2010-05-24
Hi, first off I'm a new user to ubuntu and I don't know a whole lot. I'm building a Rocks mini-cluster with old machines, and many of the nodes that I'm trying to install rocks on encounter GRUB errors.

Currently I'm working on one node that I DBAN'd, and now I've booted from a LiveCD and created a new eth2 partition. This is where I am stuck. DBAN wiped my boot loader, correct? If I put in the Rocks Mega CD nothing happens.

So do I have to install GRUB through the LiveCD? And if so, I've already looked at this thread...

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but I run into problems when trying that. I have no data I want to save, I only have one hard drive per node, all I need is to get these nodes running Rocks Mega.

Thank you, and sorry if I sound clueless, because I sort of am.

---

### Post by l HaVoC l on 2010-05-24
bump.

---

### Post by l HaVoC l on 2010-05-24
I'm not even sure if this is the correct forum, but if anyone could help it would be greatly appreciated.

---

### Post by wilee-nilee on 2010-05-24
> **l HaVoC l said:**
> I'm not even sure if this is the correct forum, but if anyone could help it would be greatly appreciated.

Your in the main post list so that is appropriate. You might not get a quick response as this is could be a set of complex problems. Your also expecting instant responses, when the forum etiquette is not to bump in less then 24 hours. This is a site with free help, even the mods are not paid. Take a deep breath and relax you probably will get some help. ;)

If you think your in a wrong forum though then contact the mods and have them move your thread or due what is appropriate, be sure not to start a new thread on the same topic without contacting the mods for options.

You might also from a live cd run sudo fdisk -l so we can see the setup. the l is a small case L

---

### Post by oldfred on 2010-05-24
What is Rocks? Google only came up with this thread and lots of music links. Is it based on Ubuntu?

---

### Post by l HaVoC l on 2010-05-25
> **wilee-nilee said:**
> Your in the main post list so that is appropriate. You might not get a quick response as this is could be a set of complex problems. Your also expecting instant responses, when the forum etiquette is not to bump in less then 24 hours. This is a site with free help, even the mods are not paid. Take a deep breath and relax you probably will get some help. ;)

If you think your in a wrong forum though then contact the mods and have them move your thread or due what is appropriate, be sure not to start a new thread on the same topic without contacting the mods for options.

You might also from a live cd run sudo fdisk -l so we can see the setup. the l is a small case L

Ah, very sorry, I'm new here but I should know better, thanks. As for the fdisk -l, I get this.

```

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifer: 0x000442ea

Device Boot     Start     End     Blocks    Id     System
/dev/sda1           1    2431   19526976    83     Linux
```

---

### Post by l HaVoC l on 2010-05-25
> **oldfred said:**
> What is Rocks? Google only came up with this thread and lots of music links. Is it based on Ubuntu?

Rocks is a distribution for computer clusters.

---

