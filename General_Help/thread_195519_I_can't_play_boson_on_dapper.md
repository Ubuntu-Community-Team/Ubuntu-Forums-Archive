---
title: "I can't play boson on dapper"
date: 2006-06-13
forum: General Help
---

### Post by joshua27 on 2006-06-13
Well, I had installed boson recently, when I wanted to play it, it said the direct rendering is not enabled, I don't know if there were some errors, when I click on singleuser, and start, the window closed.

My hardware is:
PD 930, Asus P5LD2-VM, 1G RAM, using onboard display

Also, I get "direct rendering = Yes" in glxinfo.

Can anyone tell me what the problem was?

Thank You!

---

### Post by kawker on 2006-09-15
I have the same problem. I just managed to make the direct rendering work and still the same error as you have. I have a Centrino 1,7 GHz and an ATI 1600.
This won't help you but at least you are not allone with this issue...

---

### Post by 4ndY on 2006-09-16
Same issue here...
[I]"Direct rendering is NOT enabled - boson will run very slow.
You should ensure that direct rendering is enabled!"[/I]
Game WILL start but soon it will crush with this debuging info:
> 
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1232755008 (LWP 12405)]
[New Thread -1236067408 (LWP 12421)]
[KCrash handler]
#6  0x00000000 in ?? ()
#7  0xb7fa1a2b in alutLoadVorbis_LOKI () from /usr/lib/libopenal.so.0
#8  0xb7fa1df1 in alutLoadVorbis_LOKI () from /usr/lib/libopenal.so.0
#9  0x00000000 in ?? ()


Glxinfo says that DR is on.
Onboard i810 video card on IBM R50e laptop.

If i find some solution Ill post it here :)

---

### Post by csk on 2006-09-16
could someone please tell me how to get direct rendering to work. i typed glxinfo and i its saying direct rendering as no

---

### Post by bogoliubov on 2006-09-16
> **csk said:**
> could someone please tell me how to get direct rendering to work. i typed glxinfo and i its saying direct rendering as no

You need to be more specific. What's your hardware, what drivers are you using? If you do "glxinfo", what's your output? Also, check other threads if someone has had a problem on similar hardware.

---

