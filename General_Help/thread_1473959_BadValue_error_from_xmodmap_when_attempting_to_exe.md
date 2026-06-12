---
title: "BadValue error from xmodmap when attempting to execute &quot;clear Lock&quot; directive"
date: 2010-05-05
forum: General Help
---

### Post by intuited on 2010-05-05
IE

```
$ xmodmap -e 'remove Lock = Caps_Lock'
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  118 (X_SetModifierMapping)
  Value in failed request:  0x17
  Serial number of failed request:  11
  Current serial number in output stream:  11
```

I get an identical error message when running the command
```
$ xmodmap -e 'clear Lock'
```

This just started happening with my recent upgrade to Lucid.

I'm running the openbox window manager right now; I will try a Gnome session and a KDE session to see if that makes a difference, and will post a reply if this error does not occur under either of those WMs.

---

### Post by intuited on 2010-05-05
Confirmed that this error is reproducible under both GNOME and KDE.

---

### Post by intuited on 2010-05-05
I've posted a bug report for this issue:

[https://bugs.launchpad.net/ubuntu/+source/x11-xserver-utils/+bug/576102](https://bugs.launchpad.net/ubuntu/+source/x11-xserver-utils/+bug/576102)

---

