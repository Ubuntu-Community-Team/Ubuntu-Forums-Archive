---
title: "Grub menu not scrolling"
date: 2010-09-03
forum: General Help
---

### Post by Thorndog on 2010-09-03
Grub is not recognizing my keyboard. It works in the BIOS and no problems after boot. Any ideas?
I had been trying to get my iPod Shuffle working without using iTunes... without success and had installed and then uninstalled GTKpod, Hipo, Floola and at the end of (frustrating) messing around with all that, grub wouldn't let me use my last resort, booting to windoze. Maybe something to do with uninstalling GTKpod?
Help!!

---

### Post by bobcollard on 2010-09-03
> **Thorndog said:**
> Grub is not recognizing my keyboard. It works in the BIOS and no problems after boot. Any ideas?
I had been trying to get my iPod Shuffle working without using iTunes... without success and had installed and then uninstalled GTKpod, Hipo, Floola and at the end of (frustrating) messing around with all that, grub wouldn't let me use my last resort, booting to windoze. Maybe something to do with uninstalling GTKpod?
Help!!
Use your live CD to reinstall it.  Sartup with the CD and connect to the Internet, everything should be there to get you back on track.

---

### Post by Thorndog on 2010-09-03
Thanks for the suggestion.
I never made a live cd since I installed Lucid as an upgrade. I already did a new install as root from terminal to no effect.
I will download and make a live cd and try that but I am skeptical. I assume you mean I should only do a GRUB install.

---

### Post by StuartN on 2010-09-03
> **Thorndog said:**
> I already did a new install as root from terminal to no effect.

Possibly you need to modify your BIOS settings to enable legacy keyboard support - USB devices are not recognised until the OS has loaded.

---

### Post by Thorndog on 2010-09-03
> **StuartN said:**
> Possibly you need to modify your BIOS settings to enable legacy keyboard support - USB devices are not recognised until the OS has loaded.

Not likely since it worked for ages before. I always hit the enter key to skip the time delay.

---

### Post by bobcollard on 2010-09-03
> **Thorndog said:**
> Thanks for the suggestion.
I never made a live cd since I installed Lucid as an upgrade. I already did a new install as root from terminal to no effect.
I will download and make a live cd and try that but I am skeptical. I assume you mean I should only do a GRUB install.
Try the Grub install fix first, if that fails backup your home folder and do a full install.

---

### Post by Thorndog on 2010-09-03
> **bobcollard said:**
> Try the Grub install fix first, if that fails backup your home folder and do a full install.

Yuck, ..... P.I.T.A.!

---

### Post by bobcollard on 2010-09-03
> **Thorndog said:**
> Yuck, ..... P.I.T.A.!
Been there, done that, too many times.

---

### Post by StuartN on 2010-09-04
> **Thorndog said:**
> Not likely since it worked for ages before. I always hit the enter key to skip the time delay.

My install does the same (keyboard works in BIOS, but not in Grub), but a PS/2 keyboard does work.

---

### Post by bobcollard on 2010-09-04
> **StuartN said:**
> My install does the same (keyboard works in BIOS, but not in Grub), but a PS/2 keyboard does work.
Strange, my Logitech USB Wireless keyboard and mouse works in boot as well as normally.  Go figure.

---

