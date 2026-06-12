---
title: "&quot;radeon&quot; driver not available any more???"
date: 2006-06-25
forum: General Help
---

### Post by flankker on 2006-06-25
hi, i had 3d acceleration working out of the box for my ati mobility 9000 IGP, had xgl/compiz working fine too.

however, today (or yesterday) i had an update for the "mesa" stuff and now 3d acceleration is gone. whats worse i was using the "radeon" driver but now it doesnt appear in the xorg config options.

can anyone help plz? thanx.

---

### Post by johnc4510 on 2006-06-25
I would be more likely to think this happened with the recent kernel update. Whenever there is a kernel update, you have to reinstall the graphics card driver. This is true for radeon or nvidia. It's something we all have to live with.

---

### Post by flankker on 2006-06-25
im pretty sure it was working fine after the kernel update

---

### Post by johnc4510 on 2006-06-25
Okay, I just did some reading up on Mesa, and it is part of the core of the OpenGL drivers for xorg and xserver. So I would imagine the same thing holds true, and you need to reinstall your drivers.

---

### Post by flankker on 2006-06-25
how would i go about doing that? i just used the ones that came with dapper, so i havent actually installed them, so im not sure how to.

---

### Post by johnc4510 on 2006-06-25
Sorry, was eating lunch. Go here to learn how:
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

---

