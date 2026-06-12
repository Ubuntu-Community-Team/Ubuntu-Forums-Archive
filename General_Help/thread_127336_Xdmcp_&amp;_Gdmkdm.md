---
title: "Xdmcp &amp; Gdm/kdm"
date: 2006-02-08
forum: General Help
---

### Post by edoardo on 2006-02-08
I tried for long (and reserached forums & the web at large) to get XDMCP working on my network of ubuntu 5.10 machines.
My findings:

xdmcp in kdm is BROKEN - no f****in way to get it to work

xdmcp in gdm may work but for me:

-works locally in a nested window started as
Xnest :1 -query localhost
or
Xnest :1 -query machinename

-works from a remote machine running windows and cygwin/X
-does NOT work from a remote machine using Xnest or kde remote login,
in both cases i get the grey X background but no login UI

because cygwin works and native X don't on remote machine that may be my fault. I tried stopping firewalls but in any case they don't show rejected packets. So I'm at a loss ...

any help ?

---

