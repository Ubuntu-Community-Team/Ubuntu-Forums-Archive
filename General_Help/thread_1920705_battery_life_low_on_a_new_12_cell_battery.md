---
title: "battery life low on a new 12 cell battery"
date: 2012-02-05
forum: General Help
---

### Post by dorlow on 2012-02-05
My battery life has been low so I just ordered a new 12 cell battery.  When I used to have a 12 cell battery on this laptop, I could go about 7 hours on a charge.  With this new 12 cell battery, I'm getting about 1.5 hours.  Only thing I can think is it's many years later and I'm using a much newer version of Ubuntu... 11.10.  Any ideas of anyting in Ubuntu that would be sucking the battery about 4xs faster?

---

### Post by xyzzyman on 2012-02-05
Is it a sandy bridge chipset?

---

### Post by dorlow on 2012-02-06
I have no idea.  How do I tell?

---

### Post by JC Cheloven on 2012-02-12
There is a known [kernel issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131"), from 2.6.38 onwards (ie, for Ub11.04 & 11.10), which could be causing the problem.

You can install 3.0.20 linux kernel from [this ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (applies for oneiric 11.10).

---

### Post by xyzzyman on 2012-02-12
> **JC Cheloven said:**
> There is a known [kernel issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131"), from 2.6.38 onwards (ie, for Ub11.04 & 11.10), which could be causing the problem.

You can install 3.0.20 linux kernel from [this ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (applies for oneiric 11.10).

Unfortunately that's a mainline kernel so it's losing all of Ubuntu's "sauce" patches as they call them, big ones being ureadahead to speed up boot times and apparmor, along with alot of driver support for newer hardware. That mainline ppa is only meant for testing while debugging the kernel. He's best off using the following PPA:

```
sudo add-apt-repository ppa:francisbrwn9/kernels 
 
sudo apt-get update 
 
sudo apt-get dist-upgrade
```

That'll install the latest 3.2.0-15 (Or whatever is newer in the future) kernel from Ubuntu sources instead of mainline vanilla.

---

### Post by JC Cheloven on 2012-02-13
Ok, just to let people know: I have just tested the battery life with the 3.0.20 kernel from the ppa mentioned in my post above. The conditions have been:

- Dell mini9 netbook. 2+ years old.
- 10 reboots during the testing process.
- LUbuntu
- Most of the time, wireless off.
- Moderate screen brightness
- Mainly playing minesweeper. Also some doc editing and web browsing.
- Procedure: taking a note of 'uptime' before each shutdown. 

Sum of battery life: 3h05'
Fairly well for this machine. I'd say back to normal. So good news :)

I didn't test the kernel xyzzyman mentioned, I think I'll wait until Precise Pangolin is released. But more than likely newer kernels are equally gentle on battery, so let's hope the bad times of linux regarding this are gone.

Cheers

---

### Post by philinux on 2012-02-13
> **JC Cheloven said:**
> Ok, just to let people know: I have just tested the battery life with the 3.0.20 kernel from the ppa mentioned in my post above. The conditions have been:

- Dell mini9 netbook. 2+ years old.
- 10 reboots during the testing process.
- LUbuntu
- Most of the time, wireless off.
- Moderate screen brightness
- Mainly playing minesweeper. Also some doc editing and web browsing.
- Procedure: taking a note of 'uptime' before each shutdown. 

Sum of battery life: 3h05'
Fairly well for this machine. I'd say back to normal. So good news :)

I didn't test the kernel xyzzyman mentioned, I think I'll wait until Precise Pangolin is released. But more than likely newer kernels are equally gentle on battery, so let's hope the bad times of linux regarding this are gone.

Cheers

You might find this of interest. [http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)

---

### Post by Andrew_P on 2012-02-13
You have to also pay attention to the ampere-hour (Ah) rating of the battery.  There's a lot of fudging in the aftermarket and replacement battery market, but the numbers don't lie.  To get the maximum life from a battery, you should seek ones with the highest Ah rating.  Laptop batteries are usually constructed from cylindrical Li-ion cells welded together with nickel strips.  The individual cells may look very much like the cells used in a flashlight, but their storage capacity when new can vary tremendously, depending on the internal construction and how much "stuff" the manufacturer put into each cell.

---

### Post by JC Cheloven on 2012-02-13
> **philinux said:**
> You might find this of interest. [http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)

Thank you for the suggestion. Unfortunately, I think Jupiter is mono based (at least a lot of mono stuff is installed along jupiter), which I'd rather to avoid.

EDIT: a regular update just came to my pc (for oeniric), with kernel 3.0 among some other stuff. Let's see how it does ;)

---

