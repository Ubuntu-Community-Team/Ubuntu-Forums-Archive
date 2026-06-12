---
title: "how do i change/add kernel modules?"
date: 2012-02-18
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-02-18
lspci -v
```
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 83be
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fbdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

how do i change/add kernel modules?

i am fairly certain for this device to work i have use [FONT=Courier New]snd_hda_codec_nvhdmi[/FONT]
instead of [FONT=Courier New]snd-hda-intel[/FONT]
i loaded the [FONT=Courier New]snd_hda_codec_nvhdmi[/FONT] model but it will not use it how do i force it to?

---

