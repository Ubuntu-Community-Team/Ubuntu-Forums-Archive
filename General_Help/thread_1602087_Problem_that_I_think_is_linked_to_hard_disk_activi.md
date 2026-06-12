---
title: "Problem that I think is linked to hard disk activity - need to know where to look!"
date: 2010-10-21
forum: General Help
---

### Post by pHreaksYcle on 2010-10-21
> modprobe: FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: No such file or directory

is the first thing I see when I boot up Ubuntu 10.10. Then, at a seemingly random time, normally while writing to the hard drive, it'll lock up, screen will freeze wherever it is, and the keyboard lights will flash. I've determined it's not a hardware issue by using Win7 and replacing my GPU, HDD, mobo, and doing a RAM check.

Someone please help - I miss Ubuntu, Windows just doesn't cut it for me.

---

### Post by efflandt on 2010-10-21
Sounds like a kernel update was incomplete.  Can you still boot a different (earlier) kernel?

What do you get for: **ls /lib/modules**

There should be a bunch of stuff in the dir for that kernel: 
**ls /lib/modules/2.6.35-22-generic/**
```
build              modules.builtin.bin  modules.inputmap   modules.softdep
initrd             modules.ccwmap       modules.isapnpmap  modules.symbols
kernel             modules.dep          modules.ofmap      modules.symbols.bin
modules.alias      modules.dep.bin      modules.order      modules.usbmap
modules.alias.bin  modules.devname      modules.pcimap     updates
modules.builtin    modules.ieee1394map  modules.seriomap
```

---

### Post by srs5694 on 2010-10-21
Try typing this as soon as you boot:

```

sudo depmod -a

```

If you're having problems writing files, or if some module files are missing or damaged, that might fail, but it's possible it'll fix the problem.

---

### Post by pHreaksYcle on 2010-10-23
Sorry it took so long to reply - I'll follow up on both of your posts in just a few minutes here...

---

### Post by pHreaksYcle on 2010-10-23
> **efflandt said:**
> Sounds like a kernel update was incomplete.  Can you still boot a different (earlier) kernel?

What do you get for: **ls /lib/modules**

There should be a bunch of stuff in the dir for that kernel: 
**ls /lib/modules/2.6.35-22-generic/**
```
build              modules.builtin.bin  modules.inputmap   modules.softdep
initrd             modules.ccwmap       modules.isapnpmap  modules.symbols
kernel             modules.dep          modules.ofmap      modules.symbols.bin
modules.alias      modules.dep.bin      modules.order      modules.usbmap
modules.alias.bin  modules.devname      modules.pcimap     updates
modules.builtin    modules.ieee1394map  modules.seriomap
```

Okay, here's what's in that directory on my system - looks identical:
> 
build              modules.builtin.bin  modules.inputmap   modules.softdep
initrd             modules.ccwmap       modules.isapnpmap  modules.symbols
kernel             modules.dep          modules.ofmap      modules.symbols.bin
modules.alias      modules.dep.bin      modules.order      modules.usbmap
modules.alias.bin  modules.devname      modules.pcimap     updates
modules.builtin    modules.ieee1394map  modules.seriomap

@srs5694 Ran depmod -a, rebooting for good measure after I post this reply, will update on status as soon as I start some disk activity ^.^

---

### Post by pHreaksYcle on 2010-10-23
depmod -a completed successfully, and it's staying live for a lot longer now, but it still happens after 10 minutes to 30 minutes or so of torrenting or file transfers. Any other suggestions??

---

### Post by geordie17 on 2010-10-24
**I**[B] have the same message at boot up, it comes up twice then it boots in to the system and everything works fine as far as i can tell,but then I have only been using Ubuntu for a couple of day since my move from Windows7 . I have the directory of lib/modules/2.6.35-22-generic/ with files etc in them, would be nice to get rid of the message.
[/B]

---

