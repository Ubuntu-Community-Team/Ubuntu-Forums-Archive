---
title: "Ubuntu server 10.10 doesn't work at all"
date: 2010-10-17
forum: General Help
---

### Post by Glandoux on 2010-10-17
Hello, i'm new to linux and i just installed Ubuntu server 10.10 on a separate hard drive. (i have another one with Win7).
 
The install went fine (from the CDROM) and at the end, it was asking for a reboot.
I did, and i also changed the boot order from my bios to boot with the linux drive.
 
But when i start notting happen, only a **[COLOR=#ff0000]black[/COLOR]** **[COLOR=#ff0000]screen[/COLOR]** with a single flashing white underscore. Nothing, no loading, niet...
 
Anyone can help me?
 
thanks

---

### Post by theozzlives on 2010-10-17
You probably set it up to boot off the "7" drive (dual boot). Does GRUB present you with a menu as to which OS to use if you set it to boot off the "7" drive? Why you would want to dual boot a SERVER OS is beyond me anyhow.

---

### Post by Glandoux on 2010-10-17
Nothing happen, no menu nothing, just a black screen.
 
I don't think the dual boot is a problem, Actually, it's not a real dual boot system.
I have win7 on one hard drive, and linux on another hard drive.

---

### Post by theozzlives on 2010-10-17
> **Glandoux said:**
> Nothing happen, no menu nothing, just a black screen.
 
I don't think the dual boot is a problem, Actually, it's not a real dual boot system.
I have win7 on one hard drive, and linux on another hard drive.

So Windows does not start? My thinking is that GRUB was written to sda as opposed to sdb unless you told it not to install GRUB. If it were me, and Windows worked, I would disconnect the "7" drive and re-install Ubuntu. I do, however, recommend the desktop version.

---

### Post by Glandoux on 2010-10-17
Windows does start if i change the hard drive boot order in the bios

---

### Post by Glandoux on 2010-10-17
I'll give it a try, i'll re-install with the win7 HHD unplugged. I'll keep you posted!
 
thanks

---

### Post by Glandoux on 2010-10-18
Just unplugged the other drive and it worked like a charm.
thanks!

---

