---
title: "uninstalling line6 drivers?"
date: 2012-04-08
forum: General Help
---

### Post by lightsaberlesbian on 2012-04-08
I recently looked to this site for instructions on how to install drivers for my Toneport GX device --> [http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html#comments](http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html#comments)

However only after reading the comments did I learn that newer version of ubuntu (i'm assuming including 11.10 which is what i'm running) actually already have the drivers.  I didn't experience the loss of sound as reported but I do notice the drivers aren't working properly -- i'm getting crackly sounds when trying to record.  

Does anyone know how I might uninstall the drivers as installed by these instructions?

---

### Post by raja.genupula on 2012-04-08
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Cheesemill on 2012-04-08
```
cd line6linux/driver/trunk
sudo make uninstall
```

You may have to alter the cd command depending on where you downloaded the source code to.

---

### Post by lightsaberlesbian on 2012-04-08
terminal returned > =make: *** No rule to make target `uninstall'.  Stop.


Will upgrade from 11.10 to 12.04 LTS wipe out these extra drivers?

---

### Post by Cheesemill on 2012-04-08
Are you running the uninstall command in the same source code directory that you installed from, or did you delete the source at any point?

> Will upgrade from 11.10 to 12.04 LTS wipe out these extra drivers?
No.

---

### Post by lightsaberlesbian on 2012-04-08
yea i cd to "cd line6linux/driver/trunk" but even then it returns the same error.

---

