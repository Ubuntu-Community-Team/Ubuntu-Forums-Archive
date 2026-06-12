---
title: "Customizing Grub - Possible to Overwrite menu.lst on boot?"
date: 2010-01-13
forum: General Help
---

### Post by ramsay on 2010-01-13
Hello,

I'm new to Ubuntu/Linux and am slowly but gradually getting the hang of it. I have a situation where I would like the grub boot loader to dynamically overwrite the menu.lst file just before loading the Linux/Windows Kernel.

More Detail:

I'm running a dual boot XBMC Live (ubuntu kernel) / Windows 7 machine. Everything is installed, including Grub (Legacy) and works perfectly. 

I would like to create a script in XBMC that will essentially be a function to "Boot to Windows 7" so one can easily and conveniently choose this with a remote control in the living room. My vision is that this script would replace the existing "standard" menu.lst (that is normally set to automatically boot to XBMC Live) with a replacement menu.lst that instructs Grub to boot to Windows 7 without intervention. Makes sense? 

Because (to my knowledge) I can't revert menu.lst back to loading XBMC Live by default (since I'll be in Windows and can't access the filesystem), my idea was to customize Grub so it will automatically replace menu.lst with the "standard" configuration just prior to loading up the Windows 7 kernel...such that a subsequent reboot would send me right back to XBMC Live.

The end result would be an (easy?) way to quickly jump into Windows on the fly, and get back to XBMC on reboot without the need to keyboard interaction, etc.

Can anyone let me know if getting Grub to replace/re-write menu.lst on the fly is even possible, or if I'm totally out to lunch?

Thanks.

---

