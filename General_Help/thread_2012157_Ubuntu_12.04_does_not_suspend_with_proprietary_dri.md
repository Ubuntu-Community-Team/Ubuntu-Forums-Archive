---
title: "Ubuntu 12.04 does not suspend with proprietary driver for Radeon 6800"
date: 2012-06-28
forum: General Help
---

### Post by technel on 2012-06-28
I'm running Ubuntu 12.04 x86_64 (though these issues have existed in previous releases too) and have a Radeon 6800 graphics card. I've run into issues with the open-source driver (the system would randomly hang when shutting down) so I switched to the proprietary driver (I compiled it myself using these instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)), but I am having new problems now.

The main issue is that when I go into sleep mode, about 50-75% of the time, the screen goes black but the monitor does not actually shut off, and I can hear that the fans/hard drive are not suspending either. I can't get the computer to wake up (Ctrl+Alt+F1,2,3,etc. does not work), and I always end up force shutting down with the power button.

I'd *really* appreciate help! Here is some information that might be helpful:

```
$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series  
OpenGL version string: 4.2.11631 Compatibility Profile Context

$ dmesg | grep fglrx
[...]
[    6.718606] [fglrx] module loaded - fglrx 8.96.4 [Apr  5 2012] with 1 minors$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series  
OpenGL version string: 4.2.11631 Compatibility Profile Context

$ dmesg | grep fglrx
[...]
[    6.718606] [fglrx] module loaded - fglrx 8.96.4 [Apr  5 2012] with 1 minors
[...]$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series  
OpenGL version string: 4.2.11631 Compatibility Profile Context

$ dmesg | grep fglrx
[...]
[    6.718606] [fglrx] module loaded - fglrx 8.96.4 [Apr  5 2012] with 1 minors
[...]
[...]
```

---

### Post by technel on 2012-06-29
It appears that this works properly with Catalyst 12.6 (released yesterday)!It appears that this works properly with Catalyst 12.6 (released yesterday)!

---

### Post by Quiane on 2012-08-25
did you recompile the 12.6, or did you install from the "extra drivers"? I'm experiencing exactly the same problem for exactly the same reason! Cheers!

---

### Post by technel on 2012-08-25
> **Quiane said:**
> did you recompile the 12.6, or did you install from the "extra drivers"? I'm experiencing exactly the same problem for exactly the same reason! Cheers!

I actually ran into some other problems with 12.6 (related to scaling on my display), but it did, in fact, fix *this* issue. I had to compile it myself (at the time, I don't think it was available from the repos). I also read that was ideal even when the current version of Catalyst is available in the repos.

Good luck!

---

