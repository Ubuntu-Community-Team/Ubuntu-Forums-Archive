---
title: "Ubuntu won't boot after &quot;emergency reset&quot;"
date: 2009-11-16
forum: General Help
---

### Post by stiansoftcore on 2009-11-16
I turned on my PC about an hour ago, went to shower, and forgot I turned it on. So I tried again, but instead of hitting the "POWER ON" button, I hit the reset button, the small one next to the power button. I don't know what it's called.

Anyway, when the PC boots, I'm presented to the "maintenance shell". Is there a fix for this? I'll give you the full error message:
```
/dev/sda6: UNEXPECTED INCONSISTENSY; RUN fsck MANUALLY.
           (i.e., without -a or -p options)
mountall: fsck / [446] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (426) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@axelpaxel-desktop:~#
```
OR, if you want the screenie:
[img]http://2.bp.blogspot.com/_09eRNofzOWo/SwEqUnAop0I/AAAAAAAAAGI/GI001o-76Iw/s1600/image-upload-7-770343.jpg[/img]
If ofcoruse tried CONTROL+D, it just gives me a reboot, and the same screen.

---

### Post by Bunnybugs on 2009-11-16
Have you pressed that button again??

Could be some turbo kind of button, they seem to stay pressed in untill you press it again...

---

### Post by jeb800e on 2009-11-16
Its telling you to run fsck. You may have a file system error. If you have to do an emergency restart again, do the REISUB technique.

Hold down on Alt and  SysRq, then slowly type REISUB, one letter at a time, waiting at least 2-3 seconds after each letter is pressed.

---

### Post by stiansoftcore on 2009-11-16
> **jeb800e said:**
> Its telling you to run fsck. You may have a file system error. If you have to do an emergency restart again, do the REISUB technique.

Hold down on Alt and  SysRq, then slowly type REISUB, one letter at a time, waiting at least 2-3 seconds after each letter is pressed.

My keyboard doesen't have a SysRq button, so that can't be done!

---

### Post by Bunnybugs on 2009-11-16
That's the secondary function of the Prt Sc (Print Screen)-button

---

### Post by jeb800e on 2009-11-16
Yeah. Print Screen and System Request (SysRq) are the same

---

