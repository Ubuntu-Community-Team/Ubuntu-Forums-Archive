---
title: "Ubuntu 12.04 locking up with most kernels"
date: 2012-07-24
forum: General Help
---

### Post by Ncage1974 on 2012-07-24
I have a fairly new ivy bridge system:
Motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138352](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138352)
Graphics: I'm using the embedded HD 4000
Monitors: Dual 22in Dells

Pretty Simple setup. Ubuntu starts just fine. The problems don't start until i enter my password and click the login button. As soon as i do the screen/system locks up and the mouse cursor goes to one corner of the screen.

Whats weird is i have a variety of kernels:
2.6.38-11
3.0.0-15
3.2.0-24
3.2.0-27

Everything works just fine with 2.6.38-11 but what i was talking about above happens on all the other kernels.

I just updated everything today hoping it would fixed (which is when i grabbed 3.2.0-27) but nope everything still locks up. Any Advice?

thanks...

---

### Post by echo6 on 2012-07-24
Can you switch to a console Virtual Terminal?

<ctrl><alt><F1> etc?

If not you may want to consider [kernelnewbies.org/KernelHacking-HOWTO/Debugging_Kernel](kernelnewbies.org/KernelHacking-HOWTO/Debugging_Kernel) and using Magic SysRq key.

---

### Post by Ncage1974 on 2012-07-24
> **echo6 said:**
> Can you switch to a console Virtual Terminal?

<ctrl><alt><F1> etc?

If not you may want to consider [kernelnewbies.org/KernelHacking-HOWTO/Debugging_Kernel](kernelnewbies.org/KernelHacking-HOWTO/Debugging_Kernel) and using Magic SysRq key.

Unfortunately no. The system is totally locked up. Anything else i can try instead of debugging the kernel? To be honest i'm not a seasoned linux person. To be honest i'm just there to do some learning using git, ROR, NoSQL.

---

