---
title: "Compiz on startup Ubuntu Lucid"
date: 2010-10-14
forum: General Help
---

### Post by zangderak on 2010-10-14
Hi,

I installed Compiz Fusion on Lucid Lynx.  It doesn't open on startup though, so I have to right click on the Compiz Fusion Icon then click Reload Window Manager.  But I thought it would be nifty if I didn't have to do this.  So I added this command to Startup Applications:

```
compiz --replace
```And it works.  However, the CPU goes to like %50-60 on startup and doesn't stop.  I removed the startup command and restarted, and the CPU averages %5-10.  Does anyone know the reason for this?

---

