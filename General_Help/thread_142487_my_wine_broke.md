---
title: "my wine broke"
date: 2006-03-10
forum: General Help
---

### Post by Disastorm on 2006-03-10
I dunno what happened it used to work but now when I run winecfg I get this error.

fixme:ntdll:NtConnectPort (0x5ada1170,L"\\ThemeApiPort",0x7fabfb6c,(nil),(nil),(nil),0x7fabfb7c,0x7fabfb78),stub!
fixme:ntdll:NtRequestWaitReplyPort (0xffffffff,0x7fabfc04,0x7fabfbcc),stub!
err:winmm:MMDRV_InitPerType Strange: mapper with 8 > 1 devices
wine: Call from 0x7752e878 to unimplemented function KERNEL32.dll.GetModuleHandleExW, aborting
wine: Unimplemented function KERNEL32.dll.GetModuleHandleExW called at address 0x7752e878 (thread 0009), starting debugger...

---

### Post by kittycatsexycat on 2006-03-10
I've heard its broken on a few dapper kernals... could be your problem if so wait for the upgrade... it'll come....

---

### Post by Disastorm on 2006-03-10
I fixed it I had the wrong drive settings or something, and I did some command someone told me on IRC (i think it was mv or somethingl ike that) and it made it remake the wine configuration file and that fixed it.

---

