---
title: "Wine app without monitor connected?"
date: 2011-02-05
forum: General Help
---

### Post by Mrazek on 2011-02-05
Hi,

I installed mythbuntu 10.04 which will serve as a backend (no problems), as a samba file server (no problems) and also need to run wine graphical application on it (no problems to run it with monitor connected).

I'm able to access this server via VNC or via ssh. But if I try to run this wine app under VNC (with no monitor connected) I got this:
```

X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  89
  Current serial number in output stream:  89
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  89
  Current serial number in output stream:  89
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  89
  Current serial number in output stream:  89

```I'm linux newbie but I think I need to run X the same way with or without monitor connected?
I use Intel Little Fall mainboard with i915 graphical chipset.

---

### Post by mbogevik on 2011-02-18
Please read my suggestion to problem : [http://ubuntuforums.org/showthread.php?p=10471885#post10471885](http://ubuntuforums.org/showthread.php?p=10471885#post10471885)

---

### Post by Mrazek on 2011-02-27
> **mbogevik said:**
> Please read my suggestion to problem : [http://ubuntuforums.org/showthread.php?p=10471885#post10471885](http://ubuntuforums.org/showthread.php?p=10471885#post10471885)

Hello, I'm afraid this solution is not working on 10.04 and 10.10.
I solved it using three resistors on D-SUB which is working perfectly and is OS independent :-)

---

