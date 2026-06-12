---
title: "modyfying boot.ini"
date: 2011-08-04
forum: General Help
---

### Post by nichos on 2011-08-04
Does anybody know for sure whether if I modify the boot.in as below to give ubuntu priority boot would it be accepted or will it distroy the dual boot & have to reformat the HD?

ORIGINAL boot.ini:-

[boot loader]
timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Win XP Home Edition" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"

=================================================

MODIFIED boot.ini:-

[boot loader]
timeout=30

default=C:\wubildr.mbr = "Ubuntu"

[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Win XP Home Edition" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

---

### Post by WorMzy on 2011-08-04
Don't modify anything from "[operating systems]" and below. Just replace the "default" value with "C:\wubildr.mbr".

EDIT: that's just my take on what you've shown us. I'm not an expert on Windows boot.ini.

---

### Post by nichos on 2011-08-05
SOLVED

Thanks all for your paitence & help.

I understood by now that I do not have enough knowledge to deal with this.

Will stay with present bootloader & each time catch it to select ubuntu.

---

