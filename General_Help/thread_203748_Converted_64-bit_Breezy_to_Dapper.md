---
title: "Converted 64-bit Breezy to Dapper"
date: 2006-06-25
forum: General Help
---

### Post by spirilis on 2006-06-25
Welp, I took the plunge this evening and did the dist upgrade from the Upgrade Manager's "Upgrade" button.  Almost all went well; only thing that went wrong was X.  I'm using an ATI Radeon 9800Pro card and I was greeted with a 100% blank display upon bootup, after all system services started.  Couldn't break out of it to obtain a console login either.

After ~45min wrestling with it, I got xorg-driver-fglrx installed and set it as default and now I'm happily typing away in GNOME on my Dapper system, at 1680x1050 24bpp. :)

I believe dapper was using the "ati" driver when the bug occurred.  Is there a major bug in the 'ati' driver with dapper?  That wasn't a fun experience...

---

