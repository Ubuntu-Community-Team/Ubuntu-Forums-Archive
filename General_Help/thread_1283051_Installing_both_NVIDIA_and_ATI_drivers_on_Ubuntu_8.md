---
title: "Installing both NVIDIA and ATI drivers on Ubuntu 8.1"
date: 2009-10-05
forum: General Help
---

### Post by aprasad on 2009-10-05
Hello,

I am really new to Ubuntu and recently installed Intrepid Ibex on my Dell Studio 15 laptop. The laptop has an ATI Mobility Radeon HD 4570 graphics card for which I got the [latest drivers]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.39&lang=English") (which I thought were the closest match) from the ATI website. I installed these and things seem to be somewhat working. (It still shows me that the driver is disabled in the driver manager and I doesn't let me enable it. glxinfo causes a segmentation fault.) However, I am able to run at higher resolution and graphics than when the driver was not installed. 

Now I am in the weird situation where I need to install [NVIDIA CUDA drivers and tools]("http://www.nvidia.com/object/cuda_get.html") to get a GPU simulator (GPGPU Sim) to work. Is it possible for  me to install the NVIDIA drivers and still have a properly working machine? Is there something special I need to do or is this just not possible? 

Any help is much appreciated.

Thanks in advance,
Ashwin

---

### Post by CatKiller on 2009-10-05
I don't think it's going to work. I shouldn't imagine that the nVidia and Ati drivers will play nicely together.

You could probably set up a virtual machine though, and run the CUDA stuff in there though.

---

### Post by 3rdalbum on 2009-10-05
CUDA is Nvidia-only. It requires an Nvidia GPU.

---

### Post by aprasad on 2009-10-05
It is possible to run CUDA emulations on machines which do not have NVIDIA GPUs. But as far as I know, this needs the drivers as well. 

Ashwin

---

