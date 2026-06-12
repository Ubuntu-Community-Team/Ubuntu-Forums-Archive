---
title: "No sound"
date: 2006-05-08
forum: General Help
---

### Post by Robbies on 2006-05-08
Hi there. I have no sound on Ubuntu. I have a Crystal Semiconductor CS4236 soundcard. Any help? thanks.

---

### Post by gogomon on 2006-05-08
open up a console and type ' sudo lspci | grep -i audio' and post it back here,

---

### Post by Robbies on 2006-05-09
"unknown directories method"

---

### Post by Robbies on 2006-05-09
Sorry, I had that wrong. Well nothing happened. When I try to open the volume control I get this message: No volume control GStreamer plugins and/or devices found.

---

### Post by naom on 2006-05-11
I have exactly the same problem on my laptop, sometimes when i boot, the sound device is not found, "No volume control GStreamer plugins and/or devices found", to resolve the problem the only way i found is shutting down the system and boot again, a restart doesn't resolve the problem.
My sound card is a intel ... ICH4 (dont remember the full description - its a onboard card running with a i855GM chipset).
Im running Dapper now, but i had the same problem with brezzy!
Any ideas? known issues? ...

---

