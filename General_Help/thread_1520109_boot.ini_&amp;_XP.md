---
title: "boot.ini &amp; XP"
date: 2010-06-29
forum: General Help
---

### Post by slibbe on 2010-06-29
Hi,

could someone post the text in the boot.ini, when using Wubi under Windows XP?
My laptop is not booting anything at the moment.

Regards,

slibbe

---

### Post by slibbe on 2010-06-29
> **slibbe said:**
> 
could someone post the text in the boot.ini, when using Wubi under Windows XP?


This request is only for people having Windows XP and Wubi installed of course.

---

### Post by bcbc on 2010-06-29
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer 
C:\wubildr.mbr = "Ubuntu" 
```

If nothing is booting, run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results here. Instructions in link.

Have you done anything to your system recently? e.g. upgraded to 10.04? Some users have installed grub over their windows bootloader, which doesn't work well with wubi.

---

### Post by slibbe on 2010-06-29
Thx.

Yes, I did 'something'.
Edited the boot.ini without making a backup first. Stupid thing, I know :S

---

### Post by slibbe on 2010-06-29
Well, at least I get the bootloader menu again and Ubuntu really does boot.

Only have to get XP working again ;)
Trouble is, the office has upgraded to Windows 7, but me and one other collegue still need XP because not everything works in Windows 7. But because XP is not supported anymore, no disc are available.

So, I still have some 'work' to do.

---

### Post by bcbc on 2010-06-29
> **slibbe said:**
> Well, at least I get the bootloader menu again and Ubuntu really does boot.

Only have to get XP working again ;)
Trouble is, the office has upgraded to Windows 7, but me and one other collegue still need XP because not everything works in Windows 7. But because XP is not supported anymore, no disc are available.

So, I still have some 'work' to do.

Here's one for xp professional, booting from /dev/sda2. 
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\wubildr.mbr = "Ubuntu"

```

---

### Post by slibbe on 2010-06-29
Well, the XP registry is ****ed up now. 

There's a lot of nicer things to spend a day on :S
To be continued.

---

