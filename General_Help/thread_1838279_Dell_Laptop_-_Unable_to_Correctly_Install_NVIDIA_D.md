---
title: "Dell Laptop - Unable to Correctly Install NVIDIA Drivers"
date: 2011-09-03
forum: General Help
---

### Post by zenben1126 on 2011-09-03
Hello,

So I recently got a Dell Inspiron N5110. As far as I can understand, it has 2 graphics chips: an Intel and an NVIDIA. Naturally, it runs on the Intel and Ubuntu doesn't let you switch between the two graphics  cards. My problem: I want to play games as well as general use. 

So I installed a program called Bumblebee, which I'm sure some have heard of. It allows you to switch between the two graphics cards based on optimization. After huge effort in installing it correctly, I typed the command "optirun." It switched to my NVIDIA card no problem. After a little bit of gaming I wanted to switch back and typed "optirun" in the terminal once more. It gave me the following error: 
```

 * Stopping Bumblebee X server bumblebee                                 [fail] 
ERROR: Module nvidia does not exist in /proc/modules
NVOP Disabling nVidia Card failed (Error: AE_NOT_FOUND).
_PS3 Disabling nVidia Card failed (Error: AE_NOT_FOUND).

```

I assumed that I must not have the driver installed for NVIDIA. So I went online and downloaded the NVIDIA 280.13 bash file, killed the X server and ran it as root. It told me that my graphics card is not supported or the GPU is not compatible? Something like that. I said "Install Anyway" to try it out. It gave me some script errors, and then told me that I don't have the proper kernels? 

It's a big mess and I have no idea where to begin! I'm running the latest Ubuntu distribution. Can anyone please help?

---

### Post by zenben1126 on 2011-09-03
The reason I'd like to switch back is simply because NVIDIA KILLS battery consumption.

---

### Post by kentfx on 2011-10-11
I have the same problem, same Dell laptop.  Did you solve it?  This is driving me crazy.

---

