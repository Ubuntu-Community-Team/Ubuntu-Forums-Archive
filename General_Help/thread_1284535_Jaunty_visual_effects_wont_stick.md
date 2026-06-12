---
title: "Jaunty visual effects wont stick"
date: 2009-10-06
forum: General Help
---

### Post by jimcuk on 2009-10-06
Hi all

logging into my Ubuntu 9.04 the visual effects are always set to none.
I can change them using system>preferences>Appearance>visual effects>normal.
however when I next log in they are reset back to None.

Any Ideas please

Graphics card is Nvidia

lspci shows it as
01:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [GeForce 8800 GTX] [10de:0191] (rev a2)
Motherboard is MSI P 965, Neo2


I have the Nvidia driver version 173 Enabled
and have also tried the 180 version

regards
Jim

---

### Post by jimcuk on 2009-10-06
Ok A bit more research and browsing my logs I found this

The following is a common problem: (excerpted from Nvidia's docs)

Q: My X server fails to start, and my Xorg log file contains the error: "(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!"

A: Nothing will work if the NVIDIA kernel module doesn't function properly. If you see anything in the X log file like "(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!" then there is most likely a problem with the NVIDIA kernel module. First, you should verify that if you installed from rpm that the rpm was built specifically for the kernel you are using. You should also check that the module is loaded ('/sbin/lsmod'); if it is not loaded try loading it explicitly with 'insmod' or 'modprobe' (be sure to exit the X server before installing a new kernel module). If you receive errors about unresolved symbols, then the kernel module has most likely been built using header files for a different kernel revision than what you are running. You can explicitly control what kernel header files are used when building the NVIDIA kernel module with the --kernel-include-dir option (see sh NVIDIA-Linux-x86-1.0-4349.run --advanced-options for details).

Please note that the convention for the location of kernel header files changed approximately at the time of the 2.4.0 kernel release, as did the location of kernel modules. If the kernel module fails to load properly, modprobe/insmod may be trying to load an older kernel module (assuming you've upgraded). cd'ing into the directory with the new kernel module and doing 'insmod ./nvidia.o' may help.

Another cause may be that the /dev/nvidia* device files may be missing. To recreate this files simply run this script (as root). It assumes your users who have GUI access are in group "video"): 


Now I know its telling me the problem but dont know where to start
How do I find out my Kernel module ? 

regards
Jim

---

