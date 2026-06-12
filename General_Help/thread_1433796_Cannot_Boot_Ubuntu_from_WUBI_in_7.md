---
title: "Cannot Boot Ubuntu from WUBI in 7"
date: 2010-03-19
forum: General Help
---

### Post by schoft on 2010-03-19
I installed Ubuntu trough Wubi on an external USB hdd. The usb hdd is regonized by the bios. However, when i choose Ubuntu i get an error message:

Windows failed to start
file: \ubuntu\winboot\wubildr.mbr
status: 0xc000000e
application could not load. Corrupt or missing.


Is it possible that my Lacie USB doesnt support OS booting? I find it hard to believe. 

Grtz

---

### Post by schoft on 2010-03-19
Snippet from bcdedit:
```
Real-mode Boot Sector
---------------------
identifier              {f016c860-8f87-11de-bd66-ed9c50595036}
device                  partition=X:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu
```

Snippet from easyBCD
```
There are a total of 2 entries listed in the bootloader.

Default: Windows 7
Timeout: 10 seconds.
EasyBCD Boot Device: C:\

Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Ubuntu
BCD ID: {f016c860-8f87-11de-bd66-ed9c50595036}
Drive: X:\
Bootloader Path: \ubuntu\winboot\wubildr.mbr
```

Seems to be correct, not ?

,Thanks

---

### Post by schoft on 2010-03-19
Anyone?

---

### Post by schoft on 2010-03-19
I have uninstalled wubi and tried installing ubuntu on another hdd, this time one that is in my pc. Now i get the error:

Try Hd(0,0): ntfs5: no wubildr 

I have both wubildr files in c:\

HMMMMMMMMM anyone?

---

### Post by sandyd on 2010-03-19
dont install using wubi.

Install by booting from the cd, then use the ubuntu installer.

---

