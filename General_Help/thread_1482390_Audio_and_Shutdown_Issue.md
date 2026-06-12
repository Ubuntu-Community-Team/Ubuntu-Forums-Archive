---
title: "Audio and Shutdown Issue"
date: 2010-05-13
forum: General Help
---

### Post by ScarletWyvern on 2010-05-13
Recently after upgrading to Lucid, I occasionally have some weird stuff going on. Namely, when I boot, there's no sound. After I log in, still no sound at all. I don't know much about audio, but I tried alsa reload on a whim. Didn't help at all.

What's also strange is that every time I have this audio bug, trying to shutdown or restart simply takes me back to the GDM login screen and never actually shutdowns. It's odd in that these two errors are inexplicably linked. One never occurs without the other.

The only thing I found could have something to do with it is dmesg proclaiming:

```
[  175.900570] HDA Intel 0000:00:07.0: PCI INT A disabled
[  176.065375] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[  176.065381] hda_intel: Disable MSI for Nvidia chipset
[  176.065428] HDA Intel 0000:00:07.0: setting latency timer to 64
```

Again, this doesn't happen every time I boot. Usually, restarting the computer will fix it. But, that inconsistency only confuses me more.

---

### Post by ScarletWyvern on 2010-05-13
Bump?

---

