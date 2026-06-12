---
title: "Turn off shutdown beep?"
date: 2009-10-13
forum: General Help
---

### Post by growthmetal on 2009-10-13
Hi folks,

My computer beeps very loudly when I shut it down.  If I recall correctly, the beep occurs before the Ubuntu progress bar appears.  If text flashes on the screen before the progress bar appears, it probably happens during that text flash.  Turning the volume all the way down makes the beep quieter, but it's still there.  Any fix?  I'm using a Compaq Presario CQ60 dual-booting Vista and Ubuntu.

---

### Post by wojox on 2009-10-13
Blacklist it, open a terminal:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add to the bottom:

```
blacklist pcspkr
```

---

### Post by wpshooter on 2010-02-01
> **wojox said:**
> Blacklist it, open a terminal:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add to the bottom:

```
blacklist pcspkr
```

I have tried the above before and it seems to work in getting the PC system speaker not to beep on shutdown BUT can someone tell me why this beep is taking place ?  To the best of my memory, this beep did not occur before Jaunty.

Thanks.

---

