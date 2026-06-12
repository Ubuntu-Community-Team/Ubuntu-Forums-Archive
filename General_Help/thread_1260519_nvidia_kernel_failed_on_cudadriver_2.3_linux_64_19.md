---
title: "nvidia kernel failed on cudadriver_2.3_linux_64_190.18"
date: 2009-09-07
forum: General Help
---

### Post by bruno9779 on 2009-09-07
Hi!

I have tried installing CUDA on my new Ubuntu 9.04 amd 64 box following these instructions: [Nvidia CUDA]("http://www.nvidia.com/object/cuda_get.html")

after i have shut down X:
```
sudo killall gdm
```
I run the installer
```
sudo ./cudadriver_2.3_linux_64_190.18.run
```
I choose to backup Xconf file, installed 32bit libraries and then I had the message ```
nvidia kernel failed to load
``` and postix something..
following a prompt saying that ubuntu is running in low graphics mode I managed to log back in by choosing "default config"


Now if i try to re-enable my nvidia 180 driver it asks to reboot and goes back the message ```
nvidia kernel failed to load
```

so I need to do one of the following:

- Restore the x-conf backed up file (that i cannot find)
- Get my 180 driver to load properly.

please help

---

### Post by bruno9779 on 2009-09-07
I have managed by reinstalling the 180 driver after deleting conf files.

---

