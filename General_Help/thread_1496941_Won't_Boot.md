---
title: "Won't Boot"
date: 2010-05-29
forum: General Help
---

### Post by Kansasguy on 2010-05-29
A friend has a Toshiba laptop, with Windows 7. He loaded Mint 8 and wanted to change the boot order. I told him to re-load the Mint partition with Mint 9 so we could just Menu>Control Center> System > Startup Manager. He loaded Mint 9 and can't boot ANY operating system.

Gets an error message
Grub error: unknown file system

and then:
GRUB rescue prompt

He doesn't really want to reformat and load Windows 7 again

Any help would be greatly appreciated (or just a point in the right direction)

---

### Post by wilee-nilee on 2010-05-30
Post the boot script in code tags. [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Kansasguy on 2010-05-31
SOLVED  There are probably several ways to do this, but he ultimately put in the Windows 7 CD and fixed the boot record, with fixmbr I think.  Thanks so much.

---

