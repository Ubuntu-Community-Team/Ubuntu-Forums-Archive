---
title: "OpenGL no longer works after update from Lucid Lynx to Oneric Oscelot"
date: 2011-11-08
forum: General Help
---

### Post by TheSluiceGate on 2011-11-08
[B]Hi All,

I uninstalled Lynx and installed Ocelot today. Ocelot works fantastically - better than Lynx did - but for one issue: OpenGL no longer works.

With Lynx I had been using OpenGL xscreensaver with no problem, and other software reliant on it like GNUbik worked find too, but now they don't work at all.

Is there an OpenGL control panel I can tweak? Or how do I ensure that OpenGL is installed?

I am using a Toshiba Satellite L25 - S121

System graphics info as follows:[/B]

*-display UNCLAIMED
description: VGA compatible controller
product: RC410 [Radeon Xpress 200M]
vendor: ATI Technologies Inc
physical id: 5
bus info: pci@0000:01:05.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: pm msi vga_controller bus_master cap_list
configuration: latency=66 mingnt=8
resources: memory:d0000000-dfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff

**If I run ```
glxinfo | grep direct
``` on the console I get the following:**

X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  135 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  12
Current serial number in output stream:  12

Thanks all for your advice.

---

### Post by TheSluiceGate on 2011-11-09
Can somebody please help?
Please don't send me back to Windows XP [-o< !!

---

### Post by TheSluiceGate on 2011-11-09
Does this help too?:

[http://paste.ubuntu.com/733252/](http://paste.ubuntu.com/733252/)

---

### Post by TheSluiceGate on 2011-11-09
OK, I have solved this myself.

I had to do a fresh install of Oneric Ocelot, and now, magically OpenGL works fine!

Pity I spent almost 2 days trying to fix it manually! ](*,)

---

