---
title: "xmess and Apple II emulation"
date: 2011-02-04
forum: General Help
---

### Post by rmccarri on 2011-02-04
Hi everyone,
I'm trying to get Apple II emulation up and running with xmess.  I've been searching for info on how to do this and it seems like it should be fairly simple.  I've downloaded the apple2.zip bios file and placed it in /usr/share/games/xmess/bios

If I run the following command:

```
xmess apple2 -listdevices
```

I get this output


```
 SYSTEM      DEVICE NAME (brief)   IMAGE FILE EXTENSIONS SUPPORTED    
----------  --------------------  ------------------------------------
apple2       slot6disk1  (s6d1)     .do   .dsk  .bin  .po   .nib  
             slot6disk2  (s6d2)  
```   

It seems that then I should be able to simply issue the following command and be off and running:

```
xmess apple2 -slot6disk1 lninja.dsk
```

The emulator opens, I get a warning telling me to type OK and then get to a display that basically says this:

Apple ][

Slot 6 Disk #1: ---
Slot 6 Disk #2: ---

Typing anything gets me to a command line, but there doesn't seem to be anything there (not surprising based on the "---" on the previous screen).  Typing "CATALOG" shows nothing.

Does anyone know how to use this emulator or has run into the same problem.  I think that I'm doing things correctly, but it just doesn't seem to be recognizing the dsk file.
Thanks for any information.
Rob

---

### Post by rmccarri on 2011-02-04
Also, one more thing is that the key to get out of the emulation and give commands to mess is Scroll Lock, which my keyboard doesn't have.  I don't see anything in the configuration files that lets you change that to another key.  Does anyone know how that might be done?
Thanks,
Rob

---

