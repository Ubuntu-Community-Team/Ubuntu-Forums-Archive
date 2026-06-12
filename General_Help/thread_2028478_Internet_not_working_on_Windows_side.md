---
title: "Internet not working on Windows side"
date: 2012-07-18
forum: General Help
---

### Post by Impmaster on 2012-07-18
I installed ubuntu 12.04 on my parents computer a couple months ago, and around that time, they lost internet on the vista side of the same computer. The ubuntu side can access the internet, but they use the vista side, and cannot access it. Is this because of ubuntu, or something else? The router works fine on my computer.

---

### Post by Mark Phelps on 2012-07-18
It IS possible that the loss of network access was not due to the install of Ubuntu, but to the usage of it.

Before I get flamed big time for saying this ... let me explain...

I had an older PC with a RealTek network chip.  When running Windows, something initialized the chip and the networking was OK.

Then, when I booted into Ubuntu, for some reason, the chip did NOT get initialized, and there was no network connection.  Nothing I could do in Ubuntu fixed that.

When I then rebooted into Windows, there was also no networking -- anymore.  I had to run a Realtek networking diag tool -- which, apparently, reset the networking chip and it worked again.

When I rebooted later into Ubuntu, same thing happened again.

To get networking back in Windows, I had to keep rerunning the RealTek network diag tool.

Eventually, there was a firmware update (installed in Windows) that both fixed the network chip problem and drivers problem (in Windows).

After that, networking behaved properly in both Windows and Ubuntu.

---

### Post by mike555 on 2012-07-18
I have found that when I reboot from one operating system my router gets confused ........ but if I shut down for a couple minutes then boot up  on other operating system it works.

---

