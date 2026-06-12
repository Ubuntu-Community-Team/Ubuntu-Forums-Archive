---
title: "Ubuntu not detected after Wubi Install (i.e. no dual boot menu)"
date: 2011-04-22
forum: General Help
---

### Post by Jonapedia on 2011-04-22
Hi Everyone,

I just installed Ubuntu 10.10 (if I am not wrong) on my XP computer using Wubi. The problem now is that whenever I boot up, there is no sign of Ubuntu. The computer just goes straight into Windows XP. I checked the C:\ drive (main hard disk) and I see a folder called "ubuntu" and I am quite sure that Ubuntu is supposed to boot from there right? Could someone please help me out? How can I trouble shoot and get Ubuntu to boot up (using the Wubi install, that is)?

Thanks in advance

---

### Post by bcbc on 2011-04-23
An entry for Ubuntu should have been added to the C:\boot.ini (and then windows boot manager prompts you which OS to start). So a) either it failed to add the entry or b) your timeout is set at zero so it's just not prompting you and booting windows (the default).

Check by right clicking on My computer, Properties, Advanced, Startup & recovery settings. There is a drop down box and it should have Windows and Ubuntu in it (leave Windows selected). Then check the timeout and make sure it is 15 or 30.

---

### Post by Jonapedia on 2011-04-24
Hi,

Thanks for the response. Do you have any idea what I should do if XP is the only OS listed? Should I try installing again?

---

### Post by bcbc on 2011-04-24
> **Jonapedia said:**
> Hi,

Thanks for the response. Do you have any idea what I should do if XP is the only OS listed? Should I try installing again?
That's a bit strange. I have seen this before, but it doesn't seem to happen very often. You could post your boot.ini here to see if there is something strange in it. It's hard to know whether reinstalling will help.

You can manually add a boot entry (back up the boot.ini first and also keep a recovery disk on hand because if you mess up the boot.ini it could affect windows booting).

This is the line (goes at the bottom):
```
C:\wubildr.mbr = "Ubuntu"
```So an example of a full boot.ini would be something like:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
```

---

