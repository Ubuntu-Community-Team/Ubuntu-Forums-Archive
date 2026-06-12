---
title: "Debugging suspend+resume problems"
date: 2010-02-12
forum: General Help
---

### Post by regularuser on 2010-02-12
Hello,
   
   
   My laptop (Running the vanilla 2.6.31-19-generic kernel on Ubuntu 9.10) is unable to resume from suspend/hibernate, and so I've been following the instructions on the DebuggingKernelSuspend page to see what the problem is.
  
  
   However, after rebooting the machine, the 'Magic number' in the RTC appears to be pretty much random, and isn't in any way reproducible. In addition to this, the clock is correct after the reboot, which seems to indicate that the debugging values aren't being put into the clock at all.
  
  
   It may be significant that the machine is a 64 bit AMD, though the problem happens in both Ubuntu64 and Ubuntu32 installs.
  
  
   I've also tried unloading every module except binfmt_misc, which can't be unloaded. Does this indicate that the problem is in something that has been built into the kernel, rather than a module? Does the pm_trace debug info only get recorded for modules?


   Another thing of note is that when using fglrx and after unloading every driver (except for fglrx and agpart) suspending from the console doesn't seem to work, and gets stuck with a blinking cursor in the top-left. However, this could be my fault due to unloading everything, and not related to the original issue. Using the non-restricted driver has a "better" result in this case.
  
  
   Does anyone know where to go from here? How can this be debugged further?

---

