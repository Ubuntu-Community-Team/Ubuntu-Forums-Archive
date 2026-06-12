---
title: "ubuntu 11.04 burg resolutions"
date: 2011-09-18
forum: General Help
---

### Post by SENTINEL5000 on 2011-09-18
Hi to all, well I have 2 laptops with intel graphic cards, both have ubuntu 11.04 installed and burg, when I try to change the resolution in burg to 1280X800 which is the best resolution my laptops can go the higher I can go is 1024X768.

Is there anything I can do to make burg recognize that 1280x800 resolution?? Thanks in advance!

---

### Post by drs305 on 2011-09-18
I can speak about Grub, and it *probably* applies to BURG as well. The resolution is dependent on the capabilities of the BIOS and the higher resolution may not be supported until after you boot into your OS.

Again, assuming BURG is the same, you can see what resolutions are available during boot from the BURG command line before you select the OS to boot:
```
vbeinfo
```

---

### Post by SENTINEL5000 on 2011-09-18
Hmm, I did that and no 1280x800 there, so anything I can do, like update BIOS or something?

---

### Post by drs305 on 2011-09-18
> **SENTINEL5000 said:**
> Hmm, I did that and no 1280x800 there, so anything I can do, like update BIOS or something?


I've not seen that addressed in the forums. My BIOS can see 1600x1200, so newer BIOS are certainly *capable* of higher resolutions.

---

### Post by SENTINEL5000 on 2011-09-19
Well, updated the BIOS on my pc, still no resolution change, max it can go is 1024X768 apparently... Thanks anyways!

---

### Post by dcstar on 2011-09-19
> **SENTINEL5000 said:**
> Hmm, I did that and no 1280x800 there, so anything I can do, like update BIOS or something?

No, **any** boot utility can **only** use basic VESA resolutions that the video hardware supports.

---

