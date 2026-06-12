---
title: "boot.ini file needs wubi line!!"
date: 2009-07-05
forum: General Help
---

### Post by Ryupower on 2009-07-05
Hello, 
I recently installed wubi, and I liked it. However, I reinstalled windows XP in repair mode, leaving all my programs and documents in tact. Windows XP has wubi still installed (checked applications install/uninstall) , and it's probably still working.

It doesn't boot into wubi, however, it goes straight to XP. I checked the boot.ini file, and saw that the wubi line was removed.
So~
A simple request: anyone mind sharing their boot.ini file with wubi installed? Thank you. :)

 It's an odd request, I know, but I searched online for a sample and couldn't find one

---

### Post by wojox on 2009-07-05
Run chkdsk /r 
Reboot clean

---

### Post by jocko on 2009-07-05
> **wojox said:**
> Run chkdsk /r 
Reboot cleanWhy would that help? Windows will not add ubuntu to the boot menu.

> **Ryupower said:**
> Hello, 
I recently installed wubi, and I liked it. However, I reinstalled windows XP in repair mode, leaving all my programs and documents in tact. Windows XP has wubi still installed (checked applications install/uninstall) , and it's probably still working.

It doesn't boot into wubi, however, it goes straight to XP. I checked the boot.ini file, and saw that the wubi line was removed.
So~
A simple request: anyone mind sharing their boot.ini file with wubi installed? Thank you. :)

 It's an odd request, I know, but I searched online for a sample and couldn't find one
This is what I found when I asked dr. Google:
```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
[COLOR=Blue]c:\wubildr.mbr="Ubuntu"[/COLOR]
```

---

### Post by Ryupower on 2009-07-05
yeah, I tried the command, it didn't do much concerning ubuntu. 
Thank you for sending me the data, everything's up and running again. I'm typing this using kubuntu as I write. :)

---

### Post by Jonas. on 2009-07-06
Hey!

I have pretty much the same problem, and i tried the thing with boot.ini, but it didn't work....

Ryupower where do you keep your wubildr.mbr-file?
and the other files btw. Do you keep any one of them in the C:\ folder?

and why do my windows keep asking about the stupid Windows-rot>\System32\hal.dll.-file?

It also still looks for the windows-file "ntldr". 

Any one knows what to do? Share it!
Thanks

---

