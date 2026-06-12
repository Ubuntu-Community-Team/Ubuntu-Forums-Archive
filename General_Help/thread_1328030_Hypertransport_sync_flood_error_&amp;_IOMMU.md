---
title: "Hypertransport sync flood error &amp; IOMMU"
date: 2009-11-16
forum: General Help
---

### Post by Mark F on 2009-11-16
Hi everyone. I'm investigating why I get a "Hypertransport sync flood error" occasionally whilst booting up. Couldnt find anything relevant searching on these forums; wider searches shown below. There are reported problems with the MSI K9N mobo which I use but it was working fine until recently. Unfortunately I upgraded to Karmic and installed 2x2G DDR2 memory sticks at the same time so dont know which (if either) has affected things (did have 1x2G - replaced for matched pair)

Looking at /var/log/syslog.1 I find:
```
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Initializing CPU#0
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Checking aperture...
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] No AGP bridge found
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Node 0: aperture @ 184a000000 size 32 MB
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] This costs you 64 MB of RAM
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
Nov  7 14:30:26 mark-desktop kernel: [    0.000000] Memory: 4052516k/5242880k available (5313k kernel code, 1049176k absent, 141188k reserved, 3011k data, 660k init)
```

(I included lines either side as I dont really know what I'm looking at).

Now I know I could go into the BIOS and change the settings, but if I hose the TV the missus will kill me. I guess I'm looking for some reassurance before messing with things. Thanks in advance for any help.


References:
MSI K9N Problem : [http://forums.pcpitstop.com/index.php?showtopic=174201](http://forums.pcpitstop.com/index.php?showtopic=174201)
Error messages : [http://www.princeton.edu/~unix/Solaris/troubleshoot/error.html](http://www.princeton.edu/~unix/Solaris/troubleshoot/error.html)

---

