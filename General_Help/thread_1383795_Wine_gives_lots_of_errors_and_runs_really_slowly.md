---
title: "Wine gives lots of errors and runs really slowly"
date: 2010-01-17
forum: General Help
---

### Post by Weepleman on 2010-01-17
Hi, whenever I try to do anything in wine, including winecfg, I get a lot of errors, and the program runs really slowly.  Here are the errors
```
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x147f30, filter=0x84e9e4,flags=0x00000001),
    returns a fake device notification handle!
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a060, {485e7de8-0a80-11d8-ad15-505054503030}, 1, 0x33fe28, (null), (null), 0x100a068,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a080, {485e7de9-0a80-11d8-ad15-505054503030}, 1, 0x33fe28, (null), (null), 0x100a088,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0a0, {485e7dea-0a80-11d8-ad15-505054503030}, 1, 0x33fe28, (null), (null), 0x100a0a8,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0c0, {485e7deb-0a80-11d8-ad15-505054503030}, 1, 0x33fe28, (null), (null), 0x100a0c8,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a0e0, {485e7dec-0a80-11d8-ad15-505054503030}, 1, 0x33fe28, (null), (null), 0x100a0e8,)
fixme:advapi:RegisterTraceGuidsW (0x100778a, 0x100a100, {485e7ded-0a80-11d8-ad15-505054503030}, 1, 0x33fe28, (null), (null), 0x100a108,)
fixme:win:RegisterDeviceNotificationW (hwnd=0x1478e8, filter=0x76e94c,flags=0x00000001),
    returns a fake device notification handle!
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

```
I get this error for every program, so I do not think it is an error with the program.  If fixing this will change anything like making it faster any help would be appreciated.  Oh, I also can only run a few programs.  I can't run things like WMP or itunes, and I think this may be the cause.

---

### Post by tom4everitt on 2010-01-17
Reinstallation might help. 

Instructions:

Remove wine:

sudo apt-get remove wine

removing all settings:

rm -rf ~/.wine

and then installing it again.

---

### Post by Weepleman on 2010-01-17
That worked, thank you very much. :)

---

