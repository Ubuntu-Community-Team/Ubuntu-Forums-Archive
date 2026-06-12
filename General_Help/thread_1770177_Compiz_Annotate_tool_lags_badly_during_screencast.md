---
title: "Compiz Annotate tool lags badly during screencast"
date: 2011-05-28
forum: General Help
---

### Post by meridionaljet on 2011-05-28
Hello,

I use an online screencasting java applet called screencast-o-matic to record my screen. While recording, I use Compiz's annotation tool. Normally this tool works great, but for some reason while I'm recording, it gets very laggy (drawing is way behind the mouse movements) and less smooth. For example, drawing a circle at a quicker pace not only causes lag, but also makes the circle look more like a polygon with straight lines. While this is happening, my CPU also spikes, with large strains showing up on the java process.

I'm running Ubuntu 11.04 with an intel i7 processor. Any ideas as to why annotation lags badly while screencasting, and any ways to fix it, would be appreciated.

---

### Post by wildmanne39 on 2011-05-29
> **meridionaljet said:**
> Hello,

I use an online screencasting java applet called screencast-o-matic to record my screen. While recording, I use Compiz's annotation tool. Normally this tool works great, but for some reason while I'm recording, it gets very laggy (drawing is way behind the mouse movements) and less smooth. For example, drawing a circle at a quicker pace not only causes lag, but also makes the circle look more like a polygon with straight lines. While this is happening, my CPU also spikes, with large strains showing up on the java process.

I'm running Ubuntu 11.04 with an intel i7 processor. Any ideas as to why annotation lags badly while screencasting, and any ways to fix it, would be appreciated.
Hi, go into ccsm and change your refresh rate to 60 and make sure in openGL the the sync to vblank is not checked, if using nvidia go into nvidia x server settings and make sure sync to vblank is not checked there either.

---

### Post by meridionaljet on 2011-05-29
> **wildmanne39 said:**
> Hi, go into ccsm and change your refresh rate to 60 and make sure in openGL the the sync to vblank is not checked, if using nvidia go into nvidia x server settings and make sure sync to vblank is not checked there either.

Disabling Sync to VBlank did the trick. Thanks a lot.

---

### Post by wildmanne39 on 2011-05-29
> **meridionaljet said:**
> Disabling Sync to VBlank did the trick. Thanks a lot.Hi, your welcome, glad it fixed your problem.:)

---

