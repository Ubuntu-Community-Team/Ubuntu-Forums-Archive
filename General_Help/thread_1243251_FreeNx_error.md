---
title: "FreeNx error"
date: 2009-08-18
forum: General Help
---

### Post by Micha3615 on 2009-08-18
Hi,
 
I have a server that I wanted to configure freenx, everything is installed.  When I try to login I get this message: THe NX service is not available or the NX access was disabled on host.
 
in the details i do get authenticated but I get this:
 
--geometry="1280x1024x32+render" --type="unix-kde"
mktemp: cannot create temp file /tmp/nxserver_tmp.rOgrzdZkI: Permission denied
/usr/bin/nxserver: line 273: $TMPFILE: ambiguous redirect
/usr/bin/nxserver: line 274: $TMPFILE: ambiguous redirect
/usr/bin/nxserver: line 281: $TMPFILE: ambiguous redirect
/usr/bin/nxserver: line 282: $TMPFILE: ambiguous redirect
/usr/bin/nxserver: line 358: $TMPFILE: ambiguous redirect
/usr/bin/nxserver: line 359: $TMPFILE: ambiguous redirect
/usr/bin/nxserver: line 365: $TMPFILE: ambiguous redirect
NX> 280 Exiting on signal: 15

 
Any idea why?

---

### Post by Micha3615 on 2009-08-19
Found the problem.

---

### Post by stinger30au on 2009-08-19
and the cure was??????

---

