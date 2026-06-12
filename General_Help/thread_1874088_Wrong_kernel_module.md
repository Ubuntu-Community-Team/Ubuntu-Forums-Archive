---
title: "Wrong kernel module?"
date: 2011-11-02
forum: General Help
---

### Post by Cloe on 2011-11-02
Hello! I Bought a NVidia GeForce GT 520 graphics card. I installed the nvidia packages from synaptic. But, i didn't get video in VLC or other media players. Sound, but no video.

 So i tried downloading and installing the driver from NVidias homepage. And now, ubuntu boots but the screen is all black. I checked NVidias readme, and found in my X log file that the NVIDIA kernel module failed to initialize.

 Then i checked the output of dmesg. It says: the client has the version 285.05.09 but this kernel module has the version 280.13.

The driver i downloaded was version 285.05.09. Please help, i dont know what to try next!

---

### Post by dino99 on 2011-11-02
from synaptic:
- remove/purge nvidia* packages, then reinstall nvidia-current (dkms should be installed first)
- add the medibuntu archive: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
- update
- install ubuntu-restricted-extras

now you need to logout and reboot. Then check driver activation (nvidia-current): sudo jockey-gtk

---

### Post by Cloe on 2011-11-02
Thank you for your quick answer! It's a relief to have the GUI back. However, i still don't get video playing. The sudo jockey-gtk said the drivers are activated but not in use?

---

