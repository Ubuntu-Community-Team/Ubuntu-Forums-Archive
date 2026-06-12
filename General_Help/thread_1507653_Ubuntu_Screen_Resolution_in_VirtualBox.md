---
title: "Ubuntu Screen Resolution in VirtualBox?"
date: 2010-06-11
forum: General Help
---

### Post by Narpas sword0 on 2010-06-11
I know this question has been asked several times, but I swear I searched for well over an hour and a half trying to find an answer to this problem, so any help would be appreciated.

Me and a friend installed Ubuntu 10.4 in a VirtualMachine on our windows PCs, and it all worked perfectly, aside form one problem: The screen resolution is...wait for it...800x600...and the only other option is 640x480. Naturally, this is much too small for us, and it runs (even full-screen) in a tiny window. I know, I've heard this somewhere before too. Anyway, the point is, neither of us have used Linux before, so we have no idea what we're doing, but the few solutions I found to this problem have all failed. My laptop's native resolution is 1368x768, and I suppose I'd use 60Hz refresh rate, so how would I go about doing this?

I tried adding it myself, and this seems to have failed miserably. Anyway, this is what comes up when I type "xrandr":
```
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  1368x768_60.00 (0x154)   85.0MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.6KHz
        v: height  768 start  771 end  781 total  798           clock   59.7Hz
```

Any assistance, again, would be greatly appreciated! I'm loving Ubuntu already, and am looking forward to joining the Linux revolution!

---

### Post by lukeiamyourfather on 2010-06-11
Install the guest additions for the virtual machine. When you resize the window the virtual machine is running it, it'll automatically resize the desktop too. Or if you go to the fullscreen it'll go to your monitor's native resolution. Cheers!

[http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=install+guest+additions+ubuntu](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=install+guest+additions+ubuntu)

---

### Post by dcstar on 2010-06-12
> **Narpas sword0 said:**
> I know this question has been asked several times, but I swear I searched for well over an hour and a half trying to find an answer to this problem, so any help would be appreciated.
.........

Answers to VM question can usually be found in the Virtualization forum.

---

