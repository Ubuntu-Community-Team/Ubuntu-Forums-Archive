---
title: "custom kernal installation"
date: 2012-09-01
forum: General Help
---

### Post by micahpage on 2012-09-01
I have a HDTV hooked up with HDMI, and I would like to use the TV's audio. But the problem is I get a fuzz noise after a couple of minutes after using the HDMI.
I heard that it was a kernal 3.2 problem and that the new kernal 3.5 fixed this issue with HDMI audio fuzz niose. 
1) is it true that that newer kernal will fix this issue?
2) what is the process of compiling the new kernal, pointing grub to the new kernal, etc. 
3) is there another option to fix this issue without compiling a new kernal?
I would like to not screw up my ubuntu install doing this, so im asking to make sure before I try it out.

>  DISTRIBUTION:  Ubuntu 12.04.1 LTS precise
      DESKTOP:  GNOME
       KERNAL:  3.2.0-29-generic
          BIT:  64
          CPU:  Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz [8] Core
    PARTITION:  150 / 210 GB
          RAM:  1374 / 7967 MB


---

### Post by Doug S on 2012-09-02
I don't know if a 3.5 kernel will fix your issue.
You shouldn't have to compile your own kernel.
You can get the kernel already compiled and ready to install from [here.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
I think you would want [this one]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.3-quantal/").

---

### Post by micahpage on 2012-09-02
ok. Thanks for the links

But has anyone ever had this problem and/or fixed it?

---

