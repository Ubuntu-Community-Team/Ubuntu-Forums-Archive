---
title: "vncconfig: X Error of failed request:  BadLength (poly request too large or internal"
date: 2009-11-13
forum: General Help
---

### Post by ypsd on 2009-11-13
vncconfig gives me the following error. Could somebody let me know what the problem is? How to fix it?

$ vncconfig 
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  134 (VNC-EXTENSION)
  Minor opcode of failed request:  1 ()
  Serial number of failed request:  65
  Current serial number in output stream:  65

---

### Post by yodasoda on 2010-03-12
same here

---

### Post by alphasoup on 2010-07-21
Same issue here using Hardy Heron 8.04 -- no workaround found.
Using the default .vnc/xstartup default provided with one extra line:
unset SESSION_MANAGER to enable gnome_session.

On one version of 9.4 vncconfig starts OK with exact same xstartup.

---

### Post by alphasoup on 2010-12-19
Workaround finally found.
Don't use the default (vino based?) vnc server.
Install and load x11vnc instead... Works great.

---

