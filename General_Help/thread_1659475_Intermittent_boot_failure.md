---
title: "Intermittent boot failure"
date: 2011-01-04
forum: General Help
---

### Post by gewitty on 2011-01-04
I have 10.10 installed and working OK. The Home directory is located on a second 1TB disk (sdb1). Recently, I've started to experience random boot failures where the start-up routine gets as far as showing the '10.10' logo with the progress dots underneath, but then throws up an error message saying that it cannot mount sdb1. I then have an option to Quit or drop into the shell to do a manual restart.

If I then do a Ctrl/Alt/Del, the system reboots, but usually fails again. Powering off and on, sometimes more than once, is the only way to eventually get a clean boot.

The drive causing the problem is fairly new and all the diagnostic checks seem to indicate that it's healthy, so I'm not sure what causes the problem.

---

### Post by fabricator4 on 2011-01-04
When the boot fails drop to the shell and see if the drive is there and recognised:

```
sudo fdisk -l
```

(If it forces you to drop to the grub command you can't do this - you need the shell to do an fdisk.  Grub is a whole different kettle of fish)

If sdb1 is there you can try mounting it manually and see if it's accessible.  If it's not there, it would seem to indicate a problem with the drive or BIOS.  Reset the BIOS to the defaults, and you could try updating the BIOS firmware if it's not already the latest version.  I've had some weird problems which turned out to be fixed by updating the BIOS, in one case the BIOS was a pre-release version which should never have been allowed out of captivity.

Chris

---

### Post by gewitty on 2011-01-11
The problem appears to have been caused by a USB external hard drive (sdg). I tried switching this off before booting and so far have had no further failures. I'm still none the wiser about why this was interfering with mounting the sdb internal drive though.

---

